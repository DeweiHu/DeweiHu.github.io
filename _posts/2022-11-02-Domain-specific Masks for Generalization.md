## [Representation Disentangle] Learning to Balance Specificity and Invariance for In and Out of Domain Generalization
- [x] Public accessibility to [paper](https://arxiv.org/pdf/2008.12839.pdf)
- [x] Reproducibility [code](https://github.com/prithv1/DMG) 

> **Key idea:** The key idea of the paper is: leveraging the a balance between "invariance" (feature that are shared across domains) and 
> "specificity" (features are specific to invididual domains) will aid the model in terms of generalization. The proposed the method mainly
> stress on the expression of such "specificity".  

<p align="center">
  <img src="/assets/221102_idea.png" alt="drawing" width="500"/>
</p>

The idea is illustrated as above, suppose the feature extracted can be classified into to 3 catagories: domain-invariant, domain-specific and partially domain-invariant.
Note that the so-called domain-invariant/domain-specific feature here is defined by the multiple source domains. Hence, this classification of features is not in a global
sence. Then in the test time, the instance from an unseen distribution can share some similarities with a specific source domain in "domain-specific" components. As an 
example, the quickdraw image has a similar style with the sketch dataset. 

The author introduce the **D**omain-specific **M**asks for **G**eneralization (DMG) to model the specificity. For each individual domain, they learn a mask (normalized by
a sigmoid function, then sampled from the Bernoulli distribution so that it is binarized). Then apply this mask to the activation functions. Similar to the dropout, this
will resulted in a "thinner" network which is regarded to be domain specific.

<p align="center">
  <img src="/assets/221102_DMG.png" alt="drawing" width="600"/>
</p>

To futher ensure the specificity, they implement a loss function to minize the overlap of masks for different domain.

<p align="center">
  <img src="/assets/221102_sIoU.png" alt="drawing" width="350"/>
</p>

Combined with the loss function for the specific task (classification), the overall loss function is defined as

<p align="center">
  <img src="/assets/221102_loss.png" alt="drawing" width="350"/>
</p>
