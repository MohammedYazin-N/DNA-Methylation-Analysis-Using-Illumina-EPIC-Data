# DNA Methylation Analysis of Cerebral Small Vessel Disease Using Illumina EPIC Data

## About the Project

DNA methylation is an epigenetic mechanism that can influence gene regulation without changing the underlying DNA sequence. Changes in DNA methylation have been studied in several diseases, including neurological and vascular disorders.

Cerebral small vessel disease (SVD) is associated with stroke and cognitive decline. This project investigates genome-wide DNA methylation differences between people with SVD and healthy controls using Illumina Infinium MethylationEPIC array data.

The analysis uses raw IDAT files from the GEO dataset GSE318387. Data preprocessing and quality control were performed in R using the minfi package. Differential methylation analysis was carried out using the limma framework, with Benjamini–Hochberg correction to control the false discovery rate. PCA, heatmaps, volcano plots, and beta-value distribution plots were generated to explore methylation patterns across samples.

This project was completed as part of the NGS and Omics Data Analysis course.

## Aim

To identify genome-wide DNA methylation differences between cerebral small vessel disease samples and healthy controls using Illumina Infinium MethylationEPIC array data.

## Objectives

- Obtain and process DNA methylation array data from the Gene Expression Omnibus (GEO).
- Import raw IDAT files and perform quality control.
- Normalize methylation data and calculate beta values.
- Compare methylation levels between SVD and control samples.
- Identify differentially methylated positions (DMPs) using statistical analysis.
- Apply Benjamini–Hochberg false discovery rate correction.
- Identify CpG sites showing increased or decreased methylation in the SVD group.
- Visualize methylation patterns using boxplots, PCA, heatmaps, and volcano plots.
- Generate result tables for significant CpG sites and separate hypermethylated and hypomethylated sites.

## Dataset

The study used GEO dataset GSE318387.

- Dataset: GSE318387
- Platform: Illumina Infinium MethylationEPIC array (850K)
- Number of samples: 32
- SVD samples: 16
- Control samples: 16
- Sample source: Peripheral blood

Dataset source: https://www.ncbi.nlm.nih.gov/geo/

The report describes approximately 930,000 CpG sites analyzed. The original array data were supplied as IDAT files, which contain raw methylation array signal measurements.

## Tools and Packages Used

- R Statistical Software
- minfi
- limma
- pheatmap
- GEO database
- Illumina Infinium MethylationEPIC array data

## Methodology

### 1. Data Acquisition and Import

Raw IDAT files for GSE318387 were obtained from GEO. The minfi package in R was used to import the raw methylation array data and prepare it for downstream analysis.

Sample metadata were used to assign samples to the SVD and control groups.

### 2. Quality Control and Preprocessing

Quality control was performed to assess data integrity before statistical analysis. The data were normalized using quantile normalization with the preprocessQuantile workflow in minfi, as described in the report.

Beta values were calculated to represent methylation levels at CpG sites. Beta values range from 0 to 1, with higher values indicating greater measured methylation.

### 3. Differential Methylation Analysis

Differential methylation analysis was performed to identify CpG sites with different methylation levels between SVD and control samples.

The limma framework was used to fit linear models. P-values were adjusted using the Benjamini–Hochberg method to control the false discovery rate. CpG sites with an adjusted p-value below 0.05 were selected as significantly differentially methylated positions.

### 4. Hypermethylation and Hypomethylation

Significant CpG sites were examined according to the direction of the reported log fold change.

- Hypermethylated CpGs (logFC > 0): higher methylation in the SVD group under the report's contrast definition.
- Hypomethylated CpGs (logFC < 0): lower methylation in the SVD group under the report's contrast definition.

The biological consequences of methylation depend on genomic location and context. Therefore, hypermethylation should not automatically be interpreted as gene silencing, nor hypomethylation as gene activation, without further annotation and evidence.

### 5. Data Visualization

Several visualizations were generated to inspect the data and communicate the findings.

**Beta-value distribution boxplot:** Used to compare methylation-value distributions across samples and inspect normalization patterns.

**Principal Component Analysis (PCA):** Used to explore sample-level patterns and assess whether SVD and control samples showed separation in the main components.

**Heatmap:** Used to visualize methylation patterns for selected CpG sites and explore clustering among samples.

**Volcano plot:** Used to display effect sizes and statistical significance, highlighting CpG sites that passed the selected significance threshold.

## Results

The report identified 7,295 significantly differentially methylated CpG sites using an adjusted p-value threshold below 0.05.

The main findings reported were:

- Significant methylation differences were identified between the SVD and control groups.
- Both hypermethylated and hypomethylated CpG sites were observed.
- The beta-value distribution plot was reported to show broadly uniform distributions across samples after normalization.
- The PCA plot showed partial separation between SVD and control samples, with some overlap.
- The heatmap showed clustering patterns among samples based on the selected CpG sites.
- The volcano plot highlighted CpG sites with statistically significant changes.

These results suggest differences in peripheral-blood methylation profiles between the groups in this dataset. They do not by themselves establish causal mechanisms or validated clinical biomarkers.

## Files Generated

The analysis report lists the following output files and visualizations:

- DMP_full_results.csv
- DMP_significant.csv
- Hyper_methylated.csv
- Hypo_methylated.csv
- Top_100_CpGs.csv
- Heatmap
- PCA plot
- Volcano plot
- Beta-value distribution boxplot

Include the actual output files and exported figures in the repository when available. Do not add placeholder files for results that have not been generated.

## Limitations

- The analysis included 32 samples, so the small sample size may limit statistical power and generalizability.
- The samples came from peripheral blood and may not fully reflect methylation patterns in brain tissue.
- The reported analysis focused on differentially methylated positions; differential methylation region analysis was not performed.
- Gene annotation and pathway enrichment analysis were not included in the reported workflow.
- Independent validation is needed before considering the findings as potential biomarkers.
- Potential confounding factors and technical effects should be evaluated as part of further analysis.

## Future Work

Possible extensions of this project include:

- Performing differentially methylated region (DMR) analysis.
- Annotating significant CpG sites to genes and genomic regions.
- Conducting gene and pathway enrichment analysis.
- Validating the findings using independent datasets.
- Integrating methylation data with gene expression data for a multi-omics analysis.
- Investigating the effects of relevant covariates and potential batch effects.

## Conclusion

This project applied an R-based DNA methylation analysis workflow to Illumina Infinium MethylationEPIC array data from cerebral small vessel disease and control samples. Using minfi for data processing and limma for differential analysis, the study reported 7,295 significantly differentially methylated CpG sites after false discovery rate correction.

PCA, heatmaps, volcano plots, and beta-value distribution plots were used to explore methylation patterns and differences between the two groups. The findings provide an initial computational analysis of peripheral-blood DNA methylation in SVD and a basis for further investigation through gene annotation, pathway analysis, regional analysis, and independent validation.

## References

- GEO dataset GSE318387: https://www.ncbi.nlm.nih.gov/geo/
- Aryee et al., *Minfi: a flexible and comprehensive Bioconductor package for the analysis of Infinium DNA methylation microarrays.*
- Ritchie et al., *limma powers differential expression analyses for RNA-sequencing and microarray studies.*
- R Statistical Software: https://www.r-project.org/

## Disclaimer

This project is intended for academic and research purposes only. The findings are based on computational analysis of a specific dataset and should not be interpreted as a clinical diagnostic test or as proof that the identified methylation changes cause cerebral small vessel disease.
