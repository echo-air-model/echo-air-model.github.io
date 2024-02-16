---
layout: default
title: Source Releases in the "Hole"
parent: Other Information
nav_exclude: true
---

## Patching the "Hole" in the California ISRM
The following page details the short-term solution to the current missing release height layer in the California ISRM. The future California ISRM that is in development will be trained on each release height and this patch will be removed.

### Background
When the California ISRM was developed for the California Air Resources Board Contract 17RD006[^1], three release elevations were created:
* (<b>L0</b>) Ground level and low stack: below 57 m
* (<b>L1</b>) Medium and high stack: 57-140 m
* (<b>L2</b>) High elevation plumes: above 760 m

This results in a lack of estimates for emissions that occur between 140 and 760 meters, or the "hole". 

The US ISRM used for most of the published literature does not have this issue, so there is no peer-reviewed approach for solving this problem. <b>As we develop the California ISRM, we can decide to avoid having this problem in the future, so this is a temporary (but important) problem.</b>

What emissions sources even fall into this release height range?
* Airplane take-off and landing
* Rooftop building sources (e.g., rooftop generators)
* Some tall stacks

### Temporary Solution
As noted above, the long-term solution for this issue is ensuring that the new ISRM for California includes reasonable layers for all near-surface release heights. Until then, ECHO-AIR takes the following approach.

In order to avoid overprescribing precision between 140 and 760 meters and slowing down ECHO-AIR's processing, ECHO-AIR will do the following:
1. Identify emissions that fall between L1 and L2.
2. Notify the user about potential imprecision for sources that are released in this range.
3. Perform a simple average of L1 and L2 to reasonably approximate ground-level concentrations from these source releases.

### Brief Case Study and Justification for Solution
As a final note on this page, we performed a simple test of four potential solutions to the hole patching using California's Cap-and-Trade facility 2012 emissions.  

----

### References
[^1]: [Apte JS, Chambliss SE, Tessum CW, Marshall JD (2019) A Method to Prioritize Sources for Reducing High PM<sub>2.5</sub> Exposures in Environmental Justice Communities in California. CARB Report.](https://ww2.arb.ca.gov/sites/default/files/classic/research/apr/past/17rd006.pdf)
...
