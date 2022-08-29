--- 
title: "ADViSELipidomics user manual"
author: "Fabio Della Rocca"
date: "2022-08-29"
site: bookdown::bookdown_site
documentclass: book
bibliography: [book.bib, packages.bib]
url: your book url like https://shinyfabio.github.io/ADViSELipidomics_book/
# cover-image: path to the social sharing image like images/cover.jpg
description: |
  This is the user manual of ADViSELipidomics.
biblio-style: apalike
csl: chicago-fullnote-bibliography.csl
---

# About

This is the documentation of the ADViSELipidomics package. ADViSELipidomics is a novel Shiny app for the preprocessing, analysis, and visualization of lipidomics data. It copes with the outputs from [LipidSearch](https://www.thermofisher.com/it/en/home/industrial/mass-spectrometry/liquid-chromatography-mass-spectrometry-lc-ms/lc-ms-software/multi-omics-data-analysis/lipid-search-software.html) and [LIQUID](https://github.com/PNNL-Comp-Mass-Spec/LIQUID) for lipid identification and quantification, and with data available from the [Metabolomics Workbench](https://www.metabolomicsworkbench.org/). ADViSELipidomics extracts information by parsing lipid species (using [LIPID MAPS classification](https://www.lipidmaps.org/data/classification/lipid_cns.html)) and, together with information available on the samples, allows performing several exploratory and statistical analyses. In the presence of internal lipid standards in the experiment, ADViSELipidomics can normalize the data matrix, providing absolute values of concentration per lipid and sample. Moreover, it allows the identification of differentially abundant lipids in simple and complex experimental designs, dealing with batch effect correction. 

The PDF version of this user manual can be downloaded from here:

<img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/download.svg" width="20" height="20"> [ADViSELipidomics_book.pdf](https://github.com/ShinyFabio/ADViSELipidomics_book/raw/main/docs/ADViSELipidomics_book.pdf)


If you use **ADViSELipidomics** in your publications, we appreciate if you can cite:

E. Del Prete *et al.* (2022) ADViSELipidomics: a workflow for analyzing lipidomics data DOI: ............



