---
layout: default
title: BCS70
nav_order: 4
---

# **BCS70**

The 1970 British Cohort Study (BCS70) is following the lives of around 17,000 people born in England, Scotland and Wales in a single week of 1970. Cohort members were genotyped during the biomedical sweep (sweep 10, aged 46-48). 

## Data availability 

| Data type       | Array/ Imputation panel       |Number samples   | Coverage    |
| :----           |    :----  |    :----    |   :----   |
| Genetic         | GSA Array   | 5,833 (5807 indiviuals)           | 654,027 Genetic variants  |
| Imputed       | TOPMed  | 5,598 individuals             | 8,640,849   Genetic variants  |
| DNA methylation | EPIC array  | 239 individuals             |  799,653   DNA methylation sites |

## Genotyping QC

Genotyping for 5905 samples (5807 individuals) was performed on the Infinium Global Screening Array-24 v3.0 (consisting of 654,027 genetic variants). One array plate (96 samples) failed during processing and therefore 96 of the samples were repeats. Genotype calling was performed using GenomeStudio (v2.0, Illumina) and quality control was completed using PLINK1.9 and PLINK2.0. 5830 samples were successfully read into GenomeStudio and mapped to a manifest file with the genome build GRCH37. Individuals were excluded if they had (i) they had > 2% missing data (136 samples excluded), (ii) their genotype predicted sex using X chromosome homozygosity was discordant with their reported sex (excluding females with an F value > 0.2 and males with an F value < 0.8) (15 samples excluded), (iii) they had excess heterozygosity [>3 standard deviation (SD) from the mean] (46 samples excluded), (iv) they were related to another individual in the sample (king-cutoff 0.0884) (35 samples excluded), where one individual from each pair of related samples was excluded based on the King greedy related algorithm. The samples which were on the failed array did not pass QC steps and only repeats were kept. The failed samples have been removed from the non QC'd data so that there is only one sample per person.We identified European samples using the GenoPred pipeline which involves (i) merging the BCS70 genotypes with data from 1000 genomes Phase 3, (ii) linkage disequilibrium pruning the overlapping single nucleotide polymorphisms (SNPs) such that no pair of SNPs within 1000 bp had r2 > 0.20 and (iii) using an elastic net model to establish which of the super populations the samples fall into (Africans [AFR], Admixed Americans [AMR], East Asians [EAS], Europeans [EUR] and South Asians [SAS]). We have not excluded non-European samples but have included a column in the basic demographics file which indicates this, which researchers can use to limit their samples to Europeans. Although each sample gets assigned to a superpopulation, there are some ancestral outliers within these groups (e.g. >4SD from mean in the PCs), which we have removed in addition to the non-European samples (European N=5,361). We have not removed these samples but provided a flag in the basic demographics file so samples can be filtered based on this. 

Prior to imputation SNPs with high levels of missing data (>3%), Hardy-Weinberg equilibrium P < 1e-6 or minor allele frequency <1% were excluded. The cleaned data were checked against the HRC reference panel r1.1 site list (Haplotype Reference Consortium, 2016) for strand issues, using a Perl script named HRC-1000G-check-bim.pl, v.4.3.0 (Rayner, Reference Rayner2020) from [the Wrayner/ McCartney tools box](https://www.chg.ox.ac.uk/~wrayner/tools/). We used the HRC panel for this step since the data were genome build GRCh37 and were mostly European. The genetic data were then recoded as vcf files before uploading to the TOPMed which uses Eagle2 to phase haplotypes, and Minimac4 (https://genome.sph.umich.edu/wiki/Minimac4) with the TOPMed reference panel. The genome build was updated to hg38 using LiftOver, which is implemented within the TOPMed server. 

Imputed genotypes were then filtered with PLINK2.0alpha, excluding SNPs with an R2 INFO score < 0.8 and recoded as binary PLINK format. Samples with >2% missing values, and SNPs with >2 alleles (using --max-allele 2), >3% missing values, Hardy-Weinberg equilibrium P < 1e-6 or a minor allele frequency of <1% were excluded (indels have not been excluded). The final quality controlled imputed set of genotypes contained 5,598 samples and ~8,640,849 variants and are provided in plink format (genome build: hg38).


## DNA methylation data 

| Data type       | Array       |Number samples | Data format |
| :---            |    :---   |    :---      |    :---  |  
| DNA methylation (batch1)     | Illumina EPIC array | 529  |     .rdat file             |
| DNA methylation (batch2)    | Illumina EPIC array | 1,298 (1,119 individuals)    |     .rdat file             |

### DNA methylation data preprocessing 

All data were QCd within R. Raw data for all datasets were used, prior to any quality control or normalization, and processed using the wateRmelon (Pidsley et al., 2013) package. Our stringent DNAm quality control pipeline included the following steps: i) excluding poorly performing samples based on methylated and unmethylated signal intensities; (ii) removing samples with a bisulphite conversion rate <80%; (iii) confirming reported sex through multidimensional scaling of X and Y chromosome sites; (iv) utilizing single nucleotide polymorphism (SNP) probes to verify genetic identity of matched samples; (v) employing the pfilter() function to exclude samples with >1% of probes with a detection P-value > 0.05; (vi) performing principal component analysis to identify and exclude outliers; and (vii) removing cross-hybridizing and SNP probes (Chen et al., 2013). Subsequent normalization of DNA methylation data was conducted using the nasen() function in wateRmelon (Pidsley et al., 2013). Any samples which have withdrawn consent or did not map to an ID have additioanlly been removed. After QC, the BCS70 DNA methylation dataset consisted of 239 samples and 799,653 DNA methylation sites. 

