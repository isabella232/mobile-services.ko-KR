---
description: 이 섹션에서는 이전 Windows 모바일 SDK의 3.x 버전에서 Experience Cloud 솔루션용 Windows 8.1 Universal App Store 4.x SDK로 마이그레이션하는 방법에 대해 설명합니다.
seo-description: 이 섹션에서는 이전 Windows 모바일 SDK의 3.x 버전에서 Experience Cloud 솔루션용 Windows 8.1 Universal App Store 4.x SDK로 마이그레이션하는 방법에 대해 설명합니다.
seo-title: 4.x SDK로 마이그레이션
solution: Experience Cloud,Analytics
title: 4.x SDK로 마이그레이션
topic: Developer and implementation
uuid: e0fe3b7b-cda5-4a91-834c-2c7e17a501a3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 13%

---


# 4.x SDK로 마이그레이션 {#migrate-to-the-x-sdks}

이 섹션에서는 이전 Windows 모바일 SDK의 3.x 버전에서 Experience Cloud 솔루션용 Windows 8.1 Universal App Store 4.x SDK로 마이그레이션하는 방법에 대해 설명합니다.

버전 4.x로 이동하면 이제 정적 방법을 통해 모든 기능에 액세스할 수 있으므로 더 이상 자신의 개체를 추적하지 않습니다.

다음 섹션에서는 버전 3.x에서 버전 4.x로 마이그레이션하는 과정을 안내합니다.

## 사용하지 않는 속성 제거 {#section_145222EAA20F4CC2977DD883FDDBBFC5}

다운로드에 포함된 새로운 `ADBMobileConfig.json` 파일이 있을 것입니다. 이 파일에는 애플리케이션별 전역 설정이 들어 있으며 이전 버전에서 사용된 대부분의 구성 변수를 대체합니다. 다음은 `ADBMobileConfig.json` 파일 예제입니다.

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
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

다음 표에는 구성 파일로 이동하는 데 필요한 구성 변수가 나열되어 있습니다. 첫 번째 열의 변수에 대한 값 세트를 두 번째 열의 변수로 이동한 다음 코드에서 이전 구성 변수를 제거합니다.

## 3.x에서 마이그레이션

| 구성 변수/방법 | Variable in the `ADBMobileConfig.json` file. |
|--- |--- |
| offlineTrackingEnabled | &quot;offlineEnabled&quot; |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| setOfflineHitLimit | 제거, 더 이상 사용되지 않습니다. |
| linkTrackVars | 제거, 더 이상 사용되지 않습니다. |
| linkTrackEvents | 제거, 더 이상 사용되지 않습니다. |

## 추적 호출 및 추적 변수 업데이트 {#section_96E7D9B3CDAC444789503B7E7F139AB9}

버전 4 SDK는 웹 기반 `Track` 과 `TrackLink` 호출을 사용하는 대신 모바일 환경에서 보다 효과적인 두 가지 방법을 사용합니다.

* `TrackState` 상태는 &quot;홈 대시보드&quot;, &quot;앱 설정&quot;, &quot;장바구니&quot; 등과 같이 앱에서 사용할 수 있는 보기입니다. 이 상태는 웹 사이트의 페이지와 유사하며 `trackState` 호출은 페이지 보기를 증가시킵니다.

* `TrackAction` 작업은 &quot;로그온&quot;, &quot;배너 탭&quot;, &quot;피드 구독&quot; 및 기타 지표 등 측정하려는 앱에서 발생하는 작업입니다. 이러한 호출은 페이지 보기를 증가시키지 않습니다.

The `contextData` parameter for both of these methods contains name-value pairs that are sent as context data.

## 이벤트, Prop, eVar

SDK 방법을 살펴본 [](/help/windows-appstore/c-configuration/methods.md)경우 이벤트, eVar, prop, 상속자 및 목록을 어디에 설정해야 하는지 궁금해 할 것입니다. 버전 4에서는 더 이상 앱에서 바로 이러한 유형의 변수를 할당할 수 없습니다. 대신, SDK는 컨텍스트 데이터 및 처리 규칙을 사용하여 보고를 위해 앱 데이터를 Analytics 변수에 매핑합니다.

처리 규칙은 다음과 같은 여러 이점을 제공합니다.

* App Store에 업데이트를 제출하지 않고 데이터 매핑을 변경할 수 있습니다.
* 보고서 세트에 고유한 변수를 설정하는 대신 데이터에 의미 있는 이름을 사용할 수 있습니다.
* 추가 데이터 전송에는 거의 영향을 주지 않습니다. 이러한 값은 처리 규칙을 사용하여 매핑될 때까지 보고서에 표시되지 않습니다.

For more information, see *Processing Rules* in [Analytics](/help/windows-appstore/analytics/analytics.md).

변수에 직접 할당했던 모든 값을 컨텍스트 데이터에 추가해야 합니다. This means that calls to `SetProp`, `SetEvar`, and assignments to persistent context data should all be removed and the values added to context data.

**AppSection/Server, GeoZip, 거래 ID, 캠페인 및 기타 표준 변수**

위에 나열된 변수를 포함하여 측정 개체에서 설정하던 다른 데이터는 컨텍스트 데이터에 추가해야 합니다.

간단히 말해, `TrackState` 또 `TrackAction` 는 호출과 함께 전송된 유일한 데이터는 매개 변수의 페이로드입니다 `data` .

### 추적 호출 대체

Throughout your code, replace the following methods with a call to `trackState` or `trackAction`:

### 3.x에서 마이그레이션

* `TrackAppState` (TrackState)
* `TrackEvents` (TrackAction)
* `Track` (TrackAction)
* `TrackLinkURL` (TrackAction)

## 사용자 지정 방문자 ID {#section_2CF930C13BA64F04959846E578B608F3}

`visitorID` 변수를 `setUserIdentifier`에 대한 호출로 바꿉니다.

## 오프라인 추적 {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file. All other offline configuration is done automatically.

코드 전체에서 다음 메서드에 대한 호출을 제거합니다.

### 3.x에서 마이그레이션

* `SetOnline`
* `SetOffline`

## Products 변수 {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

 변수는 처리 규칙에서 사용할 수 없으므로 다음 구문을 사용하여 `products`products를 설정할 수 있습니다.

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

이 예에서, 값 `"&&products"` 은 `";Cool Shoe`&quot;이고 추적 중인 이벤트 유형에 대해 제품 문자열 구문을 따라야 합니다.