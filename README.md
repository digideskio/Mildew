R-Mildew
========

Setup
-----
First install [R-INLA](http://www.r-inla.org/) testing version, which you can install with the command
```r
source("http://www.math.ntnu.no/inla/givemeINLA-testing.R")
```
Then run Mildew setup script with the command
```r
source("https://raw.github.com/statguy/R-Mildew/master/process/setup.R")
```    

Code files
----------
In the Mildew package installation directory (which is shown by the command `path.package("Mildew")`), you find
the following files to preprocess, estimate and report results for the mildew data:
* `preprocess.R`
contains high-level code to preprocess the data so that it is useful for the analysis.
* `estimate.R`
contains high-level code to estimate all models.
* `reports.R`
contains high-level code to load all results and print reports.

Configuration
-------------
Set `basePath` in `preprocess.R`, `estimate.R` and `reports.R` to point to your mildew data directory.
If you experience problems with parallel processing, set
```r
runParallel <- FALSE
```
`preprocess.R` uses Ukko remote cluster for imputation. If you cannot access it, remove the cluster setup code.
If you can use some other remote cluster, take a look at [R-Cluster](https://github.com/statguy/R-Cluster).

Estimation
----------
With the current configuration, estimation may take up to 1 day per model in a powerful system.
You may want to construct a mesh with less nodes by adjusting the mesh parameters
`occ.mesh.params`, `col.mesh.params`, `ext.mesh.params` in `estimate.R` or use
a subset of the data for testing. Use the `plotMesh` method, e.g.
```r
occ$plotMesh()
```
to plot the mesh.

Extensions
----------
Extending the current code can be done by inheriting the classes defined in
`https://raw.github.com/statguy/R-Mildew/master/R/classes.R`, which contains low-level code to
load the mildew data, set up models, estimate models with INLA, save results and print results.
See more info about the references classes with the R command
```r
?ReferenceClasses
```
You may want to consider [forking](https://help.github.com/articles/fork-a-repo) the repository for your own use first.

TODO
----
* Plotting

Bugs
----
Send bug reports to [`jvj@iki.fi`](mailto:jvj@iki.fi).
