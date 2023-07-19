---
title: Home
layout: home
nav_order: 1
---

<img src="/assets/echo-air_logo-01.png" alt="drawing" width="200"/>

A repository of scripts used for converting emissions to concentrations and health impacts using the InMAP Source Receptor Matrix (ISRM). 

*Libby H. Koolik, Álvaro Alvarado, Amy Budahn, Laurel Plummer, Julian D. Marshall, and Joshua S. Apte*

Last modified July 19, 2023

<b>Note: this website is currently under construction and is being actively updated.</b>

----

## Purpose and Goals
The Intervention Model for Air Pollution (InMAP) is a powerful first step towards lowering key technical barriers by making simplifying assumptions that allow for streamlined predictions of PM<sub>2.5</sub> concentrations resulting from emissions-related policies or interventions.[^1] InMAP performance has been validated against observational data and WRF-Chem, and has been used to perform source attribution and exposure disparity analyses.[^2]<sup>,</sup> [^3]<sup>,</sup> [^4] The InMAP Source-Receptor Matrix (ISRM) was developed by running the full InMAP model tens of thousands of times to understand how a unit perturbation of emissions from each grid cell affects concentrations across the grid. However, both InMAP and the ISRM require considerable computational and math proficiency to run and an understanding of various atmospheric science principles to interpret. Furthermore, estimating health impacts requires additional knowledge and calculations beyond InMAP. Thus, a need arises for a standalone and user-friendly process for comparing air quality health disparities associated with various climate change policy scenarios.

The ultimate goal of this repository is to create a pipeline for estimating disparities in health impacts associated with incremental changes in emissions. Annual average PM<sub>2.5</sub> concentrations are estimated using the [InMAP Source Receptor Matrix](https://www.pnas.org/doi/full/10.1073/pnas.1816102116) for California.

----
## Documentation

This website serves as the living documentation for the ECHO-AIR model. The navigation pane on the left will help you navigate through Getting Started, Running the Code, Technical Code Details, and any other additional supporting information.

Currently, the model is configured and validated for California ISRM calculations. In the near future, I will validate it on the national ISRM as well. 

----
## References
[^1]: [Tessum CW, Hill JD, Marshall JD (2017) InMAP: A model for air pollution interventions. PLOS ONE 12(4)](https://doi.org/10.1371/journal.pone.0176131).
[^2]: [Tessum CW, et al., (2021) PM<sub>2.5</sub> polluters disproportionately and systemically affect people of color in the United States. Sci. Adv. 7.](https://doi.org/10.1126/sciadv.abf4491)
[^3]: [Goodkind AL, et al., (2019) Fine-scale damage estimates of particulate matter pollution reveal opportunities for location-specific mitigation of emissions. PNAS 116 (18).](https://doi.org/10.1073/pnas.1816102116)
[^4]: [Tessum CW, et al., (2019) Inequity in consumption of goods and services adds to racial-ethnic disparities in air pollution exposure. PNAS 116 (13).](https://doi.org/10.1073/pnas.1818859116)

[Just the Docs]: https://just-the-docs.github.io/just-the-docs/
[GitHub Pages]: https://docs.github.com/en/pages
[README]: https://github.com/just-the-docs/just-the-docs-template/blob/main/README.md
[Jekyll]: https://jekyllrb.com
[GitHub Pages / Actions workflow]: https://github.blog/changelog/2022-07-27-github-pages-custom-github-actions-workflows-beta/
[use this template]: https://github.com/just-the-docs/just-the-docs-template/generate
