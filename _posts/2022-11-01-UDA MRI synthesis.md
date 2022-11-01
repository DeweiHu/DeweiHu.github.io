## [UDA synthesis] Generative Self-training for Cross-Domain Unsupervised Tagged-to-Cine MRI Synthesis

- [x] Public accessibility to [paper](http://arxiv-export-lb.library.cornell.edu/pdf/2106.12499)

### Summary
The author propose a unsupervised domain adaptation (UDA) method to transfer the tagged MRI to cine MRI for cross-scanner and cross-center data. <br />
>**Key idea:** The so-called "self-training" is realized by setting contraint on the uncertainty of the prediction on the target domain. Two types of uncertainties are taken into consideration:
> - Epistemic uncertainty: A systemetic uncertainty ralated to the model. It is usually modelled via Bayesian neural networks (do K times prediction with Monte Carlo dropout), and the uncertainty id measured by the MSE
> <p align="center">
>   <img src="/assets/221101_epistemic.png" alt="drawing" width="400"/>
> </p>
> 
> - Aleatoric uncertainty: The uncertainty induced by the stochastic variability inherent in the data. In this work, it is represented by the head split prediction, and we regard it as the variance of the prediction (Similar to the latent space of VAE realization). The the corresponding expression is
> <p align="center">
>   <img src="/assets/221101_aleatoric.png" alt="drawing" width="200"/>
> </p>

The overall pipeline is shown as following:
<p align="center">
  <img src="/assets/221101_pipeline.png" alt="drawing" width="600"/>
</p>
The model is initialized by training on the source domain with paired supervision. <br />

**Step (a)** is to use the current model, apply MC dropout K times to estimate the uncertainty (the sum of the two types mentioned above) and a pseudo-label which is the mean of the K predictions. 

**Step (b)** is to retrain the network with the loss function given below:
<p align="center">
  <img src="/assets/221101_loss.png" alt="drawing" width="400"/>
</p>
