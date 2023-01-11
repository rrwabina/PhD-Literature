## Molecular Biomarkers

## [Summary]
### Interesting Methods and Insights
[1] [Identifcation and prognostic analysis of biomarkers to predict the progression of pancreatic cancer patients](https://molmed.biomedcentral.com/articles/10.1186/s10020-022-00467-8)

- The surgical resection is the only treatment for pancreatic cancer. Only a minority of patients can obtain surgery and improving the overall survival rate is still a major challenge. 
- Molecular biomarkers are a significant approach for diagnostic and predictive use in pancreatic cancers.
- Precise biomarkers are urgently required to increase the efficiency of predicting a disease-free survival, overall survival, and sensitivity to immunotherapy in PC patients and improve the prognosis of PC. 

- Results: 
    - LAMB3, FN1, KRT17, KRT19, and ANXA1 were defined as the top five upregulated targets in PC compared with paracancer.
    - Significantly, LAMB3, FN1, KRT19, and ANXA1 but not KRT17 can be considered as biomarkers for survival analysis, univariate and multivariate Cox proportional hazards model, and risk model analysis.
    - In conclusion, LAMB3, FN1, KRT19, and ANXA1 are good predictors of PC prognosis. Furthermore, FN1 and ANXA1 can be predictors of immunotherapy in PCs.

[2] [Deep Learning-Based Prediction of Molecular Tumor Biomarkers from H&E: A Practical Review](https://www.mdpi.com/2075-4426/12/12/2022/pdf)

- Molecular and genomic properties are critical in selecting cancer treatments to target individual tumors, particularly for immunotherapy. 
- Breast cancer is a clear example of the effectiveness of precision medicine. Tumors that overexpress the HER2 protein can receive targeted therapy, radically improving the prognosis
- Molecular biomarkers can be predicted from H&E using the advancements of deep learning: molecular alterations, genomic subtypes, protein biomarkers, and even the presence of viruses.
- Understanding the subset of patients who may benefit is the key to personalized cancer treatments. Patients can be stratified by a variety of molecular and genomic properties, where each subtype responds to some courses of treatment but not others and tends to have a distinct prognosis.
- Four types of molecular biomarkers have been successfully predicted from H&E in studies of more than ten different types of cancer: 
    - (1) protein biomarkers
    - (2) genomic subtypes and expression of individual genes 
    - (3) molecular alterations
    - (4) virus. 

## Deep Learning Methods for Whole Slide Images
- Traditional methods in computational pathology mostly focus on replicating tissue morphology features to mimic pathologists.

#### 1. Bottom-Up Approaches to Learning Features
- Histopathology --> Image Tile Segmentation
    - These apporahces require detailed annotations at the pixel level.
    - Most algorithms to predict molecular biomarkers rely on **weak supervision**