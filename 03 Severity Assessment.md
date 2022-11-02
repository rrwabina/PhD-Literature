## Severity Assessment

## [Summary]
### Interesting Methods
- Reference [1]: Ensemble as an uncertainty quantification method

## [1] A Deep Ensemble Learning Approach to Lung CT Segmentation for COVID-19 Severity Assessment

### Problem Statement
- Existing studies present binary segmentation methods for dividing lung scans into healthy and non-healthy tissues while only a few studies yse multi-class segmentation techniques for separating between GGO and CON regions.

### Clinical Motivation
- The lung disease is characterized by GGO and CON pathology. The GGO is manifested by intensity enhancement in the infected lung regions while moderately preserving the bronchial and vascular markings. The CON which is considered graver is a region of compressible lung tissue filled with liquid instead of air. It can be distinguished but determining between GGO and CON is difficult even for experienced radiologists due to the gradual change in the level of opacity and the absence of apparent contrast. 

### Technical Motivation
- The authors presented a novel deep learning for multi-class segmentation of healthy and pathological tissues in lung CT scans. Constructing an ensemble of deep hierarchial models allows us to perform high quality segmentation accuracy. 
- Having $K$ segmentation predictions from the network ensemble allows us to both enhance performance and to provide soft segmentation map. 

### Contributions
- The proposed framework can distinguish between CON and GGO and has high generalization capabilities thanks to unique hierarchial network architectures and ensemble learning.
- Utilizing statistics of the ensemble independent predictions allows us to enhance the overall segmentation accuracy and to derive a measure of segmentation uncertainty.

### Methodology
- The compound hierarchial segmentation architecture consists of L-Net and C-Net, both of which are under U-Net baseline models. 
- The authors used Cross Entropy and Dice Loss Functions. To compensate for the imbalance of data, they used the weighted loss.
- The L-Net: lung cavity is first extracted by L-Net. Then the lung region is partitioned by C-Net into CON and GGO. 

## [2] Rapid Lung Ultrasound COVID-19 Severity Scoring with Resource-Efficient Deep Feature Extraction

### Problem Statement
- The unprecedented number of patients with COVID19 at times of the pandemic caused an oversaturation of the diagnostic capacities in some hospitals. This is likely due to the inherent challenges with ultrasound, whereby experienced ultrasound may be required to obtain images of sufficient quality, and requisite knowledge is then required to propely interpret the acquired images. 
- Existing works on Lung Ultrasound Imaging focuses on complete end-to-end training process only. Moreover, other models only focuses in transfer learning and fine-tuning. 
