---
title: "Research"
permalink: /research/
author_profile: true
---

My research focuses on the design and analysis of computer experiments.  Computer 
simulations are increasingly relevant to many scientific fields, where they are used
to replace or supplement physical experimentation that might be infeasible (due to
practicality, cost, or ethical constraints).  Engineers and scientists
devote a LOT of work to developing useful and realistic computer simulations, but the
complexity of these simulations can make it difficult to use them to answer specific
research questions.  That's where we come in.  My work is united by one common question:
**how can we leverage complex computer simulation experiments to answer specific research questions?**
This work usually falls into three realms:

1. Developing better "surrogate" models.  Surrogates are statistical models that are trained
on limited evaluations of the computer simulation in order to provide predictions (with uncertainty
quantification) for unobserved inputs.  They are essential when it is not possible to
exhaustively evaluate all possible configurations of the computer experiment.  "Better" surrogates
can provide more accurate predictions with more effective uncertainty quantification from the
same training data.  Or they may provide just as accurate predictions but with less computational
overhead.

2. Developing better experimental designs.  When we can only evaluate the computer simulation so
many times, we need to be very strategic with the inputs we choose to run.  The "experimental
design" should be tailored to the research question we want to answer.  Design of computer
experiments often involves "active learning" or "sequential design" where surrogates are used
to decide which inputs to run next in an iterative feedback loop.

3. Developing better ways to use surrogates.  This may involve calibrating the surrogate to
physical experimental data, using the surrogate to estimate the probability of system failure
under uncertain inputs, etc. (depending on the research question we want to answer).

I have done a lot of work developing deep Gaussian processes as surrogates for nonstationary
computer experiments (which I classify under realm \#1 above).  I maintain the 
[deepgp](https://cran.r-project.org/package=deepgp) package on CRAN.

Some of the **application areas** I've worked on:

* Digital twins
* Aerospace engineering
* Quantum mechanics
* Cosmology

I am very grateful for financial support from:

* the National Science Foundation
* Lawrence Livermore National Laboratory
* Virginia Tech and NC State

Check out my [CV](/files/BoothCV.pdf) or the [Publications](../publications/) page for more information including references to my papers.

Students
------

Virginia Tech:

* [Courtney Kyger](https://www.linkedin.com/in/courtney-kyger-30226a1b1/), 2025 - Present
* [Jason Kost](https://www.linkedin.com/in/jason-kost-587299224/), 2026 - Present
* Yusi Yao (undergraduate researcher), 2026
  + Now pursuing a Ph.D. in Civil and Systems Engineering at Johns Hopkins University

NC State:

* Ayumi Mutoh, 2024 - 2025, co-advised with Jon Stallrich
* [Shih-Ni Prim](https://snprim.github.io/), 2024 - 2025, co-advised with Brian Reich
  + Now a post-doc at Wake Forest University
