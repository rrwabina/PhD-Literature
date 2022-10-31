## Contrastive Learning + Federated Learning

## [1] Federated Contrastive Learning for Volumetric Medical Image Segmentation
<code>
@inproceedings{wu2021federated,
  title={Federated contrastive learning for volumetric medical image segmentation},
  author={Wu, Yawen and Zeng, Dewen and Wang, Zhepeng and Shi, Yiyu and Hu, Jingtong},
  booktitle={International Conference on Medical Image Computing and Computer-Assisted Intervention},
  pages={367--377},
  year={2021},
  organization={Springer}
}
</code>

### Problem Statement
- Existing Federated Learning models are highly limited across clients because data sharing are private and illegal. Combining a large dataset consisting of very sensitive and private medical data in a single location is impractival as well.
### Clinical Motivations
- Medical image datasets exist in isolated medical centers and hospitals. Combining a large dataset consisting of very sensitive and private medical data in a single location is impractical and illegal. 
- Federated learning is an effective approach in which distributed clients collaboratively learn a shared model while keeping private raw data local. 

### Technical Motivations
- Existing FL approaches use supervised learning on each client (i.e., computers) and require that all data are labeled. However, annotating all the medical images is usually unrealistic due to high labeling cost and requirement of expertise. **The deficiency of labels makes supervised FL impractical.**
- Self-supervised learning (SSL) can address this challenge by **pre-training a neural network encoder** with unlabeled data, followed by fine-tuning for a downstream task with limited labels. Hence, we integrate CL to FL as **federated contrastive learning**. 
- Simply applying CL to each client and then aggregating the models is not the optimal solution for the following two reasons:
  - Each client only has a small amount of unlabeled data with limited diversity. 
  - If each client only focuses on CL on its local data while not considering other's data, each data will have its own feature space based on its raw data.
- Previous works on FL is that fully labeled data are needed to perform FL, which results in high-labeling cost.
- Previous works on CL
  - Drawback: CL is designed for centralized learning on large-scale datasets with sufficient data diversity. However, when applying CL to FL, the limited data diversity will greatly degrade the performance of the learned model. 
### Contributions
- Proposed an FCL framework for volumetric medical image segmentation with limited annotations
- No data sharing for Federated Learning and leverage the structural similarity of images among clients.
### Methodology
- The FCL consists of two stages (1) feature exchange, (2) global structure matching
- The feature exchange simply exchange the features of its local data with other clients. It provides more diverse data to compare with for better local contrastive learning while avoiding raw data sharing. 
- The global structure matching (GSM) leverages structural similarity of 3D images to align similar features among clients for better FCL.
- Used **<code>MoCo</code>** for local CL since it has a memory bank for negatives, which can leverage local and remote features.
- Two encoders: (1) Main encoder will be used as the initialization for fine-tuning, (2) Momentum encoder as the variation of the main encoder to generate contrast features. The momentum encoder generates local features from local images - used as local negatives. 


## [2] Contrastive Semi-supervised Learning for Domain Adaptive Across Similar Anatomical Structures
### Problem Statement
- Existing Contrastive Learning models are challenged by the cross-anatomy domain shift due to the different appearance and even imaging modalities from the target modalities. 
### Clinical Motivations
- CNNs have achieved remarkable progress in medical image segmenation. However, **it requires a large amount of manual annotations for training images, which is highly time-consuming and labor-intensive to collect**. Therefore, the authors desired to reduce the manual annotations using Semi-Supervised Learning, as it only requires a small set of labeled data with the availability of a large set of unlabeled data. Nonetheless, it is still challenging for most existing SSL methods to achieve high performance with a small training set. 

### Technical Motivations
### Contributions
- Reduce the annotation cost and overcome the problem of limited training images in a target domain, the authors proposed to leverage a dataset for training. They poposed CS-CADA as a generalization of existing semi-supervised and domain adaptation methods.
- The authors adopted Domain-Specific Batch Normalization to deal with domain shift between the two domains while transferiing knowledge of similar anatomical structures.

### Methodology