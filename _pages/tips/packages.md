---
title: 'Installing R Packages from Source'
date: 2025-07-25
permalink: /tips/packages/
author_profile: true
---

CRAN is an amazing resource, but sometimes you will have to work with R packages outside of it.  For instance,

* When you are developing your own package
* When you are using someone else's package that is provided online (such as in a git repository) but not on CRAN
* If you are given access to a "beta" version of a package that is under development but not pushed to CRAN yet
* If you have a Mac and want to use an R package with `OpenMP` functionality, you will have to download the source files and install it yourself using `gcc/g++` (and a`Makevars` file) instead of the default `clang` compiler.

There are different ways to build/install R packages (the `devtools` package has some functionality for this), but here is my "go-to" approach.

Build the package
------

If you are starting from a package that has not been built yet (like one in a git repository):

1. Clone the repo or otherwise download the source files.

2. In the terminal, navigate to the folder that holds the package folder.  The package folder's name should match the name of the R package.  Do NOT navigate inside the package.  Stay one level outside of it.

3. Run the following command to build the package, replacing `pkg_name` with the name of the folder/package.

```
R CMD build pkg_name
```

You can provide additional flags to this command.  If a package has a lengthy vignette, I typically skip the rendering of it using `R CMD build --no-build-vignettes pkg_name`.  If the build has worked properly, then you will now have a file called `pkg_name_0.0.0.tar.gz` (where `0.0.0` is replaced with the package's version number).

If you are downloading a package from CRAN, you can download the `tar.gz` file directly without having to build it yourself.  CRAN offers this option for all packages, under the "Package Source" label.

Install the package
------

Simply run

```
R CMD INSTALL pkg_name_0.0.0.tar.gz
```

Then you can open R and check that the `library` command of your package works successfully.  If you are actively working on a package, remember to re-build it and re-install it as you make updates.
