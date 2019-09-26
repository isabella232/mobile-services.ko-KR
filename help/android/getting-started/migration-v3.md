---
description: 다음은 Android 라이브러리를 3.x 또는 2.x 버전에서 4.x 버전으로 마이그레이션하는 데 유용한 정보입니다.
keywords: android;library;mobile;sdk
seo-description: 다음은 Android 라이브러리를 3.x 또는 2.x 버전에서 4.x 버전으로 마이그레이션하는 데 유용한 정보입니다.
seo-title: Android 4.x 라이브러리로 마이그레이션
solution: Marketing Cloud,Analytics
title: Android 4.x 라이브러리로 마이그레이션
topic: 개발자 및 구현
uuid: 906e83bb-2faf-4aa2-ac9b-3fba6b833c7e
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migrating to the Android 4.x library {#migrating-to-the-android-x-library}

다음은 Android 라이브러리를 3.x 또는 2.x 버전에서 4.x 버전으로 마이그레이션하는 데 유용한 정보입니다.

>[!IMPORTANT]
>
>The SDK uses `SharedPreferences` to store data that is needed to calculate unique users, lifecycle metrics, and other data related to core SDK functionality.  SDK에 필요한 `SharedPreferences`의 값을 수정하거나 제거하면 예기치 않은 동작으로 인해 데이터 형식이 일치하지 않을 수 있습니다.

버전 4.x 라이브러리에서는 공개 메서드가 하나의 헤더로 통합되었습니다. 또한 클래스 수준 메서드를 통해 모든 기능에 액세스할 수 있으므로 포인터, 인스턴스 또는 싱글톤을 추적하지 않아도 됩니다.

## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

버전 4에서는 event, eVar, prop, heir 및 list 같은 변수를 앱에서 할당할 수 없게 되었습니다. 대신 SDK는 컨텍스트 데이터 및 처리 규칙을 사용하여 Analytics 변수에 앱 데이터를 매핑하여 보고합니다.

처리 규칙은 다음과 같은 이점을 제공합니다.

* 앱 스토어에 업데이트를 제출하지 않고도 데이터 매핑을 변경할 수 있습니다.
* 보고서 세트와 관련된 변수를 설정하는 대신 의미 있는 이름을 데이터에 사용할 수 있습니다.
* 추가 데이터를 보내는 작업에는 거의 영향을 미치지 않습니다.

   이러한 값은 처리 규칙을 사용하여 매핑될 때까지 보고서에 표시되지 않습니다.

>[!TIP]
>
>Values that you assigned directly to variables should be added to the `data` HashMap.

## Remove unused properties {#section_145222EAA20F4CC2977DD883FDDBBFC5}

새 `ADBMobileConfig.json` 파일은 애플리케이션별 전역 설정을 포함하며, 이전 버전에서 사용된 대부분의 구성 변수를 대체합니다. 다음은 `ADBMobileConfig.json` 파일 예제입니다.

```js
{
    "version" : "1.0",
    "analytics" : {
        "rsids" : "coolApp",
        "server" : "my.CoolApp.com",
        "charset" : "UTF-8",
        "ssl" : true,
        "offlineEnabled" : true,
        "lifecycleTimeout" : 5,
        "privacyDefault" : "optedin",
        "poi" : [
                    ["san francisco",37.757144,-122.44812,7000],
                    ["santa cruz",36.972935,-122.01725,600]
                ]
    },
 "target" : {
  "clientCode" : "myTargetClientCode",
  "timeout" : 5
 },
 "audienceManager" : {
  "server" : "myServer.demdex.com"
 }
}
```

## Moving the configuration file and migrating to version 4 {#section_0B844235E0B04DD4B36976A73DB28FB5}

다음 표에는 구성 파일로 이동하는 데 필요한 구성 변수가 나열되어 있습니다.

### 구성 파일 이동

1. 첫 번째 열의 변수에 대해 설정된 값을 두 번째 열의 변수로 이동합니다.
1. 코드에서 이전 구성 변수를 제거합니다.

### 버전 3.x에서 마이그레이션

버전 3.x에서 4로 마이그레이션하려면 구성 변수/메서드 값을 `ADBMobileConfig.json` 변수로 이동합니다.

| 구성 변수 또는 메서드 | Variable in the `ADBMobileConfig.json` file |
|--- |--- |
| setOfflineTrackingEnabled | "offlineEnabled" |
| setOfflineHitLimit | "batchLimit" |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| linkTrackVars | 제거합니다. 더 이상 사용되지 않습니다. |
| linkTrackEvents | 제거합니다. 더 이상 사용되지 않습니다. |

### 버전 2.x에서 마이그레이션

버전 2.x에서 버전 4로 마이그레이션하려면 첫 번째 열에서 두 번째 열의 변수로 값을 이동합니다.

| 구성 변수 | Variable in the `ADBMobileConfig.json` file |
| --- |--- |
| trackOffline | "offlineEnabled" |
| offlineLimit | "batchLimit" |
| account | "rsids" |
| trackingServer | "server"를 눌러 `"https://"` 접두사를 제거합니다. 프로토콜 접두사는 "ssl"설정에 따라 자동으로 추가됩니다. |
| trackingServerSecure | 제거. 보안 연결을 위해 "server"를 정의한 다음 "ssl"을 사용하도록 설정합니다. |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| linkTrackVars | 제거합니다. 더 이상 사용되지 않습니다. |
| linkTrackEvents | 제거합니다. 더 이상 사용되지 않습니다. |
| timestamp | 제거합니다. 더 이상 구성할 수 없습니다. |
| dc | 제거합니다. 더 이상 사용되지 않습니다. |
| userAgent | 제거합니다. 더 이상 구성할 수 없습니다. |
| dynamicVariablePrefix | 제거합니다. 더 이상 사용되지 않습니다. |
| visitorNamespace | 제거합니다. 더 이상 사용되지 않습니다. |
| usePlugins | 제거합니다. 더 이상 사용되지 않습니다. |
| useBestPractices  churn 측정에 대한 모든 호출(getChurnInstance) | 라이프사이클 지표로 대체되고 제거 |

## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

버전 4 SDK는 웹 중심의 `track` 및 `trackLink` 호출 대신 다음과 같은 방법을 사용합니다.

* `trackState`,, `home dashboard``app settings`, `cart`등 앱에서 사용할 수 있는 보기입니다.

   이 상태는 웹 사이트의 페이지와 유사하며 `trackState` 호출은 페이지 보기를 증가시킵니다.

* `trackAction` actions, such as `logons`, `banner taps`, `feed subscriptions`, and so on that occur in your app and that you want to measure.

The `contextData` parameter for both of these methods is a `HashMap<String, Object>`, which contains the name-value pairs that are sent as context data.

## Events, props, and eVars

버전 4에서는 더 이상 events, eVars, props, heirs 및 lists와 같은 변수를 앱에서 직접 할당할 수 없습니다. SDK는 이제 컨텍스트 데이터 및 처리 규칙을 사용하여 Analytics 변수에 앱 데이터를 매핑하여 보고합니다.

처리 규칙은 다음과 같은 이점을 제공합니다.

* 앱 스토어에 업데이트를 제출하지 않고도 데이터 매핑을 변경할 수 있습니다.
* 보고서 세트와 관련된 변수를 설정하는 대신 의미 있는 이름을 데이터에 사용할 수 있습니다.
* 추가 데이터를 보내는 작업에는 거의 영향을 미치지 않습니다.

   이러한 값은 처리 규칙을 사용하여 매핑될 때까지 보고서에 표시되지 않습니다. 자세한 내용은 [처리 규칙 및 컨텍스트 데이터](/help/android/getting-started/proc-rules.md)를 참조하십시오.

변수에 직접 할당한 값은 `data` HashMap에 추가해야 합니다. This means that calls to `setProp`, `setEvar`, and assignments to persistent context data should be removed and the values be added to the `data` parameter.

## AppSection/서버, GeoZip, 거래 ID, 캠페인 및 기타 표준 변수

위에 나열된 변수를 포함하여 측정 개체에 설정한 데이터는 대신 `data` HashMap에 추가해야 합니다. `trackState` 또는 `trackAction` 호출과 함께 전송되는 데이터는 `data` 매개 변수의 페이로드뿐입니다.

### 추적 호출 바꾸기

다음 메서드를 `trackState` 또는 `trackAction` 호출로 바꿉니다.

* **버전 3.x에서 마이그레이션**

   * `trackAppState (trackState)`
   * `trackEvents (trackAction)`
   * `track (trackAction)`
   * `trackLinkURL (trackAction)`

* **버전 2.x에서 마이그레이션**

   * `track (trackState)`
   * `trackLink (trackAction)`

## Custom visitor ID {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file, and all other offline configuration is done automatically.

다음 메서드 호출을 제거합니다.

**버전 3.x**

* `setOnline`
* `setOffline`

**버전 2.x**

* `forceOffline`
* `forceOnline`

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

For more information about the products variable, see [Products variable](/help/android/analytics-main/products/products.md).

