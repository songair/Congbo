---
layout: mypost
title: Meteorological data sources
categories: [Data]
comments: true
---

## Meteorological Data for HYSPLIT
* Gridded Meteorological Data archives: [https://www.ready.noaa.gov/archives.php](https://www.ready.noaa.gov/archives.php)
* Archived Model Graphics: [https://www.ready.noaa.gov/READYamet.php](https://www.ready.noaa.gov/READYamet.php)
* NOAA/ESRL Radiosonde Database: [https://ruc.noaa.gov/raobs/](https://ruc.noaa.gov/raobs/)
* FTP address: [ftp://arlftp.arlhq.noaa.gov/archives/](ftp://arlftp.arlhq.noaa.gov/archives/)

```R
# R codes
library (openair)
dataDir="xxx" ### Your working directory
setwd(dataDir)  ### Set the working directory
workingDirectory<<-dataDir  ### Shortcut for the working directory
getMet <- function (year = 2021:2022, month = 1:12, path_met = dataDir) {
  for (i in seq_along(year)) {
    for (j in seq_along(month)) {
      download.file(url = paste0("ftp://arlftp.arlhq.noaa.gov/archives/reanalysis/RP",
                                 year[i], sprintf("%02d", month[j]), ".gbl"),
                    destfile = paste0(path_met, "RP", year[i],
                                      sprintf("%02d", month[j]), ".gbl"), mode = "wb")}}}
getMet(year = 2022:2022, month = 1:12, path_met = dataDir) ### GET data for sepecific time
```

## Hourly/Sub-Hourly Observations Data
* GIS Platform: [https://www.ncei.noaa.gov/maps/hourly/](https://www.ncei.noaa.gov/maps/hourly/)
* FTP address: [ftp://ftp.ncdc.noaa.gov/pub/data/noaa/](ftp://ftp.ncdc.noaa.gov/pub/data/noaa/)



```R
# R codes
library(worldmet)
dataDir="xxx" ### Your working directory
setwd(dataDir)
info <- getMeta(lat = 40, lon = 116.9) ### Set the position of interest
dat <- importNOAA(code = "545110-99999", precip = TRUE,year = 2015:2019) ## Find the code of the meteorological station and datetime ranges
write.csv(dat,'BeijingMet.csv') ### Set filename
```

## ERA5 hourly data on single levels from 1959 to present
* Website: [https://cds.climate.copernicus.eu/cdsapp#!/dataset/reanalysis-era5-single-levels?tab=overview](https://cds.climate.copernicus.eu/cdsapp#!/dataset/reanalysis-era5-single-levels?tab=overview)
