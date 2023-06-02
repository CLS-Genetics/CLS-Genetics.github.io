---
layout: default
title: MCS
nav_order: 2
---

# **MCS**

The Millennium Cohort Study (MCS), known as ‘Child of the New Century’ to cohort members and their families, is following the lives of around 19,000 young people born across England, Scotland, Wales and Northern Ireland in 2000-02. The study began with an original sample of 18,818 cohort members. 

## Data availability 

| Data type       | Array / Imputation panel      |Number samples | Coverage  |
| :----          |    :----   |    :----     |    :----     |        
| Genetic (non QCd)        | GSA Array v1   | 21,107          | 618,540 genetic variants     |  
| Imputed  (QCd)      | TOPMED   | 20,257        | 8,580,431 genetic variants     |  
| Whole exome sequencing| TWIST  | QC in progress           | QC in progress         |


## Genetic QC

Genotyping for 21,556 samples (21,418 individuals) was performed on the Infinium Global Screening Array-24 v1.0. For more details on collection of samples, DNA extraction methods and laboratory procedures see [the MCS working paper](https://cls.ucl.ac.uk/wp-content/uploads/2020/08/CLS-working-paper-2020-7-Collection-of-DNA-samples-and-genetic-data-at-scale-in-the-UK-Millennium-Cohort-Study.pdf).  Genotype calling was performed using GenomeStudio (v2.0, Illumina) and quality control was completed using PLINK1.9 and PLINK2.0 (Chang et al., 2015). 21,556 samples were successfully read into GenomeStudio and data for 618,540 variants were written into a final manifest file and plink ped format using the plink genotyping module. Samples which could no longer be included in the sample (e.g. withdrawn consent) were removed prior to QC (338 samples excluded). Individuals were excluded if they had (i) they had > 3% missing data (677 samples excluded), (ii) they had excess heterozygosity [>3 standard deviation (SD) from the mean] (78 samples excluded), and (iii) their genotype predicted sex using X chromosome homozygosity was discordant with their reported sex (excluding females with an F value > 0.2 and males with an F value < 0.8), if these could not be rectified using family relationships (86 samples excluded). 

We used KING to create a list of parent and family IDs to update. We updated the family IDs and then updated the parent IDs. Instances where parents and children were mixed up and this could not be rectified were removed (26 samples excluded). We also identified a list of samples that had been merged into larger families, where there were multiple mother and fathers. No samples were removed but we have created a flag within the basic demographics file indicating where one trio from each family has been selected (228 individuals can be excluded based on this flag). Some of these are duplicate samples which have been flagged previously and were identified using --genome in plink (with a flag to retain those with a higher genotyping rate). It is worth noting that king highlighted some inbreeding within this cohort, where CM's parents are related to one another (e.g. to third or fourth degree). Additionally, there is relatedness between CMs and other members of the cohort (e.g. cousins, MZ/ DZ twins and siblings). This will need to be accounted for in analysis. For final validation, we ran the Plink Mendelian error check. This checks the transmission of all variants in trios is possible. 

Prior to imputation SNPs with high levels of missing data (>3%), Hardy-Weinberg equilibrium P < 1e-6 (based on a subset of unrelated, European samples) or minor allele frequency <1% were excluded. The genetic data were then recoded as vcf files before uploading to the TOPMed Imputation Server which uses Eagle2 to phase haplotypes, and Minimac4 (https://genome.sph.umich.edu/wiki/Minimac4) with the TOPMed reference panel. Imputed genotypes were then filtered with PLINK2.0alpha, excluding SNPs with an R2 INFO score < 0.8 and recoded as binary PLINK format. Proceeding with PLINK1.9, samples with >2% missing values, and SNPs with >2 alleles, >3% missing values, or a minor allele frequency of <1% were excluded. The duplicate samples were removed, retatining those which had the higher genotying rate (83 individuals excluded). We identified European samples using the [GenoPred pipeline](https://github.com/opain/GenoPred/tree/master/Scripts/Ancestry_identifier) which involves (i) merging the MCS genotypes with data from 1000 genomes Phase 3, (ii) linkage disequilibrium pruning the overlapping single nucleotide polymorphisms (SNPs) such that no pair of SNPs within 1000 bp had r2 > 0.20 and (iii) using an elastic net model to establish which of the super populations the samples fall into (Africans [AFR], Admixed Americans [AMR], East Asians [EAS], Europeans [EUR] and South Asians [SAS]). We have not excluded non-European samples but have included a column in the basic demographics file which indicates this, which researchers can use to limit their samples to Europeans (N=17,460). The final dataset consists of 20,257 samples and 8,580,431  genetic varaints (genome build: hg38). 


