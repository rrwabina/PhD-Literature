## Brain Cancer Survival Prediction Studies 

## [1] Brain Cancer Survival Prediction on Treatment-Naive MRI using Deep Anchor Attention Learning with Vision Transformer
<code>
 @inproceedings{xu2022brain,
  title={Brain Cancer Survival Prediction on Treatment-Na{\"\i}ve MRI using Deep Anchor Attention Learning with Vision Transformer},
  author={Xu, Xuan and Prasanna, Prateek},
  booktitle={2022 IEEE 19th International Symposium on Biomedical Imaging (ISBI)},
  pages={1--5},
  year={2022},
  organization={IEEE}
}   
</code>

### Problem Statement
- The radiologic phenotype from MRI are difficult to reproduce because of variability in acquisition and preprocessing pipelines. Despite the evidence of intra-tumor phenotypic heterogeneity, the spatial diversity between different slices within an MRI scan has been relatively unexplored using such methods. 

### Clinical Motivations
- Glioblastoma has a **poor prognosis** with the median survival around 12-15 months.
- The spatial diversity and the interaction between different sub-regions of a tumor are not fully explored from a **phenotype perspective**.
- Survival analysis is limited to understanding of intra-tumoral and peri-tumoral heterogeneity as slice-wise statistics **without taking into account intra-tumor heterogeneity reflected as inter-slice and intra-slice spatial diversity on MRI**.
    - The authors proposed a three-way view of slicing mechanism to improve transfer learning.

### Technical Motivations
- Pre-trained representations may not effectively capture subtle local variations prevalent in MRI scans, more so in brain tumors.
- Class label is generally assigned at an MRI-level and not at a slice-level.
- Previous works focus on local variations in image patterns. Hence, the authors extract imaging representations through axial, coronal, and sagittal patterns. **Existing methods only use axial slices.**

### Contributions
1. The authors proposed a Deep Anchor Attention Aggregation Strategy (main model) with a Vision Transformer (transfer learning) to predict survival risk for brain cancer patients. 
2. Intra-slice spatial diversity in MRI is captured by a self-attention mechanism.

### Methodology
- Goal: **Predict the survival risk $\mathbf{r}_i$** for each patient $i$.
- Two datasets: (1) $D_1$ is for transfer learning and fine-tuning; (2) Survival risk prediction using $D_2$

#### 1. Fine-tuning vision transformer on an MRI dataset.
- Images in $D$ are fed into ImageNet pretrained for Vision Transformer for classification.
- Adam optimizer, 500 epochs 
- Validation accuracy: 0.94 (classifying glioma, meningioma, and pituitary tumor)
- **Fine-tuned ViT to become a feature extractor for survival prediction.**

#### 2. Deep Anchor Attention Learning
- Anchor Query: Matching between slices and anchor slices

#### Baseline models
- Radiomics, ResNet18, CoxModel, DeepSurv, DeepAttnMISL model
