This repository contains raw data and analysis notebook for manuscript (in progress):

"Single cell mRNA signals reveal a distinct developmental state of KMT2A-rearranged infant B-lymphoblastic leukaemia"

"data" folder contains following:
- single_cell_data (10X single cell leukemia data):
    - raw_counts = output of cellranger, i.e content of filtered_gene_bc_matrices (ALL_AML_1) or filtered_feature_bc_matrix (ALL_AML_2 and ALL_AML_3)
    - SoupX_processed_counts = "decontaminated" raw data, i.e. after running SoupX
    - P1/P3/P5_iALL_clusters.tsv = output file from souporcell software for multiplexed samples.
    - final_h5ad = h5ad object for each sample with raw counts in adata.X slot and  sample ID and cancer/normal cell classification in adata.obs.patient_cancer
*Please note that I use slightly extended IDs, which correspond to the case ID in the paper as folllwing: 
    | case ID  | extended ID |
    | - | ------|
    | 1| P1_iALLM|
    | 2| P2_iALLF|
    | 3| P3_iALL|
    | 4| P4_iALL|
    | 5| P5_iALL|
    | 6| P6_iALL|
    | 7| P7_iALL7_NUTM1 |
    | 8| P8_iALL8_ETV6|
    | 9| P9_iAML_Dx|
    | 10| P10_iAML|
 

- bulk_data (bulk data run through Salmon):
    - StJude = matrix of counts with gene length in second column (stJudes_bulk_txiConvGlen.csv) together with metadata
    - TARGET = matrix of counts (TARGET_raw_countsALLwGlen.csv) together with metadata

"analysis_results" folder contains following:
- deconvolution = results of running of bulk rna-seq deconvolution (cellular signal analysis, github.com/constantAmateur/cellSignalAnalysis), includes StJudes*, TARGET* and InHouse* (lineage switch case, as on Figure 3).

- logreg = results fo logistic regression (single cell cancer to normal comparison, github.com/constantAmateur/scKidneyTumors) and includes `FetalBM_logreg_trained_model.rds` (logistic regression model trained on the fetal bone marrow reference) and `InfALL_allSAMPLES_LogregFBM.csv` (probability of similarity to each of the normal cell type per leukemia single cell)


`Leukemia_data_analysis_final.ipynb` Jupiter notebook shows the preprocessing steps (demultiplexing, normalising) and filtering (mitochondrial content < 20%), as well as code to reproduce Figure 1 (deconvolution results) and  Figure 2 (UMAPs, result of logistic regression and siluette plot)

