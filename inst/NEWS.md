# MsQuality 1.7

## Changes in version 1.7.1
- rename ticQuartersRtFraction to ticQuantileRtFraction
- update tests after update of OBO file / rmzqc

# MsQuality 1.1

## Changes in version 1.1.3
- update tests after update of OBO file / rmzqc

## Changes in version 1.1.2
- Fix implementation of `mzAquisitionRange`
- add numberEmptyScans in qualityMetrics function
- add unit tests for export in rmzqc format
- add interpretation aid of metrics in vignette

## Changes in version 1.1.1
- move msdata from Suggests to Imports
- rename function rtDuration to chromatographyDuration
- rename function rtOverTicQuantiles to ticQuartersRtFraction
- create function numberEmptyScans
- add attributes (MS QC terms) to the output of the Spectra metrics functions 
  if the output matches the described term
- add rmzqc to IMPORTS
- add functionality to export quality metrics as in rmzqc format 
- adjust documentation to newest version of PSI MS CV obo file
- add to the vignette information on how the metrics are calculated
- add argument filterEmptySpectra to remove entries of length 0 or that
  have intensity 0, implement the argument in the functions
  calculateMetricsFromOneSampleSpectra, calculateMetricsFromSpectra,
  calculateMetricsFromMsExperiment, and calculateMetrics

# MsQuality 0.99

## Changes in version 0.99.9 (2023-04-18)
- enable parallel processing in calculateMetricsFromSpectra
- rename ticQuantileToQuantileLogRatio to ticQuartileToQuartileLogRatio
- rename rtOverTicQuantile to rtOverTicQuantiles
- return quartiles instead of quantiles in precursorIntensityQuartiles
- add mzR to Suggests in DESCRIPTION

## Changes in version 0.99.8 (2023-09-02)
- adjust behaviour of metrics function when Spectra object of 
  length 0 is presented, return NA values instead of raising an
  error

## Changes in version 0.99.7 (2023-06-02)
- adjust ticQuantileToQuantileLogRatio that it adheres to
  Quameter calculation

## Changes in version 0.99.6 (2022-11-29):
- extend section Description in `DESCRIPTION`
- add sections BugReports and URL in `DESCRIPTION`
- update dependency to `R` version 4.2.0
- transfer source code in R/Lee2019-data.R to 
  inst/sources/Lee2019-data-source.R
- use partial_bundle to reduce the file size of plotly graphics

## Changes in version 0.99.5 (2022-10-12):
- add section on alternative software in vignette
- simplify the vignette with regard to dealing with the RPLC and HILIC
  example data set and adjust the Lee2019-data.R accordingly to keep 
  the RPLC/HILIC information in the dataOrigin slot of the Spectra object

## Changes in version 0.99.4 (2022-10-11):
- add missing comma in `DESCRIPTION`

## Changes in version 0.99.3 (2022-10-11):
- delete Maintainer field in `DESCRIPTION`
- add instructions to install `MsQuality` in vignette and `README.md` via
  `remotes`/`BiocManager` instead of `devtools`

## Changes in version 0.99.2 (2022-09-20):
- create branch `msexperiment` to store infrastructure and functions for
  `MsExperiment` objects
- remove `MsExperiment` objects since this is still in BioC review and solely
  rely on `Spectra` objects
- adjust documentation for the implemented changes (removal of `MsExperiment`)  
  
## Changes in version 0.99.1 (2021-11-23)
- simplify `calculateMetricsFromSpectra`:
  - the function does not any longer match the arguments by the formal 
    arguments of the metric functions
  - the function does not any longer combine the parameters
  - the additional arguments do not take longer the parameter list of 
    arguments but comma-separated arguments given to `...`
  - for all metric functions the `...` parameter is added
  - adjust the vignette and help pages  
- rename functions to camel case

## Changes in version 0.99.0 (2021-09-10)
- add quality metrics/functions (metrics based on HUPO-mzQC):
  - `rtDuration` (QC:4000053),
  - `rtOverTICquantile` (QC:4000054),
  - `rtOverMsQuarters` (rtOverMSQuarters),
  - `ticQuantileToQuantileLogRatio` (QC:4000057, QC:4000058),
  - `numberSpectra` (QC:4000059, QC:4000060),
  - `medianPrecursorMz` (QC:4000065),
  - `rtIQR` (QC:4000072),
  - `rtIQRrate` (QC:4000073),
  - `areaUnderTIC` (QC:4000077),
  - `areaUnderTICRTquantiles` (QC:4000078),
  - `extentIdentifiedPrecursorIntensity` (QC:4000125),
  - `medianTICRTIQR` (QC:4000130),
  - `medianTICofRTRange` (QC:4000132),
  - `mzAcquisitionRange` (QC:4000138),
  - `rtAcquisitionRange` (QC:4000139),
  - `precursorIntensityRange` (QC:4000144),
  - `precursorIntensityQuartiles` ((QC:4000167, QC:4000228, QC:4000233),
  - `precursorIntensityMean` (QC:4000168, QC:4000229, QC:4000234),
  - `precursorIntensitySD` (QC:4000169, QC:4000230, QC:4000235),
  - `msSignal10XChange` (QC:4000172, QC:4000173),
  - `ratioCharge1over2` (QC:4000174, QC:4000179),
  - `ratioCharge3over2` (QC:4000175, QC:4000180),
  - `ratioCharge4over2` (QC:4000176, QC:4000181),
  - `meanCharge` (QC:4000177, QC:4000182),
  - `medianCharge` (QC:4000178, QC:4000183)
  - `.rt_order_spectra` (helper function)
- add the functions `calculateMetricsFromSpectra`, 
  `calculateMetricsFromMsExperiment` to calculate the metrics based on 
  `Spectra` and `MsExperiment` objects
- add functions `plotMetric`, `plotMetric_tibble` to visualize the metrics
- add shiny application `shinyMsQuality` to interactively visualize the metrics
