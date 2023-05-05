---
layout: default
title: MCS
nav_order: 2
---

# **MCS**

The Millennium Cohort Study (MCS), known as ‘Child of the New Century’ to cohort members and their families, is following the lives of around 19,000 young people born across England, Scotland, Wales and Northern Ireland in 2000-02. The study began with an original sample of 18,818 cohort members. 

## Data availability 

| Data type       | Array / Imputation panel      |Number samples | Number variants  |
| :---            |    :----:   |    :----:     |     ---:   |        
| Genetic         | GSA Array v1   | ~20,000          | XX    |  
| Imputed        | TOPMED   | ~20,000          | XX    |  
| Whole exome sequencing| TWIST  | XX           | XX       |


## Genetic QC

Genotyping for 21,556 samples (21,418 individuals) was performed on the Infinium Global Screening Array-24 v1.0. For more details on collection of samples, DNA extraction methods and laboratory procedures see [the MCS working paper](https://cls.ucl.ac.uk/wp-content/uploads/2020/08/CLS-working-paper-2020-7-Collection-of-DNA-samples-and-genetic-data-at-scale-in-the-UK-Millennium-Cohort-Study.pdf).  Genotype calling was performed using GenomeStudio (v2.0, Illumina) and quality control was completed using PLINK1.9 and PLINK2.0 (Chang et al., 2015). 21,556 samples were successfully read into GenomeStudio and data for 618,540 variants were written into a final manifest file and plink ped format using the plink genotyping module. Duplicate samples (retaining those with higher genotyping rates) and samples which could no longer be included in the sample (withdrawn consent) were removed prior to QC (338 samples excluded). Individuals were excluded if they had (i) they had > 3% missing data (677 samples excluded), (ii) their genotype predicted sex using X chromosome homozygosity was discordant with their reported sex (excluding females with an F value > 0.2 and males with an F value < 0.8), if these could not be rectified using family relationships (154 samples excluded), and (iii) they had excess heterozygosity [>3 standard deviation (SD) from the mean] (94 samples excluded). 

We used KING to create a list of parent and family IDs to update. We updated the family IDs and then updated the parent IDs. Instances where parents and children were mixed up and this could not be rectified were removed. We also identified a list of samples that had been merged into larger families, e.g. cousins and siblings in the parent generation. We then calculated which parents were biological parents to the children. For final validation, we ran the Plink Mendelian error check. This checks the transmission of all variants in trios is possible.

Prior to imputation SNPs with high levels of missing data (>3%), Hardy-Weinberg equilibrium P < 0.001 or minor allele frequency <1% were excluded. The genetic data were then recoded as vcf files before uploading to the TOPMed Imputation Server which uses Eagle2 to phase haplotypes, and Minimac4 (https://genome.sph.umich.edu/wiki/Minimac4) with the TOPmed reference panel. Imputed genotypes were then filtered with PLINK2.0alpha, excluding SNPs with an R2 INFO score < 0.8 and recoded as binary PLINK format. Proceeding with PLINK1.9, samples with >2% missing values, and SNPs with >2 alleles, >3% missing values, Hardy-Weinberg equilibrium P < 0.0001 or a minor allele frequency of <1% were excluded. We identified European samples by merging the MCS genotypes with data from 1000 genomes Phase 3), linkage disequilibrium pruning the overlapping single nucleotide polymorphisms (SNPs) such that no pair of SNPs within 3000 bp had r2 > 0.10 and visually inspecting the first two genetic principal components along with the known ethnicities of the 1000 genomes sample to define European samples. We have not excluded non-European samples but have provided a file "EUR_samples.txt" which researchers can use to limit their samples to Europeans. 


