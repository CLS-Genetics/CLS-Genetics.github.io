---
layout: default
title: MCS
nav_order: 2
---

# **MCS**

The Millennium Cohort Study (MCS), known as ‘Child of the New Century’ to cohort members and their families, is following the lives of around 19,000 young people born across England, Scotland, Wales and Northern Ireland in 2000-02. The study began with an original sample of 18,818 cohort members. Cohort members were genotyped at age 14.

## Data availability 

| Data type       | Array / Imputation panel      |Number samples | Coverage  |
| :----          |    :----   |    :----     |    :----     |        
| Genetic (non QCd)        | GSA Array v1   | 21,159          | 618,540 genetic variants     |  
| Imputed  (QCd)      | TOPMED   | 20,247        |8,720,874 genetic variants     |  
| Whole exome sequencing| TWIST  | 14,753           | 1,916,636 sites         |


## Genetic QC

Genotyping for 21,556 samples (21,418 individuals) was performed on the Infinium Global Screening Array-24 v1.0. For more details on collection of samples, DNA extraction methods and laboratory procedures see [Fitzsimons et al 2022](https://bristoluniversitypressdigital.com/view/journals/llcs/13/1/article-p169.xml).  Genotype calling was performed using GenomeStudio (v2.0, Illumina) and quality control was completed using PLINK1.9 and PLINK2.0 (Chang et al., 2015). 21,556 samples were successfully read into GenomeStudio and data for 618,540 variants were written into a final manifest file and plink ped format using the plink genotyping module. Samples which could no longer be included in the sample (e.g. withdrawn consent) were removed prior to QC (338 samples excluded). Individuals were excluded if they had (i) they had > 2% missing data (677 samples excluded), (ii) they had excess heterozygosity [>3 standard deviation (SD) from the mean] (78 samples excluded), and (iii) their genotype predicted sex using X chromosome homozygosity was discordant with their reported sex (excluding females with an F value > 0.2 and males with an F value < 0.8), if these could not be rectified using family relationships (86 samples excluded). 

We used KING to create a list of parent and family IDs to update, excluding duplicate samples (retaining those with a higher genotyping rate). We updated the family IDs and then updated the parent IDs. Instances where parents and children were mixed up and this could not be rectified were removed (26 samples excluded). We also identified a list of samples that had been merged into larger families, where there were multiple mother and fathers. No samples were removed but we have created a flag within the basic demographics file indicating where one trio from each family has been selected (212 individuals can be excluded based on this flag). It is worth noting that king highlighted some inbreeding within this cohort, where CM's parents are related to one another (e.g. to third or fourth degree). Additionally, there is relatedness between CMs and other members of the cohort (e.g. cousins, MZ/ DZ twins and siblings). This will need to be accounted for in analysis. For final validation, we ran the Plink Mendelian error check. This checks the transmission of all variants in trios is possible. 

Prior to imputation SNPs with high levels of missing data (>3%), Hardy-Weinberg equilibrium P < 1e-6 (based on a subset of unrelated, European samples) or minor allele frequency <1% were excluded. The cleaned data were checked against the HRC reference panel r1.1 site list (Haplotype Reference Consortium, 2016) for strand issues, using a Perl script named HRC-1000G-check-bim.pl, v.4.3.0 (Rayner, Reference Rayner2020) from [the Wrayner/ McCartney tools box](https://www.chg.ox.ac.uk/~wrayner/tools/). This script checks for strand inconsistencies between the data and the reference panel, and generates a series of Plink commands that can then be used to remove or update mismatched loci. We used the HRC panel for this step since the data were genome build GRch37 and were mostly European. 

The genetic data were then recoded as vcf files before uploading to the TOPMed Imputation Server which uses Eagle2 to phase haplotypes, and Minimac4 (https://genome.sph.umich.edu/wiki/Minimac4) with the TOPMed reference panel.  The genome build was updated to hg38 using LiftOver, which is implemented within the TOPMed server. Imputed genotypes were then filtered with PLINK2.0alpha, excluding SNPs with an R2 INFO score < 0.8 and recoded as binary PLINK format. Samples with >2% missing values and SNPs with >3% missing values, >2 alleles (using --max-allele 2, which filters out the multiallelic variants but when a variant has exactly one ALT allele and it's a missing-code, these filters treat it as having only one allele) or a minor allele frequency of <1% were excluded (indels have not been excluded). The duplicate samples were removed, retatining those which had the higher genotying rate (83 individuals excluded). We identified European samples using the [GenoPred pipeline](https://github.com/opain/GenoPred/tree/master/Scripts/Ancestry_identifier), which involves (i) merging the MCS genotypes with data from 1000 genomes Phase 3, (ii) linkage disequilibrium pruning the overlapping single nucleotide polymorphisms (SNPs) such that no pair of SNPs within 1000 bp had r2 > 0.20 and (iii) using an elastic net model to establish which of the super populations the samples fall into (Africans [AFR], Admixed Americans [AMR], East Asians [EAS], Europeans [EUR] and South Asians [SAS]). We have not excluded non-European samples but have included a column in the basic demographics file which indicates this, which researchers can use to limit their samples to Europeans (N=17,460). Although each sample gets assigned to a superpopulation, there are some ancestral outliers within these groups (e.g. >4SD from mean in the PCs), which researchers may want to remove. A further 10 individuals have been removed due to withdrawal of consent.

The final dataset consists of 20,247 samples and 8,720,874  genetic varaints (genome build: hg38). The data are provided in plink binary format.

### Number of mother/ fathers/ children after QC:

| Category       | Count   |
| :----          |    :----   |   
| Mother [M]      | 7,781 |
| Father [F]      | 4,635   | 
| Child/ cohort member [C] | 7,841  |
|Trios | 3,119   | 

## Genetic data (non-QCd)

These data have not been QCd, however where sample swaps were identified these have been rectified in this sample. The final dataset consists of 21,159 samples and 618,540  genetic varaints (genome build: hg19/GRCh37). The data are provided in plink binary format unless requested otherwise. 

## Whole exome sequencing (WES) data

The WES data were generated and QCd by Sanger. 14,791 individuals from MCS, including 7,807 children and 6,975 of their parents, were exome-sequenced using TWIST capture baits (Twist Custom Panel: Core exome plus Broad panel; Twist Design ID: NGSTECustom_0001418) and Illumina NovaSeq S4 100PE, to an average depth of ~68X. Samples were excluded with VerifyBamID score > 0.05 due to having possible contamination. BWA-MEM was used to map the reads to GRCh38 with BWA-MEM, then SNV and indel calling was conducted with GATK HaplotypeCaller, GenomicsDBImport and GenotypeGVCFs (GATK version 4.2.4.0), following GATK best practices. Hail v0.2.105 was used to conduct sample, variant and genotype QC, as described below.
 
<details>
  <summary> <b>WES QC</b>  </summary>

  
<b>Sample QC</b> 

For sample QC the following steps were taken: 

1) Data were filtered to include only biallelic SNVs; 2) Variants were removed with an internal allele frequency of <= 0.001 and variants with a call rate of <= 0.99, which reduced the number of variants from 4,920,291 to 386,148; 3) MCS data were merged with 1,000 Genomes phase 3, retaining variants present in both. Variants were removed if they had a low call rate (< 0.99), low allele frequency (< 0.05) or low Hardy-Weinberg equilibrium p-value (< 1e-5), variants in long range linkage disequilibrium regions and palindromic SNVs. ; 4) PCA was conducted using Hail’s hwe_normalized_pca function, followed by gnomad’s assign_population_pcs function on the first ten principal components to predict which superpopulation (European, South Asian, East Asian, African, American, or other) each MCS sample was most similar to. 12,851 MCS samples were assigned as being most similar to the European samples from 1000 Genomes. ; 5) The sample_qc function was run in Hail and the output was stratified by superpopulation; and 6) Calls were removed with DP (depth) < 20, GQ (genotype quality) < 20 or VAF (variant allele fraction) < 0.25, and then calculated the following metrics per sample: number of SNVs, Transition/Transversion ratio, het/hom ratio, heterozygosity rate, number of transitions, number of transversions, number of insertions, number of deletions, and insertion/deletion ratio. 302 samples were excluded who fell outside of the median +/-4 median absolute deviations compared to samples from the same superpopulation for at least one metric.

