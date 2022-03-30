---
description: 이 섹션에서는 이전 Windows 모바일 SDK의 3.x 버전에서 Experience Cloud 솔루션용 Windows 8.1 Universal App Store 4.x SDK로 마이그레이션하는 방법을 설명합니다.
solution: Experience Cloud Services,Analytics
title: 4.x SDK로 마이그레이션
topic-fix: Developer and implementation
uuid: e0fe3b7b-cda5-4a91-834c-2c7e17a501a3
exl-id: d6dc34f2-61b7-4026-a66a-19284e21e69c
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 25%

---

# 4.x SDK로 마이그레이션 {#migrate-to-the-x-sdks}

이 섹션에서는 이전 Windows 모바일 SDK의 3.x 버전에서 Experience Cloud 솔루션용 Windows 8.1 Universal App Store 4.x SDK로 마이그레이션하는 방법을 설명합니다.

버전 4.x로 이동하면 이제 정적 메서드를 통해 모든 기능에 액세스할 수 있으므로 더 이상 고유한 개체를 추적하지 않습니다.

다음 섹션에서는 버전 3.x에서 버전 4.x로 마이그레이션하는 과정을 안내합니다.

## 사용하지 않는 속성 제거 {#section_145222EAA20F4CC2977DD883FDDBBFC5}

아마 새로운 걸 발견했을 겁니다 `ADBMobileConfig.json` 다운로드에 포함된 파일입니다. 이 파일은 애플리케이션별 전역 설정을 포함하며, 이전 버전에서 사용된 대부분의 구성 변수를 대체합니다. 다음은 `ADBMobileConfig.json` 파일 예제입니다.

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

다음 표에는 구성 파일로 이동하는 데 필요한 구성 변수가 나열되어 있습니다. 첫 번째 열의 변수에 대해 설정된 값을 두 번째 열의 변수로 이동한 다음 코드에서 이전 구성 변수를 제거합니다.

## 3.x에서 마이그레이션

| 구성 변수/메서드 | 의 변수 `ADBMobileConfig.json` 파일. |
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

웹 중심의 `Track` 및 `TrackLink` 를 호출하는 경우 버전 4 SDK는 모바일 세계에서 약간 더 적합한 두 가지 방법을 사용합니다.

* `TrackState` 상태는 &quot;홈 대시보드&quot;, &quot;앱 설정&quot;, &quot;장바구니&quot; 등과 같이 앱에서 사용할 수 있는 보기입니다. 이 상태는 웹 사이트의 페이지와 유사하며 `trackState` 호출은 페이지 보기를 증가시킵니다.

* `TrackAction` 작업은 &quot;logons&quot;, &quot;banner taps&quot;, &quot;feed subscriptions&quot; 및 기타 지표 등 앱에서 발생하여 측정하려는 작업입니다. 이러한 호출은 페이지 보기를 증가시키지 않습니다.

다음 `contextData` 이 두 메서드의 매개 변수에는 컨텍스트 데이터로 전송되는 이름-값 쌍이 포함됩니다.

## Event, Prop, eVar

만약 [SDK 메서드](/help/windows-appstore/c-configuration/methods.md), events, eVar, prop, 상속자 및 목록을 어디에 설정해야 하는지 알 수 있습니다. 버전 4에서는 더 이상 이러한 유형의 변수를 앱에서 바로 할당할 수 없습니다. 대신, SDK는 컨텍스트 데이터 및 처리 규칙을 사용하여 앱 데이터를 Analytics 변수에 매핑해서 보고에 사용합니다.

처리 규칙은 다음과 같은 몇 가지 이점을 제공합니다.

* 앱스토어에 업데이트를 제출하지 않고 데이터 매핑을 변경할 수 있습니다.
* 보고서 세트에 고유한 변수를 설정하는 대신 데이터에 의미 있는 이름을 사용할 수 있습니다.
* 추가 데이터 전송에는 거의 영향을 주지 않습니다. 이러한 값은 처리 규칙을 사용하여 매핑될 때까지 보고서에 표시되지 않습니다.

자세한 내용은 *처리 규칙* in [Analytics](/help/windows-appstore/analytics/analytics.md).

변수에 직접 할당한 모든 값은 대신 컨텍스트 데이터에 추가해야 합니다. 즉, `SetProp`, `SetEvar`및 영구 컨텍스트 데이터에 할당하고 모두 제거하고 컨텍스트 데이터에 추가된 값을 제거해야 합니다.

**AppSection/서버, GeoZip, 트랜잭션 ID, 캠페인 및 기타 표준 변수**

위에 나열된 변수를 포함하여 측정 개체에 설정한 다른 모든 데이터는 대신 컨텍스트 데이터에 추가해야 합니다.

간단히 말하면, `TrackState` 또는 `TrackAction` 호출은 의 페이로드입니다 `data` 매개 변수.

### 추적 호출 대체

코드 전체에서 다음 메서드를 `trackState` 또는 `trackAction`:

### 3.x에서 마이그레이션

* `TrackAppState` (TrackState)
* `TrackEvents` (TrackAction)
* `Track` (TrackAction)
* `TrackLinkURL` (TrackAction)

## 사용자 지정 방문자 ID {#section_2CF930C13BA64F04959846E578B608F3}

`visitorID` 변수를 `setUserIdentifier`에 대한 호출로 바꿉니다.

## 오프라인 추적 {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

오프라인 추적은 `ADBMobileConfig.json` 파일. 다른 모든 오프라인 구성은 자동으로 수행됩니다.

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

이 예에서 값 `"&&products"` is `";Cool Shoe`&quot; 및에서 추적 중인 이벤트 유형에 대해 제품 문자열 구문을 따라야 합니다.
