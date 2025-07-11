---
layout: default
title: Ancestry and genetic similarity
nav_order: 10
---

# **Ancestry and genetic similarity** 

Genetic analyses have predominantly been conducted on samples of individuals who are of “European ancestry” (Mills & Rahal, 2019). This emphasis has arisen due to numerous reasons, including the underrepresentation of some population groups in genetic research studies; biases in availability of funding, expertise, technology, and infrastructure globally to study different populations; and the desire to control for correlations amongst genetic, geographical and environmental factors that can bias analyses when incorrectly modelled or unmodelled.

As a result, many existing GWAS (from which our polygenic indexes are derived) have restricted their study samples to groups that are relatively genetically homogenous. These samples are often described in terms of "genetic ancestry", which is commonly assigned based on arbitrary cutoffs based on genetic similarity to other groups of individuals on principal components of genetic variation. That is, genetic ancestry labels are heavily simplified statistical modelling constructs with labels drawn from external sources. An individual labelled as "European genetic ancestry" is simply defined as such by virtue of having a genotype that is more similar to individuals in a reference dataset who are also labelled as "European" (for a detailed discussion of this, see (Coop, 2022)). This approach is clearly blunt and reductive, but can be necessary given the difficulty of accurately modelling real-world complexity and the need to simplify reality to meet modelling assumptions (e.g., of relatively homogenous samples). 

It is critical to acknowledge the limitations that this approach presents. For example, analyses restricted to samples that are genetically similar to one sample set (e.g., those most similar to European samples in 1000 Genomes Phase 3) may not generalise to samples that are more similar to other sample sets (e.g., those more similar to East Asian samples in 1000 Genomes Phase 3), and ultimately, the broader and more diverse population of interest. This has been demonstrated in previous studies showing that the predictive performance of polygenic indexes is inconsistent across different samples (Martin et al., 2019). 

Researchers should be aware that the PGIs available in the CLS PGI repository are restricted to cohort participants who are genetically similar to the 1000 Genomes Phase 3 European sample set. This genetic similarity was defined using an elastic net model on pruned SNPs after merging the cohort genotypes with the 1000 Genomes Phase 3 data. 

This approach means that cohort participants who are genetically similar to other sample sets in 1000 Genomes Phase 3 than Europeans sample set and who provided biosamples are not present in the CLS PGI repository. Any outputs using the CLS PGIs should clearly communicate this fact, the limitations that it entails, and ensure that the conclusions drawn are appropriate to the data.

The MCS and Next Steps have collected genetic data from cohort participants and these study members can be included in ongoing multi-ancestry initiatives to increase diversity and representativeness in genetic research; if our data would be useful to you then please contact us. We plan to release future versions of the CLS PGI repository with PGI derived for all cohort participants, but in the meantime, researchers can access the full genomewide genetic data on all cohort participants via the CLS Data Access Committee. 


# **Statements on ancestry and genetic similarity** 
Researchers using the CLS PGIs must acknowledge in research outputs that they are limited to those who are genetically similar to European samples in 1000 Genomes Phase 3, the limitations that this will impose upon their results, and a brief justification. For example:

“Our study was limited to cohort members who were genetically similar to European samples in 1000 Genomes Phase 3 as defined using an elastic net model (**delete as appropriate:** in order to minimise sample heterogeneity and limit bias / to aid comparability with previous studies / given less diverse cohorts / since comparable polygenic scores were not available across ancestral groups). This approach will limit the generalisability of our findings to the broarder UK population. As genetic knowledge improves across the genetic similarlity spectrum future research should extend these findings to other groups.”


## References

Coop, G. (2022). Genetic similarity versus genetic ancestry groups as sample descriptors in human genetics. ArXiv Preprint ArXiv:2207.11595.

Martin, A. R., Kanai, M., Kamatani, Y., Okada, Y., Neale, B. M., & Daly, M. J. (2019). Clinical use of current polygenic risk scores may exacerbate health disparities. Nature Genetics, 51(4). https://doi.org/10.1038/s41588-019-0379-x.

Mills, M. C., & Rahal, C. (2019). A scientometric review of genome-wide association studies. In Communications Biology. https://doi.org/10.1038/s42003-018-0261-x.
 

