
<!-- README.md is generated from README.Rmd. Please edit that file -->

# FunBootBand

<!-- badges: start -->
<!-- badges: end -->

Compute statistical bands from curve data using a functional approach
and bootstrapping.

At the core, this is an implementation of the method developed by
Sutherland et al. (1988) and Olshen et al. (1989), described in detail
in Lenhoff et al. (1999). The method was originally written as a MATLAB
program by Doris Oriwol and later translated into R and extended with an
approach to handle hierarchical data (see also
<https://github.com/koda86/floa>).

<!-- Bugfix bei der Berechnung -->

More details can be found in this publication (and the vignette):

Koska, D., Oriwol, D., & Maiwald, C. (2023). Comparison of statistical
models for characterizing continuous differences between two
biomechanical measurement systems. Journal of Biomechanics, J. Biomech.
149, <https://doi.org/10.1016/j.jbiomech.2023.111506>.

## Citation

IMHO, the following statement makes a great point:

“Every great open source math library is built on the ashes of someone’s
academic career” – <https://njt-rse-unsw.netlify.app/#24>

So, if you use the package, please consider citing the package via

``` r
citation("FunBootBand")
#> To cite package 'FunBootBand' in publications use:
#> 
#>   Koska D (????). _FunBootBand: Creates Functional Bootstraped
#>   (statistical) Bands_. R package version 0.1.0.
#> 
#> A BibTeX entry for LaTeX users is
#> 
#>   @Manual{,
#>     title = {FunBootBand: Creates Functional Bootstraped (statistical) Bands},
#>     author = {Daniel Koska},
#>     note = {R package version 0.1.0},
#>   }
#> 
#> ATTENTION: This citation information has been auto-generated from the
#> package DESCRIPTION file and may need manual editing, see
#> 'help("citation")'.
```

## Issues and contributing

In case you find a bug or run into other problems, please look for the
“Issues” tab. Feedback of any kind is welcome.

## Installation

You can install the development version of FunBootBand from
[GitHub](https://github.com/koda86/FunBootBand) with:

``` r
# install.packages("devtools")
devtools::install_github("koda86/FunBootBand")
```

## Example

Here’s how to use the

This is a basic example which shows you how to solve a common problem:

``` r
library(FunBootBand)

prediction.band <- band(data, type = "prediction", B = 5, alpha = 0.05, iid = TRUE)

# Function output:
rownames(prediction.band)
#> [1] "upper" "mean"  "lower"
str(prediction.band)
#>  num [1:3, 1:101] 0.781 0.135 -0.511 0.825 0.179 ...
#>  - attr(*, "dimnames")=List of 2
#>   ..$ : chr [1:3] "upper" "mean" "lower"
#>   ..$ : NULL

plot(data[, 1], type = "l", ylim = c(-3, 3), ylab = "Amplitude")
apply(data, 2, function(x) lines(x))
#> NULL
apply(prediction.band, 1, function(x) lines(x, col = "red", lwd = 4))
```

<img src="man/figures/README-example-1.png" width="100%" />

    #> NULL

<!-- What is special about using `README.Rmd` instead of just `README.md`? You can include R chunks like so: -->
<!-- ```{r cars} -->
<!-- summary(cars) -->
<!-- ``` -->
<!-- You'll still need to render `README.Rmd` regularly, to keep `README.md` up-to-date. `devtools::build_readme()` is handy for this. You could also use GitHub Actions to re-render `README.Rmd` every time you push. An example workflow can be found here: <https://github.com/r-lib/actions/tree/v1/examples>. -->
<!-- You can also embed plots, for example: -->
<!-- ```{r pressure, echo = FALSE} -->
<!-- plot(pressure) -->
<!-- ``` -->
<!-- In that case, don't forget to commit and push the resulting figure files, so they display on GitHub and CRAN. -->

## Licence

LGPL (\>= 3)

## References

-   Lenhoff, M.W., Santner, T.J., Otis, J.C., Peterson, M.G., Williams,
    B.J., Backus, S.I., 1999. Bootstrap prediction and confidence bands:
    a superior statistical method for analysis of gait data. Gait
    Posture 9 (1), 10–17. <http://dx.doi.org/10.1016/s0966->
    6362(98)00043-5.

-   Olshen, R.A., Biden, E.N., Wyatt, M.P., Sutherland, D.H., 1989. Gait
    analysis and the bootstrap. Ann. Statist. 17 (4),
    <http://dx.doi.org/10.1214/aos/1176347372>.

-   Sutherland, D., Olshen, R., Biden, E., Wyatt, M., 1988. Development
    of Mature Walking. Mac Keith Press.
