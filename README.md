# dwd-grib-helper
`dwd-grib-helper` is a tiny helper package to extract timeseries data from grib files that have been downloaded by the `dwd_data_crawler` service.

## Installation
```
$ npm install dwd-grib-helper
```

## Usage
The `dwd-grib-helper` package exposes two functions


### extractTimeseriesDataFromGrib2Directory
* purpose: extract a timeseries from a given directory
* arguments:
  1. (`String`): path to the directory holding the .grib2.lz4 files (lz4 compressed grib2 files) of a single foreacast run for a single 
  2. (`Object`): location in terms of latitude and longitude of the point of interest (will automatically be rounded to grid accuracy)
* returns (`Object`):
  * `location`: the location in terms of latitude and longitude of the actual location on the grid, stored in the grib2 files, that has been used to exract the timeseries data.
  * `timeseriesData`: the actual timeseries data (in terms of raw data) as Array of `Object`. Each `Object` in the Array has two attributes:
    * `timestamp` (`Number`): the timestamp of as UNIX EPOCH in ms resolution
    * `value` (`Number`): the value (invalid values are encoded as null)

### deriveGrib2DirectoryPath
* purpose: derive the path to a specific directory holding .grib2.lz4 files (lz4 compressed grib2 files)
* arguments:
  * 1. 