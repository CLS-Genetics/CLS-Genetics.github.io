# CLS Genomics data 

## Introduction 

Here at CLS we have genetic data for three cohorts: the 1958 Childhood Development Study (NCDS), the 1970 British Cohort Study (BCS70) and the Millennium Cohort Study (MCS). This wiki provides documentation on the genetic QC for these datasets and what is available to researchers.

The genetic data is managed by CLS at UCL (https://cls.ucl.ac.uk/). For details on how to access see CLS Data Access (https://cls.ucl.ac.uk/data-access-training/data-access/).

### NCDS

### MCS

### BCS70

Genotyping for 5905 samples was performed on the Infinium Global Screening Array-24 v3.0 (consisting of 654,027 genetic variants). One plate (96 samples) failed during processing and therefore 96 of the samples were repeats. Genotype calling was performed using GenomeStudio (v2.0, Illumina) and quality control was completed using PLINK1.9 and PLINK2.0. 5833 samples were successfully read into GenomeStudio and mapped to a manifest file with the genome build GRCH37. Individuals were excluded if they had (i) they had > 5% missing data (97 samples excluded), (ii) their genotype predicted sex using X chromosome homozygosity was discordant with their reported sex (excluding females with an F value > 0.2 and males with an F value < 0.8) (77 samples excluded), (iii) they had excess heterozygosity [>3 standard deviation (SD) from the mean] (48 samples excluded), (iv) they were related to another individual in the sample (king-cutoff 0.0884) (42 samples excluded), where one individual from each pair of related samples was excluded based on the King greedy related algorithm (v) they were classed as non-European, determined by merging the BCS70 genotypes with data from 1000 genomes Phase 3), linkage disequilibrium pruning the overlapping single nucleotide polymorphisms (SNPs) such that no pair of SNPs within 3000 bp had r2 > 0.10 and visually inspecting the first two genetic principal components along with the known ethnicities of the 1000 genomes sample to define European samples (N=197 excluded). Prior to imputation SNPs with high levels of missing data (>5%), Hardy-Weinberg equilibrium P < 0.0001 or minor allele frequency <1% were excluded. The genetic data were then recoded as vcf files before uploading to the TOPMed Imputation Server which uses Eagle2 to phase haplotypes, and Minimac4 (https://genome.sph.umich.edu/wiki/Minimac4) with the TOPMed reference panel. The genome build was updated to hg38 using LiftOver, which is implemented within the TOPMed server. Imputed genotypes were then filtered with PLINK2.0alpha, excluding SNPs with an R2 INFO score < 0.8 and recoded as binary PLINK format. Proceeding with PLINK1.9, samples with >5% missing values, and SNPs with >2 alleles, >5% missing values, Hardy-Weinberg equilibrium P < 0.0001 or a minor allele frequency of <1% were excluded. The final quality controlled imputed set of genotypes contained 5433 samples and 8,604,230 variants (genome build: hg38).

## Polygenic risk scores

## Changing the version of the theme and/or Jekyll

Simply edit the relevant line(s) in the `Gemfile`.

## Adding a plugin

The Just the Docs theme automatically includes the [`jekyll-seo-tag`] plugin.

To add an extra plugin, you need to add it in the `Gemfile` *and* in `_config.yml`. For example, to add [`jekyll-default-layout`]:

- Add the following to your site's `Gemfile`:

  ```ruby
  gem "jekyll-default-layout"
  ```

- And add the following to your site's `_config.yml`:

  ```yaml
  plugins:
    - jekyll-default-layout
  ```

Note: If you are using a Jekyll version less than 3.5.0, use the `gems` key instead of `plugins`.

## Publishing your site on GitHub Pages

1.  If your created site is `YOUR-USERNAME/YOUR-SITE-NAME`, update `_config.yml` to:

    ```yaml
    title: YOUR TITLE
    description: YOUR DESCRIPTION
    theme: just-the-docs

    url: https://YOUR-USERNAME.github.io/YOUR-SITE-NAME

    aux_links: # remove if you don't want this link to appear on your pages
      Template Repository: https://github.com/YOUR-USERNAME/YOUR-SITE-NAME
    ```

2.  Push your updated `_config.yml` to your site on GitHub.

3.  In your newly created repo on GitHub:
    - go to the `Settings` tab -> `Pages` -> `Build and deployment`, then select `Source`: `GitHub Actions`.
    - if there were any failed Actions, go to the `Actions` tab and click on `Re-run jobs`.

## Building and previewing your site locally

Assuming [Jekyll] and [Bundler] are installed on your computer:

1.  Change your working directory to the root directory of your site.

2.  Run `bundle install`.

3.  Run `bundle exec jekyll serve` to build your site and preview it at `localhost:4000`.

    The built site is stored in the directory `_site`.

## Publishing your built site on a different platform

Just upload all the files in the directory `_site`.

## Customization

You're free to customize sites that you create with this template, however you like!

[Browse our documentation][Just the Docs] to learn more about how to use this theme.

## Licensing and Attribution

This repository is licensed under the [MIT License]. You are generally free to reuse or extend upon this code as you see fit; just include the original copy of the license (which is preserved when you "make a template"). While it's not necessary, we'd love to hear from you if you do use this template, and how we can improve it for future use!

The deployment GitHub Actions workflow is heavily based on GitHub's mixed-party [starter workflows]. A copy of their MIT License is available in [actions/starter-workflows].

----

[^1]: [It can take up to 10 minutes for changes to your site to publish after you push the changes to GitHub](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll#creating-your-site).

[Jekyll]: https://jekyllrb.com
[Just the Docs]: https://just-the-docs.github.io/just-the-docs/
[GitHub Pages]: https://docs.github.com/en/pages
[GitHub Pages / Actions workflow]: https://github.blog/changelog/2022-07-27-github-pages-custom-github-actions-workflows-beta/
[Bundler]: https://bundler.io
[use this template]: https://github.com/just-the-docs/just-the-docs-template/generate
[`jekyll-default-layout`]: https://github.com/benbalter/jekyll-default-layout
[`jekyll-seo-tag`]: https://jekyll.github.io/jekyll-seo-tag
[MIT License]: https://en.wikipedia.org/wiki/MIT_License
[starter workflows]: https://github.com/actions/starter-workflows/blob/main/pages/jekyll.yml
[actions/starter-workflows]: https://github.com/actions/starter-workflows/blob/main/LICENSE
