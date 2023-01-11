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
- Learning Tile Features
    - Reliance on transfer learning with CNN pretrained on **ImageNet**
    - Recent advances in self-supervised learning present another alternative: pretrain a model on tiles from WSIs with a pretext task
        - **Fingerprinting** that learns features to distinguish one patient from another. Sourced from [Deep learned tissue "fingerprints" classify breast cancers by ER/PR/Her2 status from H&E images](https://www.nature.com/articles/s41598-020-64156-4)
        - They demonstrated that this representation works better than a fully supervised approach for predicting breast cancer receptor status.
        - **Contrastive Learning**: Liu et al. proposed a meta contrastive learning framework that iteratively trains a model with cross-entropy and contrastive objectives [31]. The contrastive objective increases intra-class similarity and decreases inter-class similarity.
    - Transformers have also emerged as an alternative to the CNN. 
        - Guo et al. trained a Swin-T transformer for predicting MSI and a few other colorectal cancer biomarkers. Their model produced results superior to previously published studies and was significantly more robust than other methods when trained on 50% or 25% of the training set.
- Tile Aggregation
    - The first step in processing WSIs is selecting which tiles to use for model training. Tiles containing little tissue can easily be discarded by tissue detection methods, and most studies also exclude non-tumor tissue.
    - The most common method is a simple aggregation of tile predictions using the mean prediction or taking a majority vote. This approach will work well in some cases, but may fail if the tumor is heterogeneous or not all tiles are informative of the biomarker status—for example, if non-tumor tiles are included.
    - La Barbera et al. calculated statistics on the tile predictions to form a single patient-level feature vector on which the second stage classifier was trained to predict HER2 status of breast cancer.

    - Recurrent neural networks (RNNs) have been used to make a prediction after encoding a sequence of tiles.
        -  A multiple instance learning (MIL) model is chosen to accommodate the latent tile labels.
    - **An attention model can be applied as a CNN aggregation layer for end-to-end prediction.** In order to fit the entire model on a GPU for training, a subset of tiles must be selected from each WSI.


# Challenges
- Model validation is difficult when large and diverse datasets are not always possible opening up opportunities for bias, batch effects, and poor model generalizability. 

## 1. Tile Selection
- Some studies have relied upon manual annotations of tumor regions from pathologists. This could take the form of tissue microarray cores that are selected by pathologists or annotated WSIs
#### Only tumor tiles are inputted to the model.
- Xu et al. selected representative tiles by clustering all tiles and choosing tiles from each cluster [Using transfer learning on whole slide images to predict tumor mutational burden in bladder cancer patients](https://www.biorxiv.org/content/10.1101/554527v1)

#### While most studies include only tumor tissue, only few studies have experimented the inclusion of non-tumor tiles. 
- **Inclusion of non-tumor tiles**:  Rawat et al. compared models that used all tissue tiles, epithelium only, stroma only, fat only, or epithelium and stroma for predicting breast cancer receptor status [30]
- **Inclusion of non-tumor tiles**: Muti et al. also experimented on which regions of tissue were included in models: the whole slide, tumor only, or a virtual biopsy of a 2 mm wide region of tissue
- **Inclusion of non-tumor tiles**: Campanella et al. used a semantic segmentation model to locate thirteen different subtypes of tissue. [49]
- **The attention component makes it possible to train with both tumor and non-tumor tiles, allowing the model to identify the discriminative tiles.**
- **Inclusion of non-tumor tiles**: Schrammen et al. also included slides containing no tumor in their training set. [69]
    - Tissue tiles from non-tumor slides were labeled as non-tumor and tiles in tumor slides were labeled according to their slide label, making this a multiclass model. Their method performed slightly better than a two-class model that uses all tiles (tumor and non-tumor).

## 2. Magnification for Bottom-Up Approaches
#### Since cellular details are not visible at lower magnifications, what magnification level should be used?