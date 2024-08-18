---
title: "Software"
permalink: /software/
author_profile: true
---

With all of my research, I strive to provide publicly available codes that are reproducible, easily accessible, and well-documented.  All of the code for my work on deep Gaussian processes is housed in my public git repository on [Bitbucket](https://bitbucket.org/gramacylab/deepgp-ex/).  I also maintain the following R packages.

`deepgp`
------

The `deepgp` package is an R package for Bayesian deep Gaussian processes using Markov Chain Monte Carlo.  It is available on [CRAN](https://CRAN.R-project.org/package=deepgp).

The crux of the package is the use of elliptical slice sampling [(Murray et al., 2010)](http://proceedings.mlr.press/v9/murray10a/murray10a.pdf) for the latent Gaussian layers of the deep Gaussian process.  The package offers

* Fully-Bayesian inference for one-layer GPs, two-layer DGPs, and three-layer DGPs
	+ MCMC sampling, trimming burn-in, and thinning
	+ Posterior predictions with means and either point-wise variances or full predictive covariances (with `SNOW` parallelization)
	+ Squared exponential or Matern kernels
	+ Optional monotonic warpings
	+ S3 class objects with built-in plot options
* Vecchia approximation for faster computation with large data sizes (with `OpenMP` parallelization)
* Active learning/sequential design through various acquisition criteria
	+ Integrated mean squared error (IMSE) and active learning Cohn (ALC) for variance reduction
	+ Expected improvement for Bayesian optimization 
	+ Entropy for contour location 

To get started, install the package from CRAN,
```
install.packages("deepgp")
```
and check out the package vignette, available [here](https://cran.r-project.org/web/packages/deepgp/vignettes/deepgp.html).

`runexp`
------

The `runexp` package is an R package for estimating softball/baseball run expectancy using Markov Chains and Monte Carlo simulation. It is available on [CRAN](https://CRAN.R-project.org/package=runexp).  This package originated from my work as a Senior Analyst for the Virginia Tech Softball team for the 2019 and 2020 seasons.

The package implements both theoretical run expectancy using discrete Markov Chains and empirical run expectancy using Monte Carlo simulations.  The core functions are

* `scrape`: webscrapes player statistics from a url
* `prob_calc`: converts player statistics to at-bat outcome probabilities
* `chain`: runs the discrete Markov chain, returns S3 class object including run expectancies which can be used with `plot`
* `sim`: runs Monte Carlo simulation, returns S3 class object including simulated run outcomes

To get started, install the package from CRAN,
```
install.packages("runexp")
```
and check out the examples in the package documentation.  You may access the package's help files with the following commands.
```
library(runexp)
?scrape
?prob_calc
?chain
?sim
``` 