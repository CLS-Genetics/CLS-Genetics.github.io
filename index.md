---
title: CLS Genomics data 
layout: home
---

## Introduction 

Here at CLS we have genetic data for three cohorts: the 1958 Childhood Development Study (NCDS), the 1970 British Cohort Study (BCS70) and the Millennium Cohort Study (MCS). This wiki provides documentation on the genetic QC for these datasets and what is available to researchers.

The genetic data is managed by CLS at UCL (https://cls.ucl.ac.uk/). For details on how to access see CLS Data Access (https://cls.ucl.ac.uk/data-access-training/data-access/).

---
title: NCDS
layout: home
---

### MCS

### BCS70

Genotyping for 5905 samples was performed on the Infinium Global Screening Array-24 v3.0 (consisting of 654,027 genetic variants). One plate (96 samples) failed during processing and therefore 96 of the samples were repeats. Genotype calling was performed using GenomeStudio (v2.0, Illumina) and quality control was completed using PLINK1.9 and PLINK2.0. 5833 samples were successfully read into GenomeStudio and mapped to a manifest file with the genome build GRCH37. Individuals were excluded if they had (i) they had > 5% missing data (97 samples excluded), (ii) their genotype predicted sex using X chromosome homozygosity was discordant with their reported sex (excluding females with an F value > 0.2 and males with an F value < 0.8) (77 samples excluded), (iii) they had excess heterozygosity [>3 standard deviation (SD) from the mean] (48 samples excluded), (iv) they were related to another individual in the sample (king-cutoff 0.0884) (42 samples excluded), where one individual from each pair of related samples was excluded based on the King greedy related algorithm (v) they were classed as non-European, determined by merging the BCS70 genotypes with data from 1000 genomes Phase 3), linkage disequilibrium pruning the overlapping single nucleotide polymorphisms (SNPs) such that no pair of SNPs within 3000 bp had r2 > 0.10 and visually inspecting the first two genetic principal components along with the known ethnicities of the 1000 genomes sample to define European samples (N=197 excluded). Prior to imputation SNPs with high levels of missing data (>5%), Hardy-Weinberg equilibrium P < 0.0001 or minor allele frequency <1% were excluded. The genetic data were then recoded as vcf files before uploading to the TOPMed Imputation Server which uses Eagle2 to phase haplotypes, and Minimac4 (https://genome.sph.umich.edu/wiki/Minimac4) with the TOPMed reference panel. The genome build was updated to hg38 using LiftOver, which is implemented within the TOPMed server. Imputed genotypes were then filtered with PLINK2.0alpha, excluding SNPs with an R2 INFO score < 0.8 and recoded as binary PLINK format. Proceeding with PLINK1.9, samples with >5% missing values, and SNPs with >2 alleles, >5% missing values, Hardy-Weinberg equilibrium P < 0.0001 or a minor allele frequency of <1% were excluded. The final quality controlled imputed set of genotypes contained 5433 samples and 8,604,230 variants (genome build: hg38).

## Polygenic risk scores

This is a *bare-minimum* template to create a Jekyll site that uses the [Just the Docs] theme. You can easily set the created site to be published on [GitHub Pages] – the [README] file explains how to do that, along with other details.

If [Jekyll] is installed on your computer, you can also build and preview the created site *locally*. This lets you test changes before committing them, and avoids waiting for GitHub Pages.[^1] And you will be able to deploy your local build to a different platform than GitHub Pages.

More specifically, the created site:

- uses a gem-based approach, i.e. uses a `Gemfile` and loads the `just-the-docs` gem
- uses the [GitHub Pages / Actions workflow] to build and publish the site on GitHub Pages

Other than that, you're free to customize sites that you create with this template, however you like. You can easily change the versions of `just-the-docs` and Jekyll it uses, as well as adding further plugins.

[Browse our documentation][Just the Docs] to learn more about how to use this theme.

To get started with creating a site, just click "[use this template]"!

----

[^1]: [It can take up to 10 minutes for changes to your site to publish after you push the changes to GitHub](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll#creating-your-site).

[Just the Docs]: https://just-the-docs.github.io/just-the-docs/
[GitHub Pages]: https://docs.github.com/en/pages
[README]: https://github.com/just-the-docs/just-the-docs-template/blob/main/README.md
[Jekyll]: https://jekyllrb.com
[GitHub Pages / Actions workflow]: https://github.blog/changelog/2022-07-27-github-pages-custom-github-actions-workflows-beta/
[use this template]: https://github.com/just-the-docs/just-the-docs-template/generate
