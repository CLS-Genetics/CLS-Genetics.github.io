---
layout: default
title: NCDS
nav_order: 3
---

# **NCDS**

The 1958 National Child Development Study (NCDS) is following the lives of an initial 17,415 people born in England, Scotland and Wales in a single week of 1958. It started in 1958 at birth, as the Perinatal Mortality Survey.

## Data availability 

| Data type       | Array       |Number samples | N SNPs |
| :---            |    :----:   |    :----:     |    ---: |  
| Genetic         | Illumina 1.2M  | 2908        |     1157986              |
| DNA Methylation | EPIC  |          |                |
| Exome |  - |    -       |          -      |-


## Genetic QC

For a subsample of the participants, a biomedical survey was also conducted at age 44, which included the collection of DNA samples (Power & Elliot, 2006). Here we describe the preparation and imputation of 13,738 overlapping genotyped samples (6,431 unique individuals) collected from the NCDS participants on seven different arrays. All quality control was conducted using Plink v1.90b4, R v3.3.2 and RStudio v4.1.2. Code used to carry out these processes, along with further information regarding externally developed scripts and resources, is publicly available as a GitHub repository (Bridges, 2022). Quality control was carried out on each of the seven genetic datasets according to the following steps. SNPs with a call-rate of less than 97% were removed (Turner et al., 2011), and SNPs that were not in Hardy-Weinberg equilibrium were removed at a threshold of P <1x10-6. Indiviuals with a genotyping call-rate of less than 98% were then removed (The Wellcome Trust Case Control Consortium, 2007). Individuals showing unexpected levels of heterozygosity (+/- 3 SD from the mean) were removed.

## Individual genotyping chips

Here is information on the individual genotyping chips used 

| Data type       | Array       |Number samples | N SNPs |
| :---            |    :----:   |    :----:     |    ---: |  
| Genetic         | Illumina 1.2M  | 2908        |     1157986              |
| Genetic         | Illumina 15k Custom Chip   | 1475        |    9803               |
| Genetic         | Illumina Human 660-Quad   | 871         |         582892          |
| Genetic         | Infinium HumanHap 550K v1.1   | 1436         |         555174          | 
| Genetic         |Infinium HumanHap 550K v3   | 2592         |       561303            |
| Genetic         |Affymetrix 500k  | 490032         |      490032             | 
| Genetic         |Affymetrix v6 | XX         |    934967               |
| DNA Methylation | EPIC  |        |                |


