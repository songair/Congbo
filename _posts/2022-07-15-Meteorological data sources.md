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
workingDirectory<-dataDir  ### Shortcut for the working directory
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
dat <- importNOAA(code = "545110-99999", year = 2015:2019) ## Find the code of the meteorological station and datetime ranges
write.csv(dat,'BeijingMet.csv') ### Set filename
```

## ERA5 hourly data on single levels from 1959 to present
* Website: [https://cds.climate.copernicus.eu/cdsapp#!/dataset/reanalysis-era5-single-levels?tab=overview](https://cds.climate.copernicus.eu/cdsapp#!/dataset/reanalysis-era5-single-levels?tab=overview)
* Useful link:
** [https://cran.r-project.org/web/packages/ecmwfr/](https://cran.r-project.org/web/packages/ecmwfr/)
** https://cran.r-project.org/web/packages/ecmwfr/vignettes/cds_vignette.html


```python
# python codes
import netCDF4 as nc
from netCDF4 import Dataset
import pandas as pd
import numpy as np
import os
dataDir="xxx" ### specify working Directory
xn="ERA5_renalysis.nc" ### specify filename of the .nc file
os.chdir(dataDir)
```

```python
# python codes
f=Dataset(xn)
for i in f.variables.keys():
    print(i)
```

```python
# python codes
def closest(lst, K):  
     lst = np.asarray(lst)
     idx = (np.abs(lst - K)).argmin()
     return lst[idx]
```

```python
# python codes
av=closest(list(f.variables['latitude'][:]),51.15) ###latitude is 51.15
bv=closest(list(f.variables['longitude'][:]),-1.44) ###longitude is -1.44
a=list(f.variables['latitude'][:]).index(av)
b=list(f.variables['longitude'][:]).index(bv)
```

```python
# python codes
timezone=0
dtime = netCDF4.num2date(f.variables['time'][:],f.variables['time'].units,calendar=f.variables['time'].calendar)
nptimes = dtime.astype('datetime64[ns]')
atm=pd.DataFrame(index=np.array(dtime),
                 data={'ssr':f.variables['ssr'][:,:,a,b][~f.variables['ssr'][:,:,a,b].mask],
                              'tp':f.variables['tp'][:,:,a,b][~f.variables['tp'][:,:,a,b].mask]})
atm['blh']=np.nan
atm['tcc']=np.nan
atm['sp']=np.nan
atm['blh'].iloc[:-2]=f.variables['blh'][:,:,a,b][~f.variables['blh'][:,:,a,b].mask] ## Check number of NAN values for the last records [:-2]
atm['tcc'].iloc[:-2]=f.variables['tcc'][:,:,a,b][~f.variables['tcc'][:,:,a,b].mask]
atm['sp'].iloc[:-2]=f.variables['sp'][:,:,a,b][~f.variables['sp'][:,:,a,b].mask]
atm.index.name='date'
atm.index=atm.index.astype('datetime64[ns]')
atm=atm.sort_index()
atm.to_csv("NETCDF_data.csv")
```
The data can be four dimension: f.variables['blh'][:,:,a,b] or three dimension: f.variables['blh'][:,a,b]

## Useful links
* [https://github.com/sonnymetvn/Basic-Python-for-Meteorology/tree/main/notebook](https://github.com/sonnymetvn/Basic-Python-for-Meteorology/tree/main/notebook)
* [https://cran.r-project.org/web/packages/ecmwfr/](https://cran.r-project.org/web/packages/ecmwfr/)
* [https://cran.r-project.org/web/packages/ecmwfr/vignettes/cds_vignette.html](https://cran.r-project.org/web/packages/ecmwfr/vignettes/cds_vignette.html)
