---
layout: default
title: Next Steps
nav_order: 5
---

# **Next Steps**

Next Steps, previously known as the Longitudinal Study of Young People in England (LSYPE), follows the lives of around 16,000 people in England born in 1989-90. Cohort members were genotyped at age 32-33 (sweep 9). For information on the saliva sampling and an analysis of response rates see [Adali et al 2025](https://discovery.ucl.ac.uk/id/eprint/10205053/).

## Data availability 

| Data type       | Array / Imputation panel      |Number samples | Coverage  |
| :----          |    :----   |    :----     |    :----     |        
| Genetic (non QCd)        | GSA Array v3   | 1,681          | 654,027 genetic variants     |  
| Imputed  (QCd)      | TOPMED   | 1,568       |8,084,945 genetic variants     | 

## Genetic QC

Genotyping for 1683 samples was performed on the Infinium Global Screening Array-24 v3.0 (consisting of 654,027 genetic variants). Genotype calling was performed using GenomeStudio (v2.0, Illumina) and quality control was completed using PLINK1.9 and PLINK2.0. 1681 samples were successfully read into GenomeStudio and mapped to a manifest file with the genome build GRCh38. Individuals were excluded if (i) > they had 2% missing data (57 samples excluded), (ii) their genotype predicted sex using X chromosome homozygosity was discordant with their reported sex (excluding females with an F value > 0.2 and males with an F value < 0.8) (36 samples excluded), (iii) they had excess heterozygosity [>3 standard deviation (SD) from the mean] (18 samples excluded), (iv) they were related to another individual in the sample (king-cutoff 0.0884) (5 samples excluded), where one individual from each pair of related samples was excluded based on the King greedy related algorithm. We identified European samples using the GenoPred pipeline which involves (i) merging the Next Steps genotypes with data from 1000 genomes Phase 3, (ii) linkage disequilibrium pruning the overlapping single nucleotide polymorphisms (SNPs) such that no pair of SNPs within 1000 bp had r2 > 0.20 and (iii) using an elastic net model to establish which of the super populations the samples fall into (Africans [AFR], Admixed Americans [AMR], East Asians [EAS], Europeans [EUR] and South Asians [SAS]). We have not excluded non-European samples but have included a column in the basic demographics file which indicates this, which researchers can use to limit their samples to Europeans. Although each sample gets assigned to a superpopulation, there are some ancestral outliers within these groups (e.g. >4SD from mean in the PCs/ Tukey#s outlier method), which we have flagged in addition to the non-European samples (European N=1272). We have not removed these samples but provided a flag in the basic demographics file so samples can be filtered based on this.

Prior to imputation SNPs with high levels of missing data (>3%) and Hardy-Weinberg equilibrium P < 1e-6 were excluded. The cleaned data were checked against the TOPMed reference panel for strand issues, using a Perl script named HRC-1000G-check-bim.pl, v.4.3.0 (Rayner, Reference Rayner2020) from the Wrayner/ McCartney tools box. The genetic data were then recoded as vcf files before uploading to the TOPMed which uses Eagle2 to phase haplotypes, and Minimac4 (https://genome.sph.umich.edu/wiki/Minimac4) with the TOPMed reference panel. 

Imputed genotypes were then filtered with PLINK2.0alpha, excluding SNPs with an R2 INFO score < 0.8 and recoded as binary PLINK format. Samples with >2% missing values, and SNPs with >2 alleles (using –max-allele 2), >3% missing values, Hardy-Weinberg equilibrium P < 1e-6 or a minor allele frequency of <1% were excluded (indels have not been excluded). The final quality controlled imputed set of genotypes contained 1,568 samples and 8,084,945 genetic variants and are provided in plink format (genome build: hg38).
