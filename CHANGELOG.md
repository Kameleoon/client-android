# Changelog
All notable changes to this project will be documented in this file.

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
