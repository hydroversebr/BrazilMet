![CRAN Total Downloads](https://cranlogs.r-pkg.org/badges/grand-total/BrazilMet)
![CRAN Download Badge](https://cranlogs.r-pkg.org/badges/BrazilMet)

# BrazilMet

<div class="fluid-row" id="header">
    <img src='man/figures/logo_BrazilMet.png' height='150' width='auto' align='right'>


<!-- badges: start -->
[![R-CMD-check](https://github.com/FilgueirasR/BrazilMet/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/FilgueirasR/BrazilMet/actions/workflows/R-CMD-check.yaml)
<!-- badges: end -->

The BrazilMet package aims to facilitate the acquisition and processing of meteorological data from INMET automatic stations.


## Installation

To install the last version of BrazilMet package follow this steps:

``` r
devtools::install_github("FilgueirasR/BrazilMet")

```

## Example

This is a basic example which shows you how to run the cropDemand package:

``` r
## basic example code

#devtools::install_github("FilgueirasR/BrazilMet")
library(BrazilMet)

see_stations_info()

df<-download_AWS_INMET_daily(stations = c("A001", "A042"), start_date = "2023-01-01", end_date = "2024-12-31")

df$eto <- daily_eto_FAO56(lat = df$latitude_degrees,
                          tmin = df$tair_min_c,
                          tmax = df$tair_max_c,
                          tmean = df$tair_mean_c,
                          Rs = df$sr_mj_m2,
                          u2 = df$ws_2_m_s,
                          Patm = df$patm_mb,
                          RH_max = df$rh_max_porc,
                          RH_min = df$rh_min_porc,
                          z = df$altitude_m,
                          date = df$date)

```
