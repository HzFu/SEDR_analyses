# SEDR Analyses
Here is the analysis code for SEDR project.  

We tested SEDR on DLPFC dataset (12 slices) and compared it with 5 state-of-the 
art methods: 
* [BayesSpace](https://github.com/edward130603/BayesSpace)
* [Giotto](https://github.com/RubD/Giotto)
* [stLearn](https://github.com/BiomedicalMachineLearning/stLearn)
* [SpaGCN](https://github.com/jianhuupenn/SpaGCN)
* [Seurat](https://satijalab.org/seurat/)


To run analyses code properly, we recommend you to organize working folder as shown 
below and download the scripts into the folder. 



## Benchmarking

### data folder structure


    SEDR
    ├── data
    │   └── DLPFC
    │        └── 151507
    │              ├── filtered_feature_bc_matrix.h5
    │              ├── metadata.tsv 
    │              └── spatial
    │                     ├── scalefactors_json.json  
    │                     ├── tissue_positions_list.csv  
    │                     ├── full_image.tif  
    │                     ├── tissue_hires_image.png  
    │                     └── tissue_lowres_image.png  
    ├── output      
    │      └── DLPFC          
    │            └── 151507 
    └── SEDR_analyses
        ├── DLPFC_Seurat.R  
        └── ...  


### Download data
DLPFC data can be downloaded from [SpatialLIBD](https://github.com/LieberInstitute/HumanPilot/). 
Extract and put data within data/DLPFC folder.  
Please notice that the scale_factors_json.json and tissue_positions_list.csv can be found in 10X folder in [SpatialLIBD](https://github.com/LieberInstitute/HumanPilot/).  
Besides, the metadata.tsv we used in SEDR is consistant with [BayesSpace](https://github.com/edward130603/BayesSpace).  
For convenient, we have put three files within data folder here. You need to move the data folder to where we recommend. 



### Run SEDR
* Follow the instructions in [SEDR](https://github.com/Xuhang01/SEDR) to run SEDR for 12 slices. 
* Move the results to output/DLPFC/sample.name/SEDR for further comparison.

### Run state-of-the-art methods
* Rscript DLPFC_Seurat.R sample n_clusters
* python DLPFC_stLearn.py sample
* python DLPFC_SpaGCN.py sample n_clusters
* Rscript DLPFC_BayesSpace.R sample n_clusters
* Rscript DLPFC_Giotto.R sample n_clusters


Table of n_clsuters:
  
|Sample_ID|n_clusters|
| ------------- |:-------------:|
|151507|7|
|151508|7|
|151509|7|
|151510|7|
|151669|5|
|151670|5|
|151671|5|
|151672|5|
|151673|7|
|151674|7|
|151675|7|
|151676|7|


### Compare SEDR and other methods
* Rscript DLPFC_comp.R sample

### Summary of 12 slices
* Rscript DLPFC.ARI_boxplot.R


## Stero-seq data
Stero-seq data in SEDR project is included in data folder. 