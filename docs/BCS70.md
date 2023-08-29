---
layout: default
title: BCS70
nav_order: 4
---

# **BCS70**

The 1970 British Cohort Study (BCS70) is following the lives of around 17,000 people born in England, Scotland and Wales in a single week of 1970.

## Data availability 

| Data type       | Array/ Imputation panel       |Number samples   | Coverage    |
| :----           |    :----  |    :----    |   :----   |
| Genetic         | GSA Array   | 5,833             | 654,027 Genetic variants  |
| Imputed       | TOPMed  | 5,407             | 8,604,230 Genetic variants  |
| DNA methylation | EPIC array  | 255             | ~800,000 DNA methylation sites |

## Genotyping QC

Genotyping for 5905 samples (5807 individuals) was performed on the Infinium Global Screening Array-24 v3.0 (consisting of 654,027 genetic variants). One plate (96 samples) failed during processing and therefore 96 of the samples were repeats. Genotype calling was performed using GenomeStudio (v2.0, Illumina) and quality control was completed using PLINK1.9 and PLINK2.0. 5830 samples were successfully read into GenomeStudio and mapped to a manifest file with the genome build GRCH37. Individuals were excluded if they had (i) they had > 2% missing data (136 samples excluded), (ii) their genotype predicted sex using X chromosome homozygosity was discordant with their reported sex (excluding females with an F value > 0.2 and males with an F value < 0.8) (15 samples excluded), (iii) they had excess heterozygosity [>3 standard deviation (SD) from the mean] (46 samples excluded), (iv) they were related to another individual in the sample (king-cutoff 0.0884) (35 samples excluded), where one individual from each pair of related samples was excluded based on the King greedy related algorithm (v) they were classed as non-European, determined by merging the BCS70 genotypes with data from 1000 genomes Phase 3), linkage disequilibrium pruning the overlapping single nucleotide polymorphisms (SNPs) such that no pair of SNPs within 3000 bp had r2 > 0.10 and visually inspecting the first two genetic principal components along with the known ethnicities of the 1000 genomes sample to define European samples (N=191 excluded). Prior to imputation SNPs with high levels of missing data (>3%), Hardy-Weinberg equilibrium P < 1e-6 or minor allele frequency <1% were excluded. The genetic data were then recoded as vcf files before uploading to the TOPMed Imputation Server which uses Eagle2 to phase haplotypes, and Minimac4 (https://genome.sph.umich.edu/wiki/Minimac4) with the TOPMed reference panel. The genome build was updated to hg38 using LiftOver, which is implemented within the TOPMed server. Imputed genotypes were then filtered with PLINK2.0alpha, excluding SNPs with an R2 INFO score < 0.8 and recoded as binary PLINK format. Proceeding with PLINK1.9, samples with >2% missing values, and SNPs with >2 alleles, >3% missing values, Hardy-Weinberg equilibrium P < 1e-6 or a minor allele frequency of <1% were excluded. The final quality controlled imputed set of genotypes contained 5407 samples and ~8,600,000 variants and are provided in plink format (genome build: hg38).
