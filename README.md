# NCI-DOE Collaboration Pilot 1: Semi-supervised Feature Learning with Center Loss

### Description
The RNA-Seq Latent Featurizer Using Center Loss Cost Function (CLRNA) software provides a semi-supervised, autoencoder-based, machine learning procedure. This procedure learns a smaller set of gene expression features that are resistant to batch effects using background information on a cell line or tissue’s tumor type. The authors of this model implemented this reduced feature representation and show that the new feature space clusters strongly according to tumor type. The authors carried out experiments across multiple studies: Cancer Cell Line Encyclopedia ([CCLE](https://sites.broadinstitute.org/ccle/)), Cancer Therapeutics Response Portal ([CTRP](https://portals.broadinstitute.org/ctrp.v2.1/)), the Genentech Cell Line Screening Initiative ([gCSI](https://pharmacodb.pmgenomics.ca/datasets/4)), Genomics of Drug Sensitivity in Cancer ([GDSC](https://www.cancerrxgene.org/)), [NCI-60](https://discover.nci.nih.gov/cellminer/home.do), and patient derived tumors. The system downloads the data in this example from the [Cancer Drug Response Prediction Dataset](https://modac.cancer.gov/searchTab?dme_data_id=NCI-DME-MS01-8088592) in the Model and Data Clearinghouse (MoDaC). This method produces features that are resistant to batch effects.

### User Community
Researchers interested in the following topics:
* Primary: Cancer biology data modeling
* Secondary: Machine learning; bioinformatics; computational biology

### Usability
The current code can be used by a data scientist experienced in Python and the domain.

### Uniqueness
The new cost function is a weighted combination of three terms: reconstruction performance, classification performance, and ‘center loss’ performance. Reconstruction performance ensures that the ‘pinch’ layer retains information about original gene expression while classification performance shapes the space so tumors of the same type are close together regardless of the source study. Originally, representing each tumor required 17,000 gene activation features. However, with the 'pinch' layer, representing each tumor requires only 1,000 features or, with some loss in predictive performance, as few as 20 features. The authors compare the new features from the ‘center loss’ autoencoder and ComBat using Silhouette score, the Calinski-Harabaszindex, and the Davies-Bouldin index. All metrics show that the ‘center loss’ autoencoder features provide a latent space with better clusters than applying ComBat.

### Components
This capability provides the following components:
* Scripts in this repository: 
    * Scripts to download and process RNA-Seq expression and cell line data. 
    * Script to train the autoencoder model.
    * Scripts to encode the RNA-Seq expression and visualize the reduced dimension results. 
* The trained model in the [CLRNA](https://modac.cancer.gov/searchTab?dme_data_id=NCI-DME-MS01-9815585) asset in MoDaC.
* Data from the [Cancer Drug Response Prediction Dataset](https://modac.cancer.gov/searchTab?dme_data_id=NCI-DME-MS01-8088592) in MoDaC. 

### Technical Details
Refer to this [README](./src/README.md).
