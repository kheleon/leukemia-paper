This repository contains raw data and analysis notebook for manuscript (in progress):

"Single cell mRNA signals reveal the developmental state of KMT2A-rearranged B-lymphoblastic infant leukaemia"

"data" folder contains following:
- single_cell_data (10X single cell leukemia data):
    - raw_counts = output of cellranger, i.e content of filtered_gene_bc_matrices (ALL_AML_1) or filtered_feature_bc_matrix (ALL_AML_2 and ALL_AML_3)
    - SoupX_processed_counts = "decontaminated" raw data, i.e. after running SoupX
    - InfALL1/3/5_clusters.tsv = output file from souporcell software for multiplexed samples.
    - final_h5ad = h5ad object for each sample with raw counts in adata.X slot and  sample ID and cancer/normal cell classification in adata.obs.patient_cancer
    
- bulk_data (bulk data run through Salmon):
    - StJude = matrix of counts with gene length in second column (stJudes_bulk_txiConvGlen.csv) together with metadata
    - TARGET = matrix of counts (TARGET_raw_countsALLwGlen.csv) together with metadata