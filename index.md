---
title: Home
layout: home
---

# ECHO-AIR
A repository of scripts used for converting emissions to concentrations and health impacts using the InMAP Source Receptor Matrix (ISRM). 

*Libby Koolik, UC Berkeley*

Last modified July 7, 2023

----

## Purpose and Goals
The Intervention Model for Air Pollution (InMAP) is a powerful first step towards lowering key technical barriers by making simplifying assumptions that allow for streamlined predictions of PM<sub>2.5</sub> concentrations resulting from emissions-related policies or interventions.\[[*](https://doi.org/10.1371/journal.pone.0176131)\] InMAP performance has been validated against observational data and WRF-Chem, and has been used to perform source attribution and exposure disparity analyses.\[[*](https://doi.org/10.1126/sciadv.abf4491), [*](https://doi.org/10.1073/pnas.1816102116), [*](https://doi.org/10.1073/pnas.1818859116)\] The InMAP Source-Receptor Matrix (ISRM) was developed by running the full InMAP model tens of thousands of times to understand how a unit perturbation of emissions from each grid cell affects concentrations across the grid. However, both InMAP and the ISRM require considerable computational and math proficiency to run and an understanding of various atmospheric science principles to interpret. Furthermore, estimating health impacts requires additional knowledge and calculations beyond InMAP. Thus, a need arises for a standalone and user-friendly process for comparing air quality health disparities associated with various climate change policy scenarios.

The ultimate goal of this repository is to create a pipeline for estimating disparities in health impacts associated with incremental changes in emissions. Annual average PM<sub>2.5</sub> concentrations are estimated using the [InMAP Source Receptor Matrix](https://www.pnas.org/doi/full/10.1073/pnas.1816102116) for California.

----

[^1]: [It can take up to 10 minutes for changes to your site to publish after you push the changes to GitHub](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll#creating-your-site).

[Just the Docs]: https://just-the-docs.github.io/just-the-docs/
[GitHub Pages]: https://docs.github.com/en/pages
[README]: https://github.com/just-the-docs/just-the-docs-template/blob/main/README.md
[Jekyll]: https://jekyllrb.com
[GitHub Pages / Actions workflow]: https://github.blog/changelog/2022-07-27-github-pages-custom-github-actions-workflows-beta/
[use this template]: https://github.com/just-the-docs/just-the-docs-template/generate
