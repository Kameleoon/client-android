# Changelog
All notable changes to this project will be documented in this file.

## 3.0.0 - 2023-02-17
* Added support of new feature flag rules:
    - [`getFeatureVariationKey`](https://developers.kameleoon.com/java-sdk.html#getFeatureVariationKey)
    - `obtainFeatureVariable` -> [`getFeatureVariable`](https://developers.kameleoon.com/java-sdk.html#getFeatureVariable)
    - [`getFeatureAllVariables`](https://developers.kameleoon.com/java-sdk.html#getFeatureAllVariables)
    - `activateFeature` -> [`isFeatureActive`](https://developers.kameleoon.com/java-sdk.html#isFeatureActive)
* Renaming of methods (old methods warn you on using and will be removed later)
    - `obtainVisitorCode` -> [`getVisitorCode`](https://developers.kameleoon.com/java-sdk.html#getVisitorCode)
    - `obtainVariationAssociatedData` -> [`getVariationAssociatedData`](https://developers.kameleoon.com/java-sdk.html#getVariationAssociatedData),
    - `obtainFeatureAllVariables` -> [`getFeatureAllVariables`](https://developers.kameleoon.com/java-sdk.html#getFeatureAllVariables),
    - `obtainExperimentList` -> [`getExperimentList`](https://developers.kameleoon.com/java-sdk.html#getExperimentList)
    - `obtainExperimentListForVisitorCode` -> [`getExperimentListForVisitorCode`](https://developers.kameleoon.com/java-sdk.html#getExperimentListForVisitorCode)
    - `obtainFeatureList` -> [`getFeatureList`](https://developers.kameleoon.com/java-sdk.html#getFeatureList)
    - `obtainFeatureListListForVisitorCode` -> [`getActiveFeatureListForVisitorCode`](https://developers.kameleoon.com/java-sdk.html#getActiveFeatureListForVisitorCode)
* Renaming of exceptions:
    - `NotActivated` -> `NotAllocated`
* Changes in Kameleoon Data:
    - Added possibility to set [`UserAgent`](https://developers.kameleoon.com/java-sdk.html#useragent).
* Added **KameleoonConfiguration**, it can be used as parameter during initialization of a client. Related to [`KameleoonClientFactory.create`](https://developers.kameleoon.com/java-sdk.html#com-kameleoon-kameleoonclientfactory)

## 2.1.1 - 2022-08-24
* Added method to obtain all variables for feature flag: [`obtainFeatureAllVariables`](https://developers.kameleoon.com/android-sdk.html#obtainfeatureallvariables)
* Added method to obtain a list of feature flags: [`obtainFeatureList`](https://developers.kameleoon.com/android-sdk.html#obtainfeaturelist)
* Added method to obtain a list of feature flags targeted for specified visitor code: [`obtainFeatureListForVisitorCode`](https://developers.kameleoon.com/android-sdk.html#obtainfeaturelistforvisitorcode)
* Added method to obtain a list of experiments: [`obtainExperimentList`](https://developers.kameleoon.com/android-sdk.html#obtainexperimentlist)
* Added method to obtain a list of experiments targeted for specified visitor code: [`obtainExperimentListForVisitorCode`](https://developers.kameleoon.com/android-sdk.html#obtainexperimentlistforvisitorcode)
* Added support for **Experiment** & **Exclusive Campaign** conditions. Related to [`triggerExperiment`](https://developers.kameleoon.com/android-sdk.html#triggerexperiment)
* Added KameleoonData [`Device`](https://developers.kameleoon.com/android-sdk.html#device) data. Possible values are: **PHONE**, **TABLET**, **DESKTOP**.
* Removed KameleoonData `Interest`
* Added support of `is among the values` operator for Custom Data

## 2.1.0 - 2022-05-13
* Added a new method [`updateConfigurationHandler`](https://developers.kameleoon.com/android-sdk.html#updateconfigurationhandler) to handle events when configuration has updated data in real time.
* Added update campaigns and feature flag configurations instantaneously with Real-Time Streaming Architecture: [`documentation`](https://developers.kameleoon.com/android-sdk.html#streaming) or [`product updates`](https://www.kameleoon.com/en/blog/real-time-streaming)

## 2.0.13 - 2022-04-12
* Added method for retrieving data from remote source: [`retrieveDataFromRemoteSource`](https://developers.kameleoon.com/android-sdk.html#retrievedatafromremotesource)

## 2.0.12 - 2022-02-10
* Added support of multi-environment for feature flags, Related to [`activateFeature`](https://developers.kameleoon.com/android-sdk.html#activatefeature), [`obtainFeatureVariable`](https://developers.kameleoon.com/android-sdk.html#obtainfeaturevariable)
* Added checking for status of site_code (Enable / Disable). Related to [`activateFeature`](https://developers.kameleoon.com/android-sdk.html#activatefeature), [`triggerExperiment`](https://developers.kameleoon.com/android-sdk.html#triggerexperiment)

## 2.0.11 - 2021-12-15
* Fixed crash when calling `emptyTargetingData`
* Fixed issue with overlapping periods for scheduling. Related to [`activateFeature`](https://developers.kameleoon.com/android-sdk.html#activatefeature)

## 2.0.10 - 2021-10-25
* Added scheduling functionality for [`activateFeature`](https://developers.kameleoon.com/android-sdk.html#activatefeature)
* Fixed wrong bucketing on respool time. Related to [`activateFeature`](https://developers.kameleoon.com/android-sdk.html#activatefeature) and [`triggerExperiment`](https://developers.kameleoon.com/swift-sdk.html#triggerexperiment)  

## 2.0.9
* obtainFeatureVariable support JSONArray as returning value
* Adding URI encoding PageView

## 2.0.8
* Migrate tests to sdk@kameleoon.com account
* Migrate exception packages

## 2.0.7
* Added dependencies for Maven Central Repo

## 2.0.6
* Improving SDK stability
* Added VisitorCodeNotValid exception when empty or exceeding the limit of 255 chars

## 2.0.5
* Fix runWhenReady issue
