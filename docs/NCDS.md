---
layout: default
title: NCDS
nav_order: 3
---

## NCDS

The 1958 National Child Development Study (NCDS) is following the lives of an initial 17,415 people born in England, Scotland and Wales in a single week of 1958. It started in 1958 at birth, as the Perinatal Mortality Survey.

## Data availability 

| Data type       | Array       |Number samples | N SNPs |Data size   | Link to apply        |
| :---            |    :----:   |    :----:     |   :----:|  :----:  |          ---:        |
| Genetic         | Illumina 1.2M  | 2908        |     1157986              | XXGB       |<https://cls.ucl.ac.uk/data-access-training/data-access/> |
| Genetic         | Illumina 15k Custom Chip   | 1475        |    9803               | XXGB       |<https://cls.ucl.ac.uk/data-access-training/data-access/> |
| Genetic         | Illumina Human 660-Quad   | 871         |         582892          | XXGB       |<https://cls.ucl.ac.uk/data-access-training/data-access/> |
| Genetic         | Infinium HumanHap 550K v1.1   | 1436         |         555174          | XXGB       |<https://cls.ucl.ac.uk/data-access-training/data-access/> |
| Genetic         |Infinium HumanHap 550K v3   | 2592         |       561303            | XXGB       |<https://cls.ucl.ac.uk/data-access-training/data-access/> |
| Genetic         |Affymetrix 500k  | 490032         |      490032             | XXGB       |<https://cls.ucl.ac.uk/data-access-training/data-access/> |
| Genetic         |Affymetrix v6 | XX         |    934967               | XXGB       |<https://cls.ucl.ac.uk/data-access-training/data-access/> |
| DNA Methylation | EPIC  | 934967          |                | XXGB       |<https://cls.ucl.ac.uk/data-access-training/data-access/> |


## Genetic QC

For a subsample of the participants, a biomedical survey was also conducted at age 44, which included the collection of DNA samples (Power & Elliot, 2006). Here we describe the preparation and imputation of 13,738 overlapping genotyped samples (6,431 unique individuals) collected from the NCDS participants on seven different arrays. All quality control was conducted using Plink v1.90b4, R v3.3.2 and RStudio v4.1.2. Code used to carry out these processes, along with further information regarding externally developed scripts and resources, is publicly available as a GitHub repository (Bridges, 2022). Quality control was carried out on each of the seven genetic datasets according to the following steps. SNPs with a call-rate of less than 98% were removed (Turner et al., 2011), and SNPs that were not in Hardy-Weinberg equilibrium were removed at a threshold of P <1x10-6.  Individuals failing quality control were also removed. Those with a genotyping call-rate of less than 97% were then removed (The Wellcome Trust Case Control Consortium, 2007). Individuals showing unexpected levels of heterozygosity (+/- 3 SD from the mean) were removed.

Each dataset was updated to GRCh37 build for consistency, using up-to-date strand files and a series of commands collated in the script Update Build (Robertson, 2012, see Supplementary Information A for further detail). Heterozygous haploid errors were present in six of the seven chips. They were removed by first ensuring that all variants in the pseudo-autosomal region had the correct chromosome code for the Plink format, and any remaining errors were set to missing. Any individuals with discrepant or ambiguous sex data were removed, excluding the Affymetrix 500K chip, for which X chromosome data was not available. A small number (n=8) of related samples (representing 6 individuals) were identified using a relatedness threshold of 0.1875, and the sample with the most missing data from each related pair was removed. The computational burden to control for genomic relatedness of 6 cases was deemed too high to warrant their inclusion, and has the advantage that users will not need to check for relatedness prior to their own analysis. 

To identify genetic ancestry outliers, the data was merged with 1000 Genomes reference data (The 1000 Genomes Project Consortium, 2015), and Principal Components Analysis (PCA) was conducted in Plink to identify outliers (n=17). Outliers were removed according to the procedure documented by Meyer (2021a, 2021b), using a theta value of 3. 

The cleaned data were checked against the HRC reference panel r1.1 site list (The Haplotype Reference Consortium, 2016) for strand issues, using a specifically developed Perl script named HRC-1000G-check-bim.pl, v.4.3.0 (Rayner, 2020). This script checks for strand inconsistencies between the data and the reference panel, and generates a series of Plink commands which can then be used to remove or update any problematic loci. Perl v5.24.0 was used, followed by Plink to make the aforementioned necessary changes. Sorted VCF files were generated for each chromosome using BCFtools (Danecek et al., 2021). A final set of quality control checks were carried out on the VCF files post-conversion, using a specifically developed Python script (Zhan  & Liu, 2016). These checks include identifying duplicated sites, invalid genotypes and NonSNP sites. Python v2.7.10 was used. No issues requiring further action were identified. The data were uploaded to the Michigan Imputation Server for quality control and imputation (Das et al., 2016). Imputation was carried out against the European population of the HRC r1.1 2016 reference panel, using the Minimac4 pipeline. Eagle v2 phasing was used.

Following imputation, quality control checks were carried out using the “ic” script developed by Rayner (2016), which incorporates a series of Perl commands to check alternate allele frequencies and imputation quality, Perl v5.24.0 (Rayner, 2016). This output can be used to evaluate the quality of an imputed dataset, including alternate allele frequency counts and frequency counts of the R2 imputation quality score by chromosome.

There was considerable overlap of individuals between arrays, with many individuals having been genotyped on multiple arrays. After imputation, we determined the number of unique samples that should be retained on each array by retaining the highest quality sample for each individual (Table S165). This was determined by listing all samples in order of chip quality, determined by the number of SNPs with an information score > 0.8 after imputation (Al-Soufi et al., 2021). 


