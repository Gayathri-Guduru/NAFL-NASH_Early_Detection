# NAFL-NASH_Early_Detection
A gene expression analysis pipeline using the GSE182060 dataset for early detection and treatment of Non-alcoholic fatty liver (NAFL) and Non-alcoholic steatohepatitis (NASH), focusing on differential expression, pathway enrichment, and biomarker discovery.

## Project Overview
This repository contains a comprehensive gene expression analysis pipeline for the GSE182060 dataset, focusing on identifying key genes and pathways involved in the early detection and treatment of Non-alcoholic fatty liver (NAFL) and Non-alcoholic steatohepatitis (NASH). By conducting differential expression analysis, pathway enrichment, and generating visualizations (heatmaps and volcano plots), the project aims to uncover biomarkers and molecular pathways essential for diagnosing and treating these liver diseases at early stages.

## Key Features
- **Differential Expression Analysis**: Identifies genes significantly upregulated or downregulated between Baseline and Follow-up conditions.
- **KEGG Pathway Enrichment**: Highlights key pathways altered in NAFL and NASH progression.
- **Gene Set Enrichment Analysis (GSEA)**: Provides insights into the biological processes and molecular functions enriched in differentially expressed genes.
- **Machine Learning Classification**: Random Forest and XGBoost models are applied for classification of Baseline and Follow-up samples.
- **Visualizations**: Volcano plot and heatmap display the results to facilitate biomarker discovery and interpretation of gene expression patterns.

## Tools and Dependencies
To reproduce the analysis, you will need the following R packages:

To reproduce the analysis, you will need the following R packages:

- **GEOquery**: To retrieve and manage data from the Gene Expression Omnibus (GEO).
- **limma**: For differential expression analysis.
- **clusterProfiler**: To perform KEGG pathway enrichment and GO analysis.
- **org.Hs.eg.db**: For mapping human gene identifiers.
- **KEGGREST**: To fetch KEGG pathway data.
- **msigdbr**: For accessing the Molecular Signatures Database.
- **ggplot2**: For generating visualizations such as volcano plots.
- **pheatmap**: To generate heatmaps of gene expression data.
- **randomForest**: For Random Forest machine learning model.
- **xgboost**: For XGBoost machine learning model.
- **caret**: For model evaluation.
- **pROC**: For ROC curve analysis and performance evaluation.

## Installation
To install the necessary packages, run the following commands in your R environment:
```
# Install BiocManager if not already installed
if (!requireNamespace("BiocManager", quietly = TRUE)) {
    install.packages("BiocManager")
}

# Install required Bioconductor and CRAN packages
BiocManager::install(c("GEOquery", "limma", "clusterProfiler", "org.Hs.eg.db", "KEGGREST", "msigdbr"))
install.packages(c("ggplot2", "pheatmap"))
```

How to Run the Analysis
1. Clone the repository:
```
git clone https://github.com/yourusername/GSE182060-Liver-Disease-NAFL-NASH-Analysis.git
cd GSE182060-Liver-Disease-NAFL-NASH-Analysis
```
2. Install R and the required packages as described above.

3. Run the R script to perform the analysis and generate visualizations.

The provided R Markdown file (dge.rmd) will guide you through the steps of downloading the dataset, processing it, performing differential expression analysis, and conducting pathway enrichment.

## Analysis Pipeline
### Differential Expression and Pathway Enrichment
- **Volcano Plot**: Depicts the Log Fold Change (logFC) and statistical significance (-log10 adjusted p-value) of differentially expressed genes between Baseline and Follow-up.
- **Heatmap**: Visualizes the expression levels of the top 20 differentially expressed genes, highlighting upregulated and downregulated genes in the patient samples.
- **KEGG Pathway Enrichment**: Identifies key metabolic and cytokine signaling pathways altered in NAFL and NASH progression.

## Machine Learning Classification
- **Random Forest Model**
The Random Forest model was trained on the expression data to classify Baseline and Follow-up conditions. Significant genes identified from differential expression analysis were used as features.
- 1.**Model Accuracy**: **82.61%** with balanced accuracy between Baseline and Follow-up.
- 2.**Important Features**: Genes such as **CCL4, EDG4, CXCL9, and CXCL10** were identified as the most important features for classification. 

