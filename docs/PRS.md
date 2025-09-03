---
layout: default
title: Polygenic indexes
nav_order: 6
---

# **Polygenic indexes** 

We have generated polygenic indexes (PGI) in all of the CLS cohorts for multiple traits over a range of domains, as listed below. The PGI were generated through a standardised pipeline applied to the quality controlled and TOPMed imputed genetic data outlined on each cohort page of this site. PGI are available in each cohort using i) the full SNP lists in each cohort independently, and ii) harmonised SNP lists that are in common across all of the cohorts. 

These PGI are available from the UKDS under Special Licence at the following links:  
[NCDS PGIs](https://beta.ukdataservice.ac.uk/datacatalogue/studies/study?id=9440)  
[BCS PGIs](https://beta.ukdataservice.ac.uk/datacatalogue/studies/study?id=9439)  
[Next Steps PGIs](https://beta.ukdataservice.ac.uk/datacatalogue/studies/study?id=9438)  
[MCS PGIs](https://beta.ukdataservice.ac.uk/datacatalogue/studies/study?id=9437)  

The current PGI have been developed using a clumping and thresholding (C+T) approach, implemented in [PRSice-2](https://choishingwan.github.io/PRSice/), across five p-value thresholds. Full details on the approach used are given in the [UKDS documentation](https://doc.ukdataservice.ac.uk/doc/9440/mrdoc/pdf/ukds_user_guide_cls_pgis.pdf). The pipeline code used to generate the PGI is available on the [CLS Data GitHub](https://github.com/CLS-Data/CLS_PGI_repository).

Future releases of the PGI will include additional traits and PGI generated with model-based approaches e.g., LDpred2.  


## Current PGI available via the UKDS (v1.0, first release: 03/09/2025)
**Anthropometrics**

| Trait | Reference |
|-------|-----------|
| Birth weight | [Warrington et al. 2019](https://www.nature.com/articles/s41588-019-0403-1) |
| Body fat distribution | [Pulit et al. 2018](https://academic.oup.com/hmg/article/28/1/166/5098227) |
| Body Mass Index (childhood) | [Vogelezang et al. 2020](https://journals.plos.org/plosgenetics/article?id=10.1371/journal.pgen.1008718) |
| Body Mass Index (adulthood) | [Yengo et al. 2018](https://academic.oup.com/hmg/article/27/20/3641/5067845) |
| Grip strength | [Jones et al. 2021](https://www.nature.com/articles/s41467-021-20918-w) |
| Height | [Yengo et al. 2018](https://academic.oup.com/hmg/article/27/20/3641/5067845) |
| Waist circumference | [Christakoudi et al. 2021](https://www.nature.com/articles/s41598-021-89176-6) |

**Brain structure and cognition**

| Trait | Reference |
|-------|-----------|
| Alzheimer's disease | [Bellenguez et al. 2022](https://www.nature.com/articles/s41588-022-01024-z) |
| Cognition | [Savage et al. 2018](https://www.nature.com/articles/s41588-018-0152-6) |
| Hippocampal volume | [Liu et al. 2023](https://www.nature.com/articles/s41588-023-01425-8) |
| Parkinson's disease | [Nalls et al. 2019](https://www.thelancet.com/journals/laneur/article/PIIS1474-4422(19)30320-5) |

**Health behaviours**

| Trait | Reference |
|-------|-----------|
| Substance abuse | [Hatoum et al. 2023](https://www.nature.com/articles/s44220-023-00034-y) |
| Age at initiation of smoking | [Liu et al. 2019](https://www.nature.com/articles/s41588-018-0307-5) |
| Alcoholic drinks per week | [Liu et al. 2019](https://www.nature.com/articles/s41588-018-0307-5) |
| Cigarettes per day | [Liu et al. 2019](https://www.nature.com/articles/s41588-018-0307-5) |
| Diet | [Cole et al. 2020](https://www.nature.com/articles/s41467-020-15193-0) |

**Mental health**

| Trait | Reference |
|-------|-----------|
| Anxiety | [Forstner et al. 2021](https://www.nature.com/articles/s41380-019-0590-2) |
| ADHD | [Demontis et al. 2023](https://www.nature.com/articles/s41588-022-01285-8) |
| Autism spectrum disorder | [Grove et al. 2019](https://www.nature.com/articles/s41588-019-0344-8) |
| Bipolar disorder | [Mullins et al. 2021](https://www.nature.com/articles/s41588-021-00857-4) |
| Depressive symptoms | [Baselmans et al. 2019](https://www.nature.com/articles/s41588-018-0320-8) |
| Externalising problems | [Karlsson Linnér et al. 2021](https://www.nature.com/articles/s41593-021-00908-3) |
| Major depressive disorder | [Howard et al. 2019](https://www.nature.com/articles/s41593-018-0326-7) |
| Schizophrenia | [Trubetskoy et al. 2022](https://www.nature.com/articles/s41586-022-04434-5) |

**Personality**

| Trait | Reference |
|-------|-----------|
| Agreeableness | [Gupta et al. 2024](https://www.nature.com/articles/s41562-024-01951-3) |
| Conscientiousness | [Gupta et al. 2024](https://www.nature.com/articles/s41562-024-01951-3) |
| Extraversion | [Gupta et al. 2024](https://www.nature.com/articles/s41562-024-01951-3) |
| Openness to experience | [Gupta et al. 2024](https://www.nature.com/articles/s41562-024-01951-3) |
| Neuroticism | [Gupta et al. 2024](https://www.nature.com/articles/s41562-024-01951-3) |

**Physical health**

| Trait | Reference |
|-------|-----------|
| Age at menopause | [Ruth et al. 2021](https://www.nature.com/articles/s41586-021-03779-7) |
| Asthma | [Han et al. 2020](https://www.nature.com/articles/s41467-020-15649-3) |
| Blood pressure | [Keaton et al. 2024](https://www.nature.com/articles/s41588-024-01714-w) |
| Coronary artery disease | [Aragam et al. 2022](https://www.nature.com/articles/s41588-022-01233-6) |
| C-reactive protein | [Koskeridis et al. 2022](https://www.nature.com/articles/s41467-022-34688-6) |
| Fasting glucose | [Downie et al. 2022](https://link.springer.com/article/10.1007/s00125-021-05635-9) |
| HbA1c | [Sinnott-Armstrong et al. 2021](https://www.nature.com/articles/s41588-020-00757-z) |
| Hypertension | [Bi et al. 2020](https://www.cell.com/ajhg/fulltext/S0002-9297(20)30191-9) |
| Rheumatoid arthritis | [Ishigaki et al. 2022](https://www.nature.com/articles/s41588-022-01213-w) |
| Type 1 Diabetes | [Chiou et al. 2021](https://www.nature.com/articles/s41586-021-03552-w) |
| Type 2 Diabetes | [Suzuki et al. 2024](https://www.nature.com/articles/s41586-024-07019-6) |

**Social outcomes**

| Trait | Reference |
|-------|-----------|
| Education | [Okbay et al. 2022](https://www.nature.com/articles/s41588-022-01016-z) |
| Household Income | [Hill et al. 2019](https://www.nature.com/articles/s41467-019-13585-5) |
| Human Longevity | [Pilling et al. 2017](https://www.aging-us.com/article/101334/text) |
| Parental Lifespan | [Timmers et al. 2019](https://elifesciences.org/articles/39856) |

