NOTE: deprecated, functionality moved to: https://github.com/r-transit/tidytransit

You can still use this but its not under development for now. 

## Description

`transitfeedr` is an R package for easily searching and getting GTFS
feeds on [Transitfeeds](https://transitfeeds.com/).

## Installation

You can install this package from GitHub using the devtools package:

    if (!require(devtools)) {
        install.packages('devtools')
    }
    devtools::install_github('r-gtfs/transitfeedr')

## Example Usage

[![Travis-CI Build
Status](https://travis-ci.com/r-transit/transitfeedr.svg?branch=master)](https://travis-ci.com/r-transit/transitfeedr)
[![cran
version](https://www.r-pkg.org/badges/version/transitfeedr)](https://cran.r-project.org/package=transitfeedr)

``` r
library(dplyr)
library(transitfeedr)

# set the API key
# set_api_key() # uncomment to set api key

# get the feedlist dataframe and filter out NYC subway
feedlist_df <- get_feedlist() %>%
  filter(grepl('NYC Subway GTFS', t, ignore.case= TRUE))
```

Read the url with [trread](https://github.com/r-gtfs/trread)

``` r
library(trread)
# import NYC gtfs feed by sending the url to `import_gtfs`
NYC <- import_gtfs(feedlist_df$url_d)
#> [1] "agency.txt"         "calendar_dates.txt" "calendar.txt"      
#> [4] "routes.txt"         "shapes.txt"         "stop_times.txt"    
#> [7] "stops.txt"          "transfers.txt"      "trips.txt"
```
