---
layout: default
title: Ancestry and genetic similarity
nav_order: 10
---

# **Ancestry and genetic similarity**
This page provides a brief introduction to ancestry and genetic similarity as it is used in statistical genetics. 

## Available/forthcoming CLS Data
**Raw / imputed genotype data** – Available for all cohort members who provided a DNA sample that passed quality control. Data access via the CLS Data Access Committe. 

**CLS Polygenic Index (PGI) repository – Version 1 (July 2025)** – PGIs are available only for participants whose are genetically similar to the European reference panel from the 1000 Genomes Project Phase 3 (a widely used reference dataset of whole-genome sequencing data from diverse populations worldwide). We recommend researchers note this, the potential limitations of this, and a brief justification (see below). Data access via the UK Data Service.  

**CLS PGI repository – Version 2 (planned 2026)** – PGIs for a broader and more genetically diverse range of participants. Forthcoming.  

For data access procedures, please see the [Data Access page](/docs/access.md). 

## Suggested wording for outputs using Version 1 of the CLS polygenic index repository

_“Our study was limited to individuals who were genetically similar to European samples in 1000 Genomes Phase 3 as defined using an elastic net model (**delete as appropriate:)** in order to minimise sample heterogeneity and limit bias due to differential PGI performance across study individuals / to aid comparability with previous studies / given the use of less diverse cohorts / since comparable polygenic indexes were not available for all individuals). This limits the generalisability of our findings to the broader population. As genetic knowledge improves across the genetic similarity spectrum, future research should extend these findings to the entire population”_

## Background
Genetic analyses have predominantly been conducted on samples of individuals who are of “European ancestry” (Mills & Rahal, 2019). This has arisen for a number of reasons, including the underrepresentation of diverse population groups in genetic research studies; differences in availability of funding, expertise, technology, and infrastructure globally to study different populations; and the need to take into account correlations between genetic and environmental factors that differ across population groups and therefore may bias analyses when  incorrectly modelled. 

As a result, many existing Genome Wide Association Studies (GWAS), a research method used to identify genetic variations associated with specific traits, from which our polygenic indexes are derived, have restricted their study samples to groups that are relatively genetically homogenous. These samples are often described in terms of “genetic ancestry”, which is commonly assigned on the basis of arbitrary cutoffs based on genetic similarity to other groups of individuals. That is, genetic ancestry labels are heavily simplified statistical modelling constructs with labels drawn from external sources. An individual labelled as “European genetic ancestry” is simply defined as such by virtue of having a genotype that is more similar to individuals in a reference dataset who are also labelled as “European” (for a detailed discussion of this, see (Coop, 2022)). While this approach is somewhat blunt and reductive, it can be necessary given the difficulty of accurately modelling real-world complexity and the need to simplify reality to meet modelling assumptions (e.g., of relatively homogenous samples).  

It is important to acknowledge the limitations that this approach presents. For example, analyses restricted to samples that are genetically similar to one sample set (e.g., those most similar to European samples in [1000 Genomes Phase 3](https://www.internationalgenome.org/category/phase-3/)) may not generalise to samples that are more similar to other sample sets (e.g., those more similar to East Asian samples in 1000 Genomes Phase 3), and ultimately, the broader and more diverse population of interest. See for example Martin et al., 2019. 

Researchers should be aware that the PGIs available in the CLS PGI repository are restricted to individuals who are genetically similar to the 1000 Genomes Phase 3 European sample set. This genetic similarity was defined using an elastic net model on pruned SNPs after merging the cohort genotypes with the 1000 Genomes Phase 3 data.  

This approach means that cohort individuals who provided biosamples but are genetically similar to sample sets in 1000 Genomes Phase 3 which are not labelled as European are not currently present in the CLS PGI repository.  

The Millennium Cohort Study (MCS) and Next Steps are comprised of diverse individuals who have provided genetic data and can be included in ongoing multi-ancestry initiatives to increase diversity and representativeness in genetic research: please apply for our data or contact [Tim Morris](mailto:t.t.morris@ucl.ac.uk) and [David Bann](mailto:david.bann@ucl.ac.uk) with questions and to discuss potential collaboration. 

## Samples included/excluded in the CLS PGI repository across the CLS studies.

| Cohort     | Passed QC (1) | Excluded (>4 SD from PC1) (2) | Included (3) |
|------------|---------------|-------------------------------|--------------|
| NCDS       | 6,396         | 72                            | 6,396        |
| BCS        | 5,598         | 237                           | 5,361        |
| Next Steps | 1,568         | 296                           | 1,272        |
| MCS        | 20,247        | 3,142                         | 17,105       |
  
(1): Number of individuals who passed genetic quality control.  
(2): Number of individuals excluded for being more than 4 standard deviations from the mean of the first principal component of population structure.  
(3): Number of individuals genetically similar to European samples in 1000 Genomes Phase 3 and included in the PGI repository.  


## References
Coop, G. (2022). Genetic similarity versus genetic ancestry groups as sample descriptors in human genetics. ArXiv Preprint ArXiv:2207.11595.

Martin, A. R., Kanai, M., Kamatani, Y., Okada, Y., Neale, B. M., & Daly, M. J. (2019). Clinical use of current polygenic risk scores may exacerbate health disparities. Nature Genetics, 51(4). https://doi.org/10.1038/s41588-019-0379-x.

Mills, M. C., & Rahal, C. (2019). A scientometric review of genome-wide association studies. In Communications Biology. https://doi.org/10.1038/s42003-018-0261-x.
