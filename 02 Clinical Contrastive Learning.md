## Contrastive Learning + Federated Learning

## [1] Federated Contrastive Learning for Volumetric Medical Image Segmentation
<code>
 
</code>

### Problem Statement

### Clinical Motivations
### Technical Motivations
- Existing FL approaches use supervised learning on each client (i.e., computers) and require that all data are labeled. However, annotating all the medical images is usually unrealistic due to high labeling cost and requirement of expertise. **The deficiency of labels makes supervised FL impractical.**
- Self-supervised learning (SSL) can address this challenge by **pre-training a neural network encoder** with unlabeled data, followed by fine-tuning for a downstream task with limited labels. Hence, we integrate CL to FL as **federated contrastive learning**. 
### Contributions
- Proposed an FCL framework for volumetric medical image segmentation with limited annotations
### Methodology
