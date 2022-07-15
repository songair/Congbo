---
layout: mypost
title: Get meteorological data from NOAA
categories: [R]
comments: true
---


```R
library (openair)
dataDir="D:\\Hysplit\\TrajData"

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