<b>Variant QC</b> 

A random forest model was employed for variant quality control (QC) to differentiate true positive variants from false positives using varied metrics. True positive variants were drawn from several high-quality datasets, including high confidence sites in 1000 Genomes, SNVs present in 1000 Genomes on the Omni 2.5 genotyping array, indels from Mills and Devine data, and SNVs and indels from HapMap3. Variants not meeting criteria (QD < 2, FS > 60, MQ < 30) were classified as false positives.

The model was trained on chromosome 20 using these annotations and then applied to the full dataset. It evaluated features such as QD, meanHetAB, is_CA, SOR, variant_type and more, with specific inclusions like is_CA and meanHetAB to eliminate C>A errors introduced during library preparation.

Variants were scored and grouped by the random forest model's output. Thresholds for score bins were established by reviewing cumulative counts of true and false positive variants per bin, taking into account the transmitted/untransmitted ratio for synonymous singletons using data from 3,132 trios.

To determine hard filters for variants and genotypes, combinations of random forest bin scores and genotype quality metrics (DP, GQ, HetAB) were tested, setting genotypes to missing below certain thresholds. These filters were assessed by precision and recall of variants in the NA12878 Genome in a Bottle sample, the proportion of true/false positives retained, and the ratio of transmitted to untransmitted synonymous singletons.

Optimal filters for SNVs were set with a random forest bin score of fewer than 82, DP of less than 5, GQ under 15, and AB below 0.2, yielding a precision of 0.931 and recall of 0.953, while capturing 97.87% of true positives and only 0.27% of false positives, with a nearly balanced transmitted:untransmitted ratio for synonymous singletons. Indels had different filtering criteria: random forest bin score less than 58, DP under 10, GQ below 20, and AB less than 0.3, achieving a precision of 0.774 and recall of 0.691, retaining 91.185% of true positives and 0.274% of false positives.
  
</details>


