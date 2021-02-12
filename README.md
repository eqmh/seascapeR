
<!-- README.md is generated from README.Rmd. Please edit that file -->

<!-- README.md is generated from README.Rmd. Please edit that file -->

# seascapeR <a href='https://marinebon.org/seascapeR'><img src='man/figures/logo.svg' align="right" height="150" /></a>

[![pkgdown](https://github.com/marinebon/seascapeR/workflows/pkgdown/badge.svg)](https://github.com/marinebon/seascapeR/actions?query=workflow%3Apkgdown)

<!--
[![R build status](https://github.com/mitchelloharawild/icon/workflows/R-CMD-check/badge.svg)](https://github.com/mitchelloharawild/icon/actions?workflow=R-CMD-check)
[![Coverage status](https://codecov.io/gh/mitchelloharawild/icon/branch/master/graph/badge.svg)](https://codecov.io/gh/mitchelloharawild/icon?branch=master)
[![lifecycle](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://www.tidyverse.org/lifecycle/#experimental)
[![CRAN_Status_Badge](http://www.r-pkg.org/badges/version/icon)](https://cran.r-project.org/package=icon)
-->

<!-- [![Downloads](http://cranlogs.r-pkg.org/badges/icon?color=brightgreen)](https://cran.r-project.org/package=icon) -->

The `seascapeR` package provides functions for fetching, analyzing and
visualizing
[Seascapes](https://coastwatch.noaa.gov/cw/satellite-data-products/multi-parameter-models/seascape-pelagic-habitat-classification.html),
a global and regional sea water classification product derived from
satellite imagery by [Maria Kavanaugh
(OSU)](https://ceoas.oregonstate.edu/people/maria-kavanaugh) and
[MarineBON.org](https://marinebon.org).

## Install

``` r
remotes::install_github("marinebon/seascapeR")
```

## Use

Load the library and map Seascape classes using a web map server (wms)
that loads image tiles (not data) interactively (zoom, pan) from R.

``` r
library(seascapeR)

map_seascape_wms("2020-11-15", ctr_lon = -81.3, ctr_lat = 24.5, ctr_dd = 10)
```

![](man/figures/README-map_seascape_wms-1.png)<!-- -->

Get Seascape data for a year and plot Seascape classes over time.

``` r
r_mo_2019 <- get_seascape_data(
  ctr_lon = -81.3, ctr_lat = 24.5, ctr_dd = 10, 
  dataset = "global_monthly", var = "CLASS", 
  date_beg = "2019-01-01", date_end = "2020-01-01")
#> info() output passed to x; setting base url to: https://cwcgom.aoml.noaa.gov/erddap/

plot_seascape_ts(r_mo_2019, show_legend = "always")
```

![](man/figures/README-plot_seascape_ts-1.png)<!-- -->

Note that when you run the code above in
[RStudio](https://rstudio.com/products/rstudio/download/), knit from
within [Rmarkdown](https://rmarkdown.rstudio.com/) to html, or use in a
[Shiny](https://shiny.rstudio.com/) app, an interactive map displays
allowing you to zoom and pan and the time series can zoom in time and
hover over values.

For more on how to use the `seascapeR` functions and view out these
interactive visualizations, see the [Getting
Started](articles/seascapeR.html) article.

For more on how to contribute to `seascapeR` package development, see
[CONTRIBUTE.md](https://github.com/marinebon/seascapeR/blob/main/CONTRIBUTE.md).
