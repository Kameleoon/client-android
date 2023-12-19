# Changelog
All notable changes to this project will be documented in this file.

## 3.4.0 - 2023-12-19
### Features
* Added a new configuration parameter to [`KameleoonConfiguration`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#initialize-the-kameleoon-client) and the [configuration](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#configure-additional-properties) file:
    - `defaultTimeout` in `KameleoonConfiguration` and `default_timeout_millisecond` in the configuration file: designates the predefined timeout for network requests. The default timeout value is 10000 milliseconds.

## 3.3.0 - 2023-10-19
### Features
* Added [`getVisitorWarehouseAudience`](https://developers.kameleoon.com/android-sdk.html#getvisitorwarehouseaudience) method to retrieve all data associated with a visitor's warehouse audiences and adds it to the visitor.

## 3.2.1 - 2023-08-29
### Features
* Changed the `KameleoonClientConfig` parameters `clientId` and `clientSecret` and the external configuration file parameters, `client_id` and `client_secret` from required to optional. This means you can now successfully initialize a configuration without providing credentials. Previously, you would receive a `CredentialsNotFound` exception.

## 3.2.0 - 2023-08-21
### Features
* Added [`getRemoteVisitorData`](https://developers.kameleoon.com/android-sdk.html#getRemoteVisitorData) method to synchronize visitor data across devices by fetching remote data for a visitor (and optionally, add the fetched data to the visitor.)
### Bug Fixes
* Stability and performance improvements.

## 3.1.3 - 2023-07-11
* Added new conditions for targeting:
    - Visitor Code
    - SDK Language
    - [Device](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/go-sdk/#device)
    - [Conversion](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/go-sdk/#trackconversion)

## 3.1.2 - 2023-07-04
* Improved the handling of internet connection loss for the [Real-Time Streaming Architecture](https://developers.kameleoon.com/feature-management-and-experimentation/technical-considerations/#streaming): We have resolved a critical issue related to the [Real-Time Streaming Architecture](https://developers.kameleoon.com/feature-management-and-experimentation/technical-considerations/#streaming). Previously, when the user’s device lost internet connection, the SDK was unable to receive configuration data until the next application launch. With this update, the SDK can now successfully retrieve the required configuration data once the connection is restored without restarting the application.\
\
The user must grant your application the `android.permission.ACCESS_NETWORK_STATE` permission for the SDK to determine when the network becomes accessible again. If the permission is not granted, the SDK uses [Polling Mode](https://developers.kameleoon.com/feature-management-and-experimentation/technical-considerations/#polling) instead.


## 3.1.1 - 2023-06-27
* The minimum supported Android version for the SDK has been designated as API level 14. This implies that the SDK is compatible with devices running Android 4.0 (Ice Cream Sandwich) and above. By setting the minimum supported version to API level 14, the SDK ensures compatibility with a wide range of Android devices, allowing developers to target a significant portion of the Android user base.

## 3.1.0 - 2023-05-02
* Added possibility for [`CustomData`](https://developers.kameleoon.com/android-sdk.html#customdata) to use variable argument list of values
* Renaming of method:
      - `retrieveDataFromRemoteSource` -> [`getRemoteData`](https://developers.kameleoon.com/java-sdk.html#getRemoteData)
* Removed `UserAgent` data type

## 3.0.0 - 2023-02-17
* Added support of new feature flag rules:
    - [`getFeatureVariationKey`](https://developers.kameleoon.com/android-sdk.html#getFeatureVariationKey)
    - `obtainFeatureVariable` -> [`getFeatureVariable`](https://developers.kameleoon.com/android-sdk.html#getFeatureVariable)
    - [`getFeatureAllVariables`](https://developers.kameleoon.com/android-sdk.html#getFeatureAllVariables)
    - `activateFeature` -> [`isFeatureActive`](https://developers.kameleoon.com/android-sdk.html#isFeatureActive)
* Renaming of methods (old methods warn you on using and will be removed later)
    - `obtainVisitorCode` -> [`getVisitorCode`](https://developers.kameleoon.com/android-sdk.html#getVisitorCode)
    - `obtainVariationAssociatedData` -> [`getVariationAssociatedData`](https://developers.kameleoon.com/android-sdk.html#getVariationAssociatedData),
    - `obtainFeatureAllVariables` -> [`getFeatureAllVariables`](https://developers.kameleoon.com/android-sdk.html#getFeatureAllVariables),
    - `obtainExperimentList` -> [`getExperimentList`](https://developers.kameleoon.com/android-sdk.html#getExperimentList)
    - `obtainExperimentListForVisitorCode` -> [`getExperimentListForVisitorCode`](https://developers.kameleoon.com/android-sdk.html#getExperimentListForVisitorCode)
    - `obtainFeatureList` -> [`getFeatureList`](https://developers.kameleoon.com/android-sdk.html#getFeatureList)
    - `obtainFeatureListListForVisitorCode` -> [`getActiveFeatureListForVisitorCode`](https://developers.kameleoon.com/android-sdk.html#getActiveFeatureListForVisitorCode)
* Renaming of exceptions:
    - `NotActivated` -> `NotAllocated`
* Changes in Kameleoon Data:
    - Added possibility to set [`UserAgent`](https://developers.kameleoon.com/android-sdk.html#useragent).
* Added **KameleoonConfiguration**, it can be used as parameter during initialization of a client. Related to [`KameleoonClientFactory.create`](https://developers.kameleoon.com/android-sdk.html#com-kameleoon-kameleoonclientfactory)

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

# Unsupported versions:

## 2.0.13 - 2022-04-12 `[Deprecated]`
* Added method for retrieving data from remote source: [`retrieveDataFromRemoteSource`](https://developers.kameleoon.com/android-sdk.html#retrievedatafromremotesource)

## 2.0.12 - 2022-02-10 `[Deprecated]`
* Added support of multi-environment for feature flags, Related to [`activateFeature`](https://developers.kameleoon.com/android-sdk.html#activatefeature), [`obtainFeatureVariable`](https://developers.kameleoon.com/android-sdk.html#obtainfeaturevariable)
* Added checking for status of site_code (Enable / Disable). Related to [`activateFeature`](https://developers.kameleoon.com/android-sdk.html#activatefeature), [`triggerExperiment`](https://developers.kameleoon.com/android-sdk.html#triggerexperiment)

## 2.0.11 - 2021-12-15 `[Deprecated]`
* Fixed crash when calling `emptyTargetingData`
* Fixed issue with overlapping period's for scheduling. Related to [`activateFeature`](https://developers.kameleoon.com/android-sdk.html#activatefeature)

## 2.0.10 - 2021-10-25 `[Deprecated]`
* Added scheduling functionality for [`activateFeature`](https://developers.kameleoon.com/android-sdk.html#activatefeature)
* Fixed wrong bucketing on respool time. Related to [`activateFeature`](https://developers.kameleoon.com/android-sdk.html#activatefeature) and [`triggerExperiment`](https://developers.kameleoon.com/swift-sdk.html#triggerexperiment)

## 2.0.9 `[Deprecated]`
* obtainFeatureVariable support JSONArray as returning value
* Adding URI encoding PageView

## 2.0.8 `[Deprecated]`
* Migrate tests to sdk@kameleoon.com account
* Migrate exception packages

## 2.0.7 `[Deprecated]`
* Added dependencies for Maven Central Repo

## 2.0.6 `[Deprecated]`
* Improving SDK stability
* Added VisitorCodeNotValid exception when empty or exceeding the limit of 255 chars

## 2.0.5 `[Deprecated]`
* Fix runWhenReady issue
