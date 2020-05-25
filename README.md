# BLUP: Brain Learning Unicorn Project

Can a model predict the genetic profile of an individual based on brain imagery derived data?

*Trying to deal with new stuff learned at the amazing Brainhack school*

Team work: UKBB-team with Hannah Kiesow [@hannahmaykiesow](https://twitter.com/hannahmaykiesow)

Project contributors: 
BHS, 
Elise Alix Douard, Kuldeep Kumar [@meetkd007](https://twitter.com/meetkd007) (extracting data from UKBB servers), Hannah Kiesow
& anyone interested (with access rigths to UKBiobank?)


## Quick presentation

Welcome to this draft dear unicorn student ! 

<p align="center">
  <img src="https://media.giphy.com/media/CzQ9Kl1UIt8hG/giphy.gif">
</p>
<p> <font size="1.5"> Source: https://media.giphy.com/</font></p> 

I am Elise, Ph.D. student since near to 4 years, and working on **the contribution of genetic to neurodevelopmental disorders** as autism. 

[/!\ unwanted article advertisment /!\ ](https://www.biorxiv.org/content/10.1101/2020.03.09.979815v1.full)

I don't really fit in a specific domain (genetic/cognitive neurosciences/psychology/neurosciences). I guess it is what we call a unicorn student?

I currently work with genetic data (Copy Number Variants), clinical phenotypes and doing a lot of statistics and graphs. But my initial formation was in cogitive neurosciences where I started to work with multimodal data (combination of Arterial Spin Labelling MRI data and Eye-tracking data).  

Since I started my Ph.D., I never used MRI data anymore, and I am here to take a revange on that. 

I am also an Open Sciences enthusiast!

**Skills:**

- Data management (feed me with multimodal data plz)
- Satistics
- Debugging codes

**Here to learn:**

- Universal languages and tools to share science 
- Machine/Deep learning (more complex stats!)
- Python libraries to change from the R routine

# Project draft: Brain Learning Unicorn Project

## Summary

<p>Can a model predict if an individual is carrier of a pathogenic genetic copy number variant based on Brain imagery derived data?</p> 

This project aims to feed a **learning** model with **brains** to predict if an individual is carrier of a pathogenic **genetic** variant (meaning that the DNA alteration is deleterious and formally associated to neurodevelopmental disorders and other psychiatric disorders).

The hypothesis is not based on strong assumptions (even if there is multiple publications showing brain alterations associated to pathogenic CNVs), the focus will be on learning how to apply machine learning model for **multimodal dataset** (derived anatomical MRI data, genetic, other clinical data).

## Background

#### What is a pathogenic genetic Copy Number Variants (CNV)?

A pathogenic CNV is a gain or a loss of a DNA portion, which encompassed genes essential for the normal development of an individual, and which is formally associated to neurodevelopmental disorders or psychiatric disorders. 

<p align="center"> <img src="Figure 1_page-0001.jpg"> 
</p> 

**Figure 1:** Representation of the 16p11.2 CNV. (A) 16p11.2 region with genes (Refseq indentification) and segmental duplications corresponding to breakpoint 4 and 5 (where the DNA is more susceptible to break). Coordinates are based on Hg19 version of the genome reference. (B) Coding genes encompassed in the 16p11.2 locus and scores corresponding to their intolerance to loss of function (pLI, observed/expected (o/e), and LOEUF defined by gnomAD v.2.1.1, Karczewski et al., bioRxiv, 2019). Genes in red are intolerant to loss of function. 

<font size="1.5">Source: Chapter in press</font>


#### Is there specific brain alteration patterns associated to these CNVs?

- **Structural alterations**: 

Multiple studies shown an effect of pathogenic CNVs on global and regional brain structures. 

[Sandra Martin-Brevet et al (2018)](http://www.sciencedirect.com/science/article/pii/S000632231831401X) *Big up Sandra!*: 
"*Quantifying the Effects of 16p11.2 Copy
Number Variants on Brain Structure:
A Multisite Genetic-First Study*"

This paper shows that beyound an effect of the well known 16p11.2 CNV on global brain morphometry, regional alterations were observed in the insula, calcarine cortex, transverse temporal gyrus, caudate and hippocampus. There was a partial overlap with results of meta-analyses performed across psychiatric disorders.

<p align="center">
  <img src="https://ars.els-cdn.com/content/image/1-s2.0-S000632231831401X-gr3.jpg">
</p>

**Figure 2:** Overlap between voxel-based and surface-based results for cortical alterations associated with gene dosage. The relationship between gene dosage and the morphometric features was compared in n = 361. The voxel-based and surface-based statistical maps are thresholded at the multiple comparisons–corrected p value and then projected on the cortical surface mesh. Regions with effect size >1 Cohen’s d and overlapping between voxel-based and surface-based analyses are (A) the bilateral insula, transverse temporal gyrus, calcarine cortex and (B) the precentral, superior and middle temporal gyri. L, left; R, right; VBM, voxel-based morphometry.

<p> <font size="1.5">Source: Sandra Martin-Brevet http://www.sciencedirect.com/science/article/pii/S000632231831401X</font>
</p>

- **Connectivity alterations**:

An effect on connectivity have also been widely shown, but the affected connections vary from the cohorts used. 

[Clara Moreau et al (2019)](https://www.biorxiv.org/content/10.1101/862615v1.full) *Big up Clara!*: 
"*Neuropsychiatric mutations delineate functional brain connectivity dimensions contributing to autism and schizophrenia*"

<p align="center">
  <img src="https://www.biorxiv.org/content/biorxiv/early/2019/12/06/862615/F1.large.jpg?width=800&height=600&carousel=1">
</p>

**Figure 3:** Connectome-wide effects of CNVs. (a-b) Scatterplot (hexagonal plot), showing estimates (beta values) from connectome-wide association studies (CWAS) performed between 16p11.2 (a) and 22q11.2 (b) CNVs and their respective controls. In total, 2,080 beta estimates were obtained from a linear model computed from z-scored connectomes based on the variance of the respective controls. The color hue represents the number of beta estimates in the hexagon bin. Y axis: beta values associated with deletions (CWAS comparing deletions vs controls). X axis: beta-values associated with duplications (CWAS comparing duplications vs controls). (c-d) Each chord diagram shows the top 20% of connections surviving FDR correction (q < 0.05) from the 16p11.2 deletion (c) and 22q11.2 deletion (d) CWAS. Each chord represents a significantly altered connection between two functional seed regions. All 64 seed regions are represented in the dark grey inner circle. The width of the seed region in the grey inner circle corresponds to the number of altered connections. Seed regions are grouped into 12 functional networks (outer ring, Supplementary Table S1.9). Networks are represented in 12 brains below the two diagrams. Red chords represent overconnectivity and blue chords underconnectivity.

<font size="1.5">Source: Clara Moreau https://www.biorxiv.org/content/10.1101/862615v1.full</font>

### Problematic: 

#### Main problematic: 

Can a model predict if an individual is carrier of a pathogenic genetic copy number variant based on Brain imagery derived data?

(here is what I want to work on the most)
1) Avoiding the transformation of the data 
2) Deal with missing values (see 24''58min in the [presentation of Gaël Varoquaux](https://www.youtube.com/watch?reload=9&v=wIMJVgkQjNY&feature=youtu.be))

### Aims: 

#### Main goal: 
Compare the model performances when infering the genetic profile of an individual.

Learning how to:
1) Properly share project related files
2) Use machine learning models 
3) Use python instead of R

## Tools 

- Git/Github to share the scripts and results 
- Python using nilearn and sklearn libraries
- Jupyter notebook to keep track of the project
- Compute Quebec to run the analyses on the complete sample (<3,000?)

## Data

A first thought is to use data from [UK Biobank](https://www.ukbiobank.ac.uk/):
- From the genetic side: [Kendall et al. (2019)](https://www.cambridge.org/core/journals/the-british-journal-of-psychiatry/article/cognitive-performance-and-functional-outcomes-of-carriers-of-pathogenic-copy-number-variants-analysis-of-the-uk-biobank/0D144F6880A46DC94EE27ADEACB5942B) already published a paper investigating 33 pathogenic CNV using 420,247 individuals.
From this paper, they have established a list of 1,265 individuals with pottentially pathogenic CNVs.
- From the MRI side: All derived structural, diffusion and fMRI data are available for 40,000 individuals. I will focus on structural data processed on FreeSurfer. Click [here for the detailed processing pipeline](https://biobank.ctsu.ox.ac.uk/crystal/crystal/docs/brain_mri.pdf).
- From the phenotypic side: sex, age, ... all the interesting data pertinent for the project which are available for most individuals from this cohort.

The final dataset will be a smaller sample of individuals carriers of the most pathogenic CNVs (among the 1,265 selected by [Kendall et al. (2019)](https://www.cambridge.org/core/journals/the-british-journal-of-psychiatry/article/cognitive-performance-and-functional-outcomes-of-carriers-of-pathogenic-copy-number-variants-analysis-of-the-uk-biobank/0D144F6880A46DC94EE27ADEACB5942B)) vs. controls.
These individuals will be selected among the 40,000 with derived MRI data.

<p align="center">
  <img src="DataMethod.png">
</p>

<p><span style="color:red">/!\ The most pathogenic CNVs are really rare, the sample may be much smaller.</span></p>

## Deliverables

In this GitHub repository:
- README file
- A detailed documentation explaining how the data were acquired, processed, analysed and describing the model used.
- Jupyter notebook detailing the data (selection, distribution,...), the implementation of machine learning algorithms, and the results
- All related scipts
- Slides (using Rise) presenting the project

## References

Kendall Kimberley M. et al., “Cognitive Performance and Functional Outcomes of Carriers of Pathogenic Copy Number Variants: Analysis of the UK Biobank.” The British Journal of Psychiatry 214, no. 5 (May 2019): 297–304. https://doi.org/10.1192/bjp.2018.301.

Martin-Brevet Sandra et al., “Quantifying the Effects of 16p11.2 Copy Number Variants on Brain Structure: A Multisite Genetic-First Study.” *Biological Psychiatry*, 84, no. 4 (2018): 253–64. https://doi.org/10.1016/j.biopsych.2018.02.1176.

Moreau Clara et al., “Neuropsychiatric Mutations Delineate Functional Brain Connectivity Dimensions Contributing to Autism and Schizophrenia.” *BioRxiv*, (2019), 862615. https://doi.org/10.1101/862615.





