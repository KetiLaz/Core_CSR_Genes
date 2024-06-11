# Core Stress Response Genes 
This repository contains the scripts written to find and analyse the core cellular stress response genes as extracted by Darling (a disease-oriented online text mining tool). The scripts are written in Python using Google Colab. <br/>
Darling was used to extracted genes associated with five types of cellular stress response (CSR): 
- Oxidative Stress Response
- Heat Shock Response
- DNA Damage Response
- Protein Damage Response
- Cellular Hypoxia <br/>

We found the genes (called them core stress response genes) that were present in all five of these CSR types and validated their biological significance. This repository contains the scripts used to achieve that. 

## Core_CSR_Genes.ipynb
This Google Colab includes the script that was written to import the CSV files that contained the genes extracted from Darling and find the core stress response genes (i.e the genes that are common among all the five types of CSR). We also found the genes that are unique for each type of cellular stress response.

## CoreGenes_In_EdgeR_Files.ipynb
In this Google Colab we found how many and which of the core CSR genes were present in edgeR files in order to validate the biological significance of the core genes. The edgeR files contain data (among them fold change of genes and the corresponding p-values) of RNA-seq data collection of 87 stress-related studies. <br/>
Also the mean number of the core CSR genes present in the studies was calculated (approximately 51 genes). This number will be used for the control genes in the bootstrap analysis. 

## Bootstrap_Analysis.ipynb
In this Google Colab the script will randomly choose 51 control genes from a CSV file - from this choice all the genes extracted from Darling are excluded. Then it will find how many of the control genes are present in each study, the count of genes with statistically significant p-values and the percentage of genes with pvalues < 0.05. <br/> 
Then, it will make a paired t-test analysis of the overall p-value percentages for control and core genes to see if there is a statistically signficant difference between them. All of the above will iterate 100 times. <br/>
Finally, it calculates the statisctics (median,mean and standard deviation) of the bootstrap analysis 
