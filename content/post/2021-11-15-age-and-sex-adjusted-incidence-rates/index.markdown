---
title: Age- and sex adjusted incidence rates
author: admin
date: '2021-11-15'
slug: age-and-sex-adjusted-incidence-rates
categories: 
  - 
tags: 
  - incidence-rate
  - poisson-regression
  - survival-analysis
  - tips-n-tricks
subtitle: "Age- and sex-adjusted incidence rates with poisson regression in R"
summary: "In this first post I'm going to present a way of obtaining age- and sex-adjusted incidence rates using poisson regression in R. This will be similar to what is done in stata as described [here](https://www.statalist.org/forums/forum/general-stata-discussion/general/1431921-age-adjusted-rates-using-a-poisson-regression)"
authors: 
  - admin
lastmod: '2021-11-15T10:40:31+01:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---
In this first post I'm going to present a way of obtaining age- and sex-adjusted incidence rates using poisson regression in R. This will be similar to what is done in Stata as described [here](https://www.statalist.org/forums/forum/general-stata-discussion/general/1431921-age-adjusted-rates-using-a-poisson-regression)

I've written a R function that's available for download [here.](age_sex_adjust.R) The scipt can be sourced ( `source("age-sex-adjust.R"` ) and then the function `age_sex_adjust()` can be used as is. The code will also be described step by step below.

***

There are, as usual, several ways to calculate adjusted incidence rates in R. I've chosen to use the package [stdReg](https://cran.r-project.org/package=stdReg) by Arvid Sjölander (lägg till länk) because it has a lot of nice features and useful implications in causal inference. Specifically, we will use the function `stdGlm()` from stdReg to generate the the adjusted incidence rates. 


But first we start off with a little bit of background on what an incidence rate it. It is simply a measure of a number of occurrences in a population over the total population time. For example, in a population of 10 people, each followed 1 year, there was one case of death. In that population, the incidence rate of death would 1 per 10 person years. In observational data, we often have larger cohorts with varying follow-up time and censoring. `\(\nabla F\)`






