## [Meta-learning] Domain Generalizer: A Few-Shot Meta Learning Framework for Domain Generalization in Medical Imaging
- [x] Public accessibility to [paper](https://link.springer.com/content/pdf/10.1007/978-3-030-60548-3_8.pdf)
- [x] Reproducibility [code](https://github.com/Pulkit-Khandelwal/medical-mldg-seg)

### Summary
This work utilizes the very basic episodic training paradigm in the meta learning on the domain generalization of CT vertebrae segmentation. The result is 
compared with domain adaptation methods like few-shot learning. The general algorithm is shown as below:
<p align="center">
  <img src="/assets/221121_algorithm.png" alt="drawing" width="500"/>
</p>
The data is splited by different parts of the vertebrae. Source domain: lumbar, lower thoracic, middle thoracic. Target domain: upper thoracic.
<p align="center">
  <img src="/assets/221121_datasplit.png" alt="drawing" width="300"/>
</p>



