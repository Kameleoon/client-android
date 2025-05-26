[trackConversion]: https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#trackconversion

# Changelog
## 4.13.0 - 2025-05-26
### Features
* Added support for **304 (Not Modified)** responses from the SDK config service to avoid redundant updates and reduce traffic when the configuration hasn't changed.
* Added automatic detection of the [`Device`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#device) type for targeting and reporting purposes. However, it can still be manually overridden using the [`addData`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#addData) method.
* Added support for a **New**/**Returning** visitor breakdown filter in reports (requires calling [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#getremotevisitordata)).

## 4.12.1 - 2025-04-08
### Bug Fixes
* Changed the order in which **conversion** and **experiment** events are sent. This may lead to more accurate **visit**-level experiment reporting.

## 4.12.0 - 2025-04-02
### Features
* Added support for new conditions:
    - Exclusive Campaign
    - Experiment
    - Personalization

All notable changes to this project will be documented in this file.

## 4.11.1 - 2025-03-26
### Bug fixes
* Fixed an issue where compressed conversions (introduced in [v4.6.0](https://github.com/Kameleoon/client-android/blob/main/CHANGELOG.md#460---2025-01-17)) could be incorrectly sent again, potentially affecting the `revenue` value for a goal.
* The value of the `revenue` parameter was not accounted for in some overloads of the [`trackConversion`][trackConversion] method.

## 4.11.0 - 2025-03-24 [`[Critical Issue: Update to 4.11.1]`](#4111---2025-03-26)
### Features
* Added new optional parameters `negative` and `metadata` to the [`trackConversion`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#trackconversion) method.
* Added new optional parameter `metadata` to the [`Conversion`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#conversion) data constructor.

## 4.10.0 - 2025-03-18 [`[Critical Issue: Update to 4.11.1]`](#4111---2025-03-26)
### Features
* Added support for Contextual Bandit evaluations. Calling [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#getremotevisitordata) with the `cbs=true` flag is required for this feature to function correctly. Platform-wide release expected in March 2025.

## 4.9.0 - 2025-02-26 [`[Critical Issue: Update to 4.11.1]`](#4111---2025-03-26)
### Features
* Added SDK support for **Mutually Exclusive Groups**. When feature flags are grouped into a **Mutually Exclusive Group**, only one flag in the group will be evaluated at a time. All other flags in the group will automatically return their default variation.
* Added new configuration parameter `networkDomain` (`network_domain`) to [`KameleoonClientConfig`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#create) and the [configuration](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#create) file. This parameter allows specifying a custom domain for all outgoing network requests.

## 4.8.0 - 2025-02-20 [`[Critical Issue: Update to 4.11.1]`](#4111---2025-03-26)
### Features
* Added suspended versions of methods (using Kotlin coroutines) as an addition to callback-based implementations, enabling easier invocation and error handling:
    - [`runWhenReady`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#runwhenready)
    - [`getRemoteData`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#getremotedata)
    - [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#getremotevisitordata)
    - [`getVisitorWarehouseAudience`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#getvisitorwarehouseaudience)
* The `get()` method of the `Result` class is deprecated. Using `getOrThrow()` is recommended instead. The logic remains the same, but the method name has been changed to explicitly indicate that it can throw an exception.

## 4.7.0 - 2025-02-10 [`[Critical Issue: Update to 4.11.1]`](#4111---2025-03-26)
### Features
* Added SDK support for **holdout experiments**. Visitors assigned to a holdout experiment are excluded from all other rollouts and experiments, and consistently receive the default variation. For visitors not in a holdout experiment, the standard evaluation process applies, allowing them to be evaluated for all feature flags as usual. Platform-wide release expected in February 2025.

## 4.6.0 - 2025-01-17 [`[Critical Issue: Update to 4.11.1]`](#4111---2025-03-26)
### Features
* Added the [`setForcedVariation()`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#setforcedvariation) method. This method allows explicitly setting a forced variation for a visitor, which will be applied during experiment evaluation.
* Compression has been added to the [Conversions](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#conversion) list, preventing its unchecked growth and improving the speed of visitor synchronization with local storage.

## 4.5.0 - 2024-11-14
### Features
* Introduced a new `visitorCode` parameter to [`RemoteVisitorDataFilter`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#using-parameters-in-getremotevisitordata). This parameter determines whether to use the `visitorCode` from the most recent previous visit instead of the current `visitorCode`. When enabled, this feature allows visitor exposure to be based on the retrieved `visitorCode`, facilitating [cross-device reconciliation](https://developers.kameleoon.com/core-concepts/cross-device-experimentation/). Default value of the parameter is `true`.
* Use [`RemoteVisitorDataFilterBuilder`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#using-parameters-in-getremotevisitordata) instead of the deprecated [`RemoteVisitorDataFilter`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#using-parameters-in-getremotevisitordata) constructor.
* Mapping identifier is now persistent, enabling the assigned variation for a visitor to be retained when [merging sessions](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#using-custom-data-for-session-merging) between anonymous and registered users.

## 4.4.0 - 2024-10-11
### Features
* Introduced new evaluation methods for clarity and improved efficiency when working with the SDK:
  - [`getVariation`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#getvariation)
  - [`getVariations`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#getvariations)
* These methods replace the deprecated ones:
  - [`getFeatureVariationKey`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#getfeaturevariationkey)
  - [`getFeatureVariable`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#getfeaturevariable)
  - [`getActiveFeatures`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#getactivefeatures)
  - [`getFeatureVariationVariables`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#getfeaturevariationvariables)
* A new version of the [`isFeatureActive`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#isfeatureactive) method now includes an optional `track` parameter, which controls whether the assigned variation is tracked (default: `true`).
### Bug Fixes
* Fixed incorrect values for **NUMBER** feature variables of types **double** and **long**.

## 4.3.0 - 2024-09-05
### Features
* Enhanced [logging](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#logging):
    - Introduced [log levels](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#log-levels):
        - `NONE`
        - `ERROR`
        - `WARNING`
        - `INFO`
        - `DEBUG`
    - Added support for [custom logger](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#custom-handling-of-logs) implementations.
* Enhanced tracking to consolidate multiple requests into a single one, combining visitor information and sending it once per interval.
* Added a new variation of the [`flush`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#flush) with `instant` parameter. If the parameter's value is `true` the visitor's data is tracked instantly. Otherwise, the visitor's data will be tracked with the next tracking interval. Default value of the parameter is `false`.
* Added new configuration parameter `trackingIntervalMillisecond` (`tracking_interval_millisecond`) to [`KameleoonClientConfig`](https://developers.kameleoon.com/android-sdk.html#initialize-the-kameleoon-client) and the [configuration](https://developers.kameleoon.com/android-sdk.html#additional-configuration) file, which is used to set interval for tracking requests. Default value is `1000` milliseconds.

## 4.2.3 - 2024-08-22
### Bug Fixes
* Fixed `NullPointerException` occurring when calling the [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#getremotevisitordata) method before the SDK is initialized.

## 4.2.2 - 2024-08-13
### Features
* Added the [`getVisitorCode`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#getvisitorcode) method, which returns the unique visitor code used within `KameleoonClient`.

## 4.2.1 - 2024-06-27
### Bug Fixes
* Resolved an issue where the [runWhenReady](https://developers.kameleon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#runwhenready) method could throw a `ConcurrentModificationException` if both of the following conditions are met simultaneously:
  - Intensive usage of the [runWhenReady](https://developers.kameleon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#runwhenready) method in multiple threads.
  - Kameleoon infrastructure is in outage or the user device encounters some network connection issues.

## 4.2.0 - 2024-06-21
### Features
* The [Likelihood to convert](https://developers.kameleoon.com/feature-management-and-experimentation/using-visit-history-in-feature-flags-and-experiments) targeting condition is now available. Pre-loading the data is required using [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#getremotevisitordata) with the `kcs` parameter set to `true`.

## 4.1.0 - 2024-05-22
### Features
* Added a new optional parameter `isUniqueIdentifier` (`is_unique_identifier`) that provides additional capabilities with [cross-device experimentation](https://developers.kameleoon.com/core-concepts/cross-device-experimentation) for the [`KameleoonClientConfig`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#create) and external [configuration](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#configure-additional-properties) file.
* Added new targeting conditions (some conditions require you to pre-load data with [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#getremotevisitordata))
  - Operating System
  - IP Geolocation
  - Kameleoon Segment
  - Target Feature Flag
  - Time since First Visit
  - Time since Last Visit
  - Number of Visits Today
  - Total Number of Visits
  - New or Returning Visitor
* Added new Kameleoon Data type:
  - [`Geolocation`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk#geolocation)
### Bug Fixes
* Stability and performance improvements.

## 4.0.1 - 2024-02-16
### Features
* Added support of different Data API servers over the world for even more quicker network requests.

## 4.0.0 - 2024-02-08
### Breaking Changes
* Migrated to [`AndroidX`](https://developer.android.com/jetpack/androidx) library as support for the [`Support Library`](https://developer.android.com/topic/libraries/support-library) is deprecated.
* Removed the `visitorCode` parameter from all methods that accepted it. You must now specify the visitor code during initialization. As a result, a `KameleoonClient` instance only works for a single visitor:
  - [`addData`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#adddata)
  - [`flush`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#flush)
  - [`isFeatureActive`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#isfeatureactive)
  - [`getFeatureVariationKey`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#getfeaturevariationkey)
  - [`getFeatureVariable`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#getfeaturevariable)
  - [`trackConversion`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#trackconversion)
  - [`getActiveFeatureList`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#getactivefeaturelist)
  - [`getVisitorWarehouseAudience`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#getvisitorwarehouseaudience)
* Removed all deprecated methods and exceptions related to **experiments**:
  - `triggerExperiment`
  - `getVariationAssociatedData` (`obtainVariationAssociatedData`)
  - `getExperimentList` (`obtainExperimentList`)
  - `getExperimentListForVisitor` (`obtainExperimentListForVisitor`)
  - `ExperimentConfigurationNotFound`
  - `NotTargeted`
  - `NotAllocated`
  - `SiteCodeDisabled`
* Removed additional methods that were deprecated in 3.x versions:
  - `activateFeature`
  - `obtainVisitorCode`
  - `obtainFeatureVariable`
  - `obtainFeatureAllVariables`
  - `obtainFeatureList`
  - `obtainFeatureListForVisitorCode`
  - `retrieveDataFromRemoteSource`
* Changed the following classes, methods, fields and exceptions:
  * Classes:
    - Renamed `KameleoonConfiguraton` to [`KameleoonClientConfig`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#initialize-the-kameleoon-client).
    - Data classes were allocated into their own package `com.kameleoon.data`.
    - Renamed static members of `Device` class:
        - `Device.PHONE` renamed to `Device.phone()`
        - `Device.TABLET` renamed to `Device.tablet()`
        - `Device.DESKTOP` renamed to `Device.desktop()`.
    - [`Conversion`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#conversion) has additional constructors with optional `revenue` and `negative` values. Also, the types of these fields are changed to primitives.
  * Interfaces:
    - For the [`runWhenReady`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#runwhenready) method, the interface `KameleoonReadyCallback` changed to `ResultCompletion<Boolean, TimeoutException>`.
    - For the [`getRemoteData`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#getremotedata) method, the interface `KameleoonDataCallback` changed to `ResultCompletion<JSONObject, Exception>`.
    - For the [`getRemoteVisitorData`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#getremotevisitordata) method, the interface `KameleoonVisitorDataCallback` changed to `ResultCompletion<List<Data>, Exception>`.
    - For the [`getVisitorWarehouseAudience`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#getvisitorwarehouseaudience) method, the interface `KameleoonVisitorDataCallback` changed to `ResultCompletion<CustomData, Exception>`.
    - For the [`onUpdateConfiguration`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#onupdateconfiguration) method, the interface `KameleoonUpdateConfigurationHandler` changed to `ResultCompletion<Long, Exception>`.
  * Methods:
    - Removed `getVisitorCode`.
    - Renamed `getFeatureAllVariables` to [`getFeatureVariationVariables`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#getfeaturevariationvariables).
    - Renamed `getVisitorWarehouseAudiences` to [`getVisitorWarehouseAudience`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#getvisitorwarehouseaudience).
    - Renamed `getActiveFeatureListForVisitorCode` to [`getActiveFeatures`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#getactivefeatures).
    - Renamed `updateConfigurationHandler` to [`onUpdateConfiguration`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#onupdateconfiguration).
    - Changed `revenue` argument to optional in the [`trackConversion`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#trackconversion) method. Also, the type of `revenue` was changed to `float`.
  * Fields:
    - Renamed `configurationRefreshInterval` to `refreshIntervalMinute` in [`KameleoonClientConfig`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#initialize-the-kameleoon-client).
    - Renamed `defaultTimeout` to `defaultTimeoutMillisecond` in [`KameleoonClientConfig`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#initialize-the-kameleoon-client).
    - Renamed `actions_configuration_refresh_interval` to `refresh_interval_minute` in the [configuration](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#additional-configuration) file.
    - Renamed `default_timeout` to `default_timeout_millisecond` in the [configuration](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#additional-configuration) file.
    - Renamed `sitecode` to `siteCode` in [`KameleoonClientFactory.create`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#create).
  * Exceptions:
    - Removed `CredentialsNotFound` (the `clientId` and `clientSecret` credentials are now optional).
    - Renamed `VisitorCodeNotValid` to `VisitorCodeInvalid`.
    - Renamed `FeatureConfigurationNotFound` to `FeatureNotFound`.
    - Renamed `VariationConfigurationNotFound` to `FeatureVariationNotFound`.
  * Added new exception `SiteCodeIsEmpty` for the method [`KameleoonClientFactory.create`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#create) that indicates the provided `siteCode` is empty.
  * Added new exception `FeatureEnvironmentDisabled` indicating that the feature flag is disabled for certain environments. The following methods can throw the new exception:
      - [`getFeatureVariationKey`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#getfeaturevariationkey)
      - [`getFeatureVariable`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#getfeaturevariable)
      - [`getFeatureVariationVariables`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#getfeaturevariationvariables)
### Features
* Added the [`setLegalConsent`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#setlegalconsent) method to determine the types data that Kameleoon includes in tracking requests. This helps you adhere to legal and regulatory requirements while responsibly managing visitor data. You can find more information in the [Consent management policy](https://help.kameleoon.com/consent-management-policy/).
* [`KameleoonClientFactory.create`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#create) method accepts `visitorCode` as a parameter to use for all SDK methods. If you omit the `visitorCode`, the SDK generates a new visitor code value that it uses until you overwrite it. To overwrite a `visitorCode`, provide it as a parameter explicitly to the method. The method throws `VisitorCodeInvalid` if the provided `visitorCode` is invalid (empty or longer than 255 characters).
* Added new configuration fields to [`KameleoonClientConfig`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#initialize-the-kameleoon-client) and external [configuration](https://developers.kameleoon.com/android-sdk.html#additional-configuration) file:
    - `dataExpirationIntervalMinute` (`data_expiration_interval_minute`) specifies the time (in minutes) that the SDK retains the visitor's data on the device. By default, the TTL (time to live) is `Integer.MAX_VALUE`.
* Changed the `key` parameter in the [`getRemoteData`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#getremotedata) method from required to optional. If you don't provide a `key` parameter, the SDK uses the `visitorCode` specified during initialization.
* Added the [`getActiveFeatures`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#getactivefeatures) method, which retrieves information about the active feature flags that are available for a specific visitor code. This method replaces the deprecated `getActiveFeatureListForVisitorCode` method.

### Bug Fixes
* Stability and performance improvements.

## 3.4.1 - 2023-12-19
### Bug Fixes
* Resolved an issue where the [`KameleoonClientFactory.create`](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#create) method could crash during initialization under specific conditions.

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
    - [Device](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#device)
    - [Conversion](https://developers.kameleoon.com/feature-management-and-experimentation/mobile-sdks/android-sdk/#trackconversion)

## 3.1.2 - 2023-07-04
* Improved the handling of internet connection loss for the [Real-Time Streaming Architecture](https://developers.kameleoon.com/feature-management-and-experimentation/technical-considerations/#streaming): We have resolved a critical issue related to the [Real-Time Streaming Architecture](https://developers.kameleoon.com/feature-management-and-experimentation/technical-considerations/#streaming). Previously, when the user’s device lost internet connection, the SDK was unable to receive configuration data until the next application launch. With this update, the SDK can now successfully retrieve the required configuration data once the connection is restored without restarting the application.\
\
The user must grant your application the `android.permission.ACCESS_NETWORK_STATE` permission for the SDK to determine when the network becomes accessible again. If the permission is not granted, the SDK uses [Polling Mode](https://developers.kameleoon.com/feature-management-and-experimentation/technical-considerations/#polling) instead.


## 3.1.1 - 2023-06-27
* The minimum supported Android version for the SDK has been designated as API level 14. This implies that the SDK is compatible with devices running Android 4.0 (Ice Cream Sandwich) and above. By setting the minimum supported version to API level 14, the SDK ensures compatibility with a wide range of Android devices, allowing developers to target a significant portion of the Android user base.

## 3.1.0 - 2023-05-02
* Added possibility for [`CustomData`](https://developers.kameleoon.com/android-sdk.html#customdata) to use variable argument list of values
* Renaming of method:
      - `retrieveDataFromRemoteSource` -> [`getRemoteData`](https://developers.kameleoon.com/android-sdk.html#getRemoteData)
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
* Fixed wrong bucketing on respool time. Related to [`activateFeature`](https://developers.kameleoon.com/android-sdk.html#activatefeature) and [`triggerExperiment`](https://developers.kameleoon.com/android-sdk.html#triggerexperiment)

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
