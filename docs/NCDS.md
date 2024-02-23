---
layout: default
title: NCDS
nav_order: 3
---

# **NCDS**

The 1958 National Child Development Study (NCDS) is following the lives of an initial 17,415 people born in England, Scotland and Wales in a single week of 1958. It started in 1958 at birth, as the Perinatal Mortality Survey.

## Data availability 

| Data type       | Array       |Number samples | Coverage |
| :----            |    :----   |    :----     | :----    |  
| Genetic         | Combined  | 6,312 individuals       |     6,663,631 genetic variants             |
| DNA Methylation (batch1) | Illumina EPIC  |    541   |        ~800,000 DNA methylation sites        |
| DNA Methylation (batch2) | Illumina EPIC  |     1,377 (1,169 individuals)     |        ~800,000 DNA methylation sites        |
| Exome |  Illumina HiSeq 2500 |    1,000       |          -      |

## Genetic QC

<details>
  <summary> <b>TOPMed QC</b>  </summary>
  
Genotyping for 13,738 samples (6,431 unique individuals) was performed across seven different genotyping arrays (see Genotyping arrays). Quality control was completed using PLINK1.9, PLINK2.0, R v3.3.2 and RStudio v4.1.2. Each dataset was updated to GRCh37 build for consistency using the LiftOver software tool. For each chip individuals were excluded if they had (i) they had > 2% missing data (ii) their genotype predicted sex using X chromosome homozygosity was discordant with their reported sex (excluding females with an F value > 0.2 and males with an F value < 0.8) (iii) they had excess heterozygosity [>3 standard deviation (SD) from the mean] and (iv) they were related to another individual in the sample (–genome threshold 0.1875), removing samples with the most missing data. Prior to imputation SNPs with high levels of missing data (>3%), Hardy-Weinberg equilibrium P < 1x10-6 or minor allele frequency <1% were excluded. The genetic data were then recoded as vcf files before uploading to the TOPMed which uses Eagle2 to phase haplotypes, and Minimac4 (https://genome.sph.umich.edu/wiki/Minimac4) with the TOPMed reference panel.

Imputed genotypes were then filtered with PLINK2.0alpha, excluding SNPs with an R2 INFO score < 0.8 and recoded as binary PLINK format. Proceeding with PLINK1.9, samples with >2% missing values, and SNPs with >2 alleles, >3% missing values, Hardy-Weinberg equilibrium P < 1e-6 or a minor allele frequency of <1% were excluded. We combined data from five of the seven chips (Illumina 1.2M, Illumina Human 660-Quad, Infinium HumanHap 550K v1.1, Infinium HumanHap 550K v3 and Affymetrix v6) which had, high and similar imputation quality (based on number of SNPs after QC). The Illumina 15k Custom Chip and Affymetrix 500k were not included in the combined dataset since they produced lower quality results, yielding less high-quality imputed SNPs than the other arrays. It is worth noting all samples, bar five, were covered by the other arrays and the combined dataset consisted of 6471 individuals and 7,545,768 SNPs. We have included a column within the basic demographics file indicating which samples are included from which chip in the final combined dataset.
  
Further QC was conducted on the combined dataset where individuals were excluded if they had (i) they had > 2% missing (8 individuals excluded) and (ii) they were related to another individual in the sample (king-cutoff 0.0884) (23 excluded), where one individual from each pair of related samples was excluded based on the King greedy related algorithm. SNPs with high levels of missing data (>3%) (49,195 variants excluded) and a Hardy-Weinberg equilibrium P < 1e-6 were excluded (17 variants excluded). 

We identified European samples using the GenoPred pipeline, which involves (i) merging the MCS genotypes with data from 1000 genomes Phase 3, (ii) linkage disequilibrium pruning the overlapping single nucleotide polymorphisms (SNPs) such that no pair of SNPs within 1000 bp had r2 > 0.20 and (iii) using an elastic net model to establish which of the super populations the samples fall into (Africans [AFR], Admixed Americans [AMR], East Asians [EAS], Europeans [EUR] and South Asians [SAS]). We have not excluded non-European samples but have included a column in the basic demographics file which indicates this, which researchers can use to limit their samples to Europeans (N=6,382). Although each sample gets assigned to a superpopulation, there are some ancestral outliers within these groups (e.g. >4SD from mean in the PCs [N = excluded]), which researchers may want to remove (a flag it provided in the basic demographics file). The final dataset consists of 6,382 samples and 7,496,556 genetic variants (genome build: hg38). The data are provided in plink binary format.

</details>

<details>
  <summary> <b>HRC QC</b>  </summary>

Genotyping for 13,738 samples (6,431 unique individuals) was performed across seven different genotyping arrays (see [Genotyping arrays](https://github.com/CLS-Genetics/CLS-Genetics.github.io/blob/main/docs/NCDS.md#genotyping-arrays)). Quality control was completed using PLINK1.9, PLINK2.0, R v3.3.2 and RStudio v4.1.2. Each dataset was updated to GRCh37 build for consistency, using up-to-date strand files and a series of commands collated in the script Update Build (Robertson, 2012) or using the LiftOver software tool. For each chip individuals were excluded if they had (i) they had > 2% missing data (ii) their genotype predicted sex using X chromosome homozygosity was discordant with their reported sex (excluding females with an F value > 0.2 and males with an F value < 0.8) (iii) they had excess heterozygosity [>3 standard deviation (SD) from the mean] and (iv) they were related to another individual in the sample (--genome threshold 0.1875), removing samples with the most missing data. Prior to imputation SNPs with high levels of missing data (>3%), Hardy-Weinberg equilibrium P < 1x10-6 or minor allele frequency <1% were excluded. The genetic data were then recoded as vcf files before uploading to the Michigan Imputation Server which uses Eagle2 to phase haplotypes, and Minimac4 (https://genome.sph.umich.edu/wiki/Minimac4) with the HRC r1.1 reference panel.

Imputed genotypes were then filtered with PLINK2.0alpha, excluding SNPs with an R2 INFO score < 0.8 and recoded as binary PLINK format. Proceeding with PLINK1.9, samples with >2% missing values, and SNPs with >2 alleles, >3% missing values, Hardy-Weinberg equilibrium P < 1e-6 or a minor allele frequency of <1% were excluded. We combined data from five of the seven chips (Illumina 1.2M, Illumina Human 660-Quad, Infinium HumanHap 550K v1.1, Infinium HumanHap 550K v3 and Affymetrix v6) which had, high and similar imputation quality (based on number of SNPs after QC). The Illumina 15k Custom Chip and Affymetrix 500k were not included in the combined dataset since they produced lower quality results, yielding less high-quality imputed SNPs than the other arrays. It is worth noting all samples, bar five, were covered by the other arrays and the combined dataset consisted of 6420 individuals and 6,722,830 SNPs. We have included a column within the basic demographics file indicating which samples are included from which chip in the final combined dataset.

Further QC was conducted on the combined dataset where individuals were excluded if they had (i) they had > 2% missing (9 individuals excluded) and (ii) they were related to another individual in the sample (king-cutoff 0.0884) (16 excluded), where one individual from each pair of related samples was excluded based on the King greedy related algorithm. SNPs with high levels of missing data (>3%) (56,268 variants excluded) and a Hardy-Weinberg equilibrium P < 1e-6 were excluded. Samples were further excluded if they were classed as non-European, determined by merging the NCDS combined genotypes with data from 1000 genomes Phase 3), linkage disequilibrium pruning the overlapping single nucleotide polymorphisms (SNPs) such that no pair of SNPs within 50 bp had r2 > 0.20 and visually inspecting the first two genetic principal components along with the known ethnicities of the 1000 genomes sample to define European samples (N=83 excluded). The final quality controlled imputed set of genotypes contained 6312 samples and 6,663,631 variants (genome build: GRCh37/ hg19).

**When using this dataset please cite**:
[Bridges, E. C., Rayner, N. W., Mountford, H. S., Bates, T. C., & Luciano, M. (2023). Longitudinal Reading Measures and Genome Imputation in the National Child Development Study: Prospects for Future Reading Research. Twin Research and Human Genetics, 1-11](https://www.cambridge.org/core/journals/twin-research-and-human-genetics/article/longitudinal-reading-measures-and-genome-imputation-in-the-national-child-development-study-prospects-for-future-reading-research/FAD4EFD7CE42759BAB7A5491935B18FC).

The imputed data were QC'd and combined by CLS. QC and imputation of the Illumina Human 660-Quad was completed by CLS. 

## Genotyping arrays used in the QC'd data set 

Here is information on the individual genotyping chips used in the combined dataset. Breakdown of number of participants sampled on each array in the NCDS after removal of exclusions and duplications, and number of SNPs sequenced in each dataset [(Bridges et al., 2023)](https://www.cambridge.org/core/journals/twin-research-and-human-genetics/article/longitudinal-reading-measures-and-genome-imputation-in-the-national-child-development-study-prospects-for-future-reading-research/FAD4EFD7CE42759BAB7A5491935B18FC).

| Data type       | Array       |Number samples | N SNPs |
| :---            |    :---   |    :---      |    :---  |  
| Genetic         | Illumina 1.2M  | 2908        |     1157986              |
| Genetic         | Illumina 15k Custom Chip   | 1475        |    9803               |
| Genetic         | Illumina Human 660-Quad   | 871         |         582892          |
| Genetic         | Infinium HumanHap 550K v1.1   | 1436         |         555174          | 
| Genetic         |Infinium HumanHap 550K v3   | 2592         |       561303            |
| Genetic         |Affymetrix 500k  |1477      |      490032             | 
| Genetic         |Affymetrix v6 | 2979         |    934967               |

</details>

# Other genetic data availability

## All genotyping arrays (none-QCd)

If you would like to use the none-QCd data you can apply for the data from the separate genotyping chips. It is worth noting that these have been generated on different genotyping platforms, have multiple genome builds and some indiviuals have multiple samples.

## Exome sequencing data

| Data type       | Array       |Number samples | Data format |
| :---            |    :---   |    :---      |    :---  |  
| Exome sequencing    | Illumina HiSeq 2500 | 1000       |     FastQ             |

## DNA methylation data 

| Data type       | Array       |Number samples | Data format |
| :---            |    :---   |    :---      |    :---  |  
| DNA methylation (batch1)     | Illumina EPIC array | >541  |     .rdat file             |
| DNA methylation (batch2)    | Illumina EPIC array | 1,377 (1,169 individuals)    |     .rdat file             |