![image](https://github.com/user-attachments/assets/9b42533d-c37d-4723-a763-f14d591205d2)


- **XGBoost Model**
The XGBoost model was also trained for classification, employing cross-validation to optimize hyperparameters and prevent overfitting.
- 1. **Model Accuracy**: **82.61%** with similar performance to Random Forest.
Feature Importance: The feature importance plot highlights significant genes such as CCL2, CXCL9, and CXCL10.

![image](https://github.com/user-attachments/assets/d97f6696-feeb-4530-884d-501725e60843)


## ROC Curve Analysis
Both models were evaluated using ROC curve analysis to assess the performance of the classification models, with ROC curves indicating high model performance.

## Results Interpretation
1. **Volcano Plot (Detection of Differential Expression)**
- **X-axis (Log Fold Change)**: Indicates the magnitude of gene expression changes between Baseline (healthy) and Follow-up (diseased or treated).
- **Positive logFC values**: Genes upregulated in Follow-up, potentially involved in disease progression or inflammation.
- **Negative logFC values**: Genes downregulated in Follow-up, possibly reflecting suppressed biological functions in NASH or NAFL.
- **Y-axis (-log10 Adjusted P-value)**: Indicates statistical significance.
- Genes with large fold changes and significant p-values are key candidates for understanding disease progression.
- **Interpretation**: Genes with significant differential expression are potential biomarkers for early detection of NAFL/NASH and could also help monitor treatment responses. Immune-related genes may indicate inflammatory processes in liver disease.
- **Random Forest and XGBoost**: Both machine learning models provided robust classification performance, with significant genes identified as important features for predicting disease state.
- **ROC Curves**: Demonstrated that both models achieved high sensitivity and specificity in classifying Baseline and Follow-up conditions.

![volcano_plot_GSE182060](https://github.com/user-attachments/assets/57c1b66a-2a7d-49b1-b25e-b0d8268bd7e6)

2. **Heatmap (Visualization of Differentially Expressed Genes)**
- **Red regions**: Genes upregulated in patients.
- **Blue regions**: Genes downregulated.

![heatmap](https://github.com/user-attachments/assets/9a07f5ca-9429-4e69-ac4c-9cda14c5aae8)

## Key Genes Identified:
- **CXCL10**: Involved in immune response and inflammation, often upregulated in inflammatory conditions like NASH.
- **CCL5**: Linked to inflammation and fibrosis, a key marker of liver disease progression.
- **CXCL9**, **CCL2**, **CCL3**: Additional immune-related genes crucial in the inflammatory process of NAFL/NASH.
- **Interpretation**: The clustering of patients and genes in the heatmap reveals patterns of gene regulation, which can pinpoint early-stage liver changes or therapeutic responses.

3. **KEGG Pathway and GO Biological Process Enrichment Results**
- **KEGG Pathway Enrichment**: Highlights pathways like cytokine-cytokine receptor interaction and metabolic pathways. Disruption in these pathways plays a critical role in NAFL and NASH progression.
- **GO Biological Process Enrichment**: Highlights processes like inflammation, immune cell activation, and lipid metabolism, reflecting abnormal fat accumulation in the liver, a hallmark of NAFLD.
- **Interpretation:** Enrichment analyses help connect differentially expressed genes to relevant biological processes and pathways, identifying potential biomarkers for early detection of inflammation and liver dysfunction.

## Early Detection and Treatment Implications
- **Biomarkers for Early Detection**: Genes involved in inflammation and lipid metabolism, such as CXCL10 and CCL5, could serve as blood-based biomarkers for detecting early liver changes before fibrosis or cirrhosis occurs.
- **Treatment Response**: Monitoring the expression of genes like TRAF6 (involved in the NF-κB signaling pathway) could help track the efficacy of anti-inflammatory treatments for liver disease.
- **Machine Learning Model**s: Random Forest and XGBoost models can be used to develop diagnostic tools for NAFL/NASH classification, providing clinicians with non-invasive alternatives to liver biopsies.

## Conclusion
- Chemokine signaling and cytokine interactions are central to the progression of NAFLD to NASH.
- CCL2, CCL4, and CXCL10 can serve as biomarkers for early detection and also as therapeutic targets.
- Non-invasive blood tests focusing on these chemokines can help in the early detection of liver disease, reducing the need for liver biopsies.
- Targeting inflammatory pathways may prevent disease progression, offering new treatment strategies for patients with NASH.
- The models identified key biomarkers and pathways that can aid in early detection and treatment of liver disease, potentially reducing the need for invasive procedures.

-The analysis provides a robust framework for early detection of liver disorders using gene expression profiling and machine learning. By focusing on the identified biomarkers, particularly those involved in inflammation, the development of blood-based diagnostic tests could allow for the non-invasive and early identification of patients at risk for liver diseases such as NAFL and NASH.

## Repository Contents
**R Scripts**: Scripts for differential expression analysis, pathway enrichment, and visualization (heatmaps, volcano plots).
Result Files:
- **GSE182060_KEGG_Pathway_Results.csv:** Results of KEGG pathway enrichment.
- **GSE182060_GSEA_GO_BP.csv**: Results of Gene Set Enrichment Analysis for GO biological processes.
- **GSE182060_KEGG_GSEA_msigdbr.csv**: KEGG GSEA results using msigdbr.
