---
description: 다음은 iOS 라이브러리를 버전 3.x 또는 2.x에서 4.x 버전으로 마이그레이션하는 데 유용한 정보입니다.
seo-description: 다음은 iOS 라이브러리를 버전 3.x 또는 2.x에서 4.x 버전으로 마이그레이션하는 데 유용한 정보입니다.
seo-title: 4.x iOS 라이브러리로 마이그레이션
solution: Experience Cloud,Analytics
title: 4.x iOS 라이브러리로 마이그레이션
topic-fix: Developer and implementation
uuid: 5668972b-f355-4e03-9df0-8c82ddf6809b
exl-id: a58067e0-b6f4-4900-ba3f-7256d9259420
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 100%

---

# 4.x iOS 라이브러리로 마이그레이션{#migrating-to-the-x-ios-library}

다음은 iOS 라이브러리를 버전 3.x 또는 2.x에서 4.x 버전으로 마이그레이션하는 데 유용한 정보입니다.

>[!IMPORTANT]
>
>SDK는 `NSUserDefaults`를 사용하여 고유 사용자, 라이프사이클 지표 및 코어 SDK 기능과 관련된 기타 데이터를 계산하는 데 필요한 데이터를 저장합니다. SDK에 필요한 `NSUserDefaults`의 값을 수정하거나 제거하면 예기치 않은 동작으로 인해 데이터 형식이 일치하지 않을 수 있습니다.

iOS SDK 라이브러리 버전 4.x에서는 공용 메서드가 하나의 헤더로 통합되었습니다. 또한 클래스 수준 메서드를 통해 모든 기능에 액세스할 수 있으므로 포인터, 인스턴스 또는 싱글톤을 추적하지 않아도 됩니다.

## Event, Prop 및 eVar {#section_76EA6F5611184C5CAE6E62956D84D7B6}

버전 4에서는 더 이상 앱의 이벤트, eVar, prop, 상속자 및 목록과 같은 변수를 직접 할당할 수 없습니다. 대신, SDK는 컨텍스트 데이터 및 처리 규칙을 사용하여 앱 데이터를 Analytics 변수에 매핑해서 보고에 사용합니다.

처리 규칙은 다음과 같은 이점을 제공합니다.

* 앱스토어에 업데이트를 제출하지 않고 데이터 매핑을 변경할 수 있습니다.
* 보고서 세트에 고유한 변수를 설정하는 대신 데이터에 의미 있는 이름을 사용할 수 있습니다.
* 추가 데이터 전송에는 거의 영향을 주지 않습니다.

   이러한 값은 처리 규칙을 사용하여 매핑될 때까지 보고서에 표시되지 않습니다.

>[!TIP]
>
>변수에 직접 할당했던 값을 이제 `data` NSDictionary에 추가해야 합니다.

## 사용하지 않는 속성 제거 {#section_145222EAA20F4CC2977DD883FDDBBFC5}

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


### 구성 파일 이동

구성 파일을 이동하려는 경우:

1. 첫 번째 열의 변수에 대해 설정된 값을 두 번째 열의 변수로 이동합니다.
1. 코드에서 이전 구성 변수를 제거합니다.

### 마이그레이션 정보

다음 표에는 구성 파일로 이동하는 데 필요한 구성 변수가 나열되어 있습니다.

#### 버전 3.x에서 마이그레이션

첫 번째 열에서 두 번째 열의 변수로 값을 이동합니다.

| 구성 변수 | `ADBMobileConfig.json` 파일의 변수 |
|--- |--- |
| offlineTrackingEnabled | &quot;offlineEnabled&quot; |
| offlineHitLimit | &quot;batchLimit&quot; |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| linkTrackVars | 제거, 더 이상 사용되지 않습니다. |
| linkTrackEvents | 제거, 더 이상 사용되지 않습니다. |


#### 버전 2.x에서 마이그레이션

첫 번째 열에서 두 번째 열의 변수로 값을 이동합니다.

| 구성 변수 | `ADBMobileConfig.json` 파일의 변수 |
|--- |--- |
| trackOffline | &quot;offlineEnabled&quot; |
| offlineLimit | &quot;batchLimit&quot; |
| account | &quot;rsids&quot; |
| trackingServer | &quot;server&quot;, `"https://"` 접두사를 제거합니다. 프로토콜 접두사는 &quot;ssl&quot; 설정에 따라 자동으로 추가됩니다. |
| trackingServerSecure | 제거. 보안 연결에 대해 &quot;server&quot;를 정의한 다음 &quot;ssl&quot;을 활성화합니다. |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;통화&quot; |
| ssl | &quot;ssl&quot; |
| linkTrackVars | 제거, 더 이상 사용되지 않습니다. |
| linkTrackEvents | 제거, 더 이상 사용되지 않습니다. |
| timestamp | 제거, 더 이상 구성할 수 없습니다. |
| dc | 제거, 더 이상 사용되지 않습니다. |
| userAgent | 제거, 더 이상 구성할 수 없습니다. |
| dynamicVariablePrefix | 제거, 더 이상 사용되지 않습니다. |
| visitorNamespace | 제거, 더 이상 사용되지 않습니다. |
| usePlugins | 제거, 더 이상 사용되지 않습니다. |
| useBestPractices - churn 측정에 대한 모든 호출(getChurnInstance) | 제거합니다. 라이프사이클 지표로 대체됩니다. 자세한 내용은 [라이프사이클 지표](/help/ios/metrics.md)를 참조하십시오. |


## 추적 호출 및 추적 변수 업데이트 {#section_96E7D9B3CDAC444789503B7E7F139AB9}

버전 4 SDK는 웹 중심의 `track` 및 `trackLink` 호출 대신 다음과 같은 방법을 사용합니다.

* `trackState:data:` 상태는 `home dashboard`, `app settings`, `cart` 등과 같이 앱에서 사용할 수 있는 보기입니다.

   이 상태는 웹 사이트의 페이지와 유사하며 `trackState` 호출은 페이지 보기를 증가시킵니다.

* `logons`, `banner taps`, `feed subscriptions` 등과 같이 앱에서 발생하며 사용자가 측정하려는 `trackAction:data:` 작업입니다.

이 두 메서드의 `data` 매개 변수는 컨텍스트 데이터로 전송되는 이름 - 값 쌍을 포함하는 `NSDictionary`입니다.

### Events, props, eVars

버전 4에서는 더 이상 앱의 이벤트, eVar, prop, 상속자 및 목록과 같은 변수를 직접 할당할 수 없습니다. 이제 SDK에서 컨텍스트 데이터 및 처리 규칙을 사용하여 앱 데이터를 Analytics 변수에 매핑하여 보고할 수 있습니다.

처리 규칙은 다음과 같은 이점을 제공합니다.

* 앱스토어에 업데이트를 제출하지 않고 데이터 매핑을 변경할 수 있습니다.
* 보고서 세트에 고유한 변수를 설정하는 대신 데이터에 의미 있는 이름을 사용할 수 있습니다.
* 추가 데이터 전송에는 거의 영향을 주지 않습니다.

   이러한 값은 처리 규칙을 사용하여 매핑될 때까지 보고서에 표시되지 않습니다. 자세한 내용은 [처리 규칙 및 컨텍스트 데이터](/help/ios/getting-started/proc-rules.md)를 참조하십시오.

변수에 직접 할당한 값은 대신 `data``NSDictionary` 에 추가해야 합니다. 다시 말해서 `setProp`, `setEvar`에 대한 호출과 영구 컨텍스트 데이터에 대한 할당이 모두 제거되고 `data` 매개 변수에 값이 추가되어야 합니다.

### AppSection/서버, GeoZip, 트랜잭션 ID, 캠페인 및 기타 표준 변수

위에 나열된 변수를 포함하여 측정 개체에 설정한 데이터는 대신 `data``NSDictionary` 에 추가해야 합니다. `trackState` 또는 `trackAction` 호출과 함께 전송되는 데이터는 `data` 매개 변수의 페이로드뿐입니다.

### 추적 호출 대체

코드에서 다음 메서드를 `trackState` 또는 `trackAction` 호출로 바꿉니다.

#### 버전 3.x에서 마이그레이션

* `trackAppState (trackState)`
* `trackEvents (trackAction)`
* `track (trackAction)`
* `trackWithContextData (trackAction)`
* `trackLinkURL (trackAction)`

#### 버전 2.x에서 마이그레이션

* `track (trackState)`
* `trackLink (trackAction)`

## 사용자 지정 방문자 ID {#section_2CF930C13BA64F04959846E578B608F3}

`visitorID` 변수를 `setUserIdentifier:`에 대한 호출로 바꿉니다.

## 오프라인 추적 {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

오프라인 추적은 `ADBMobileConfig.json` 파일에서 활성화되고 다른 오프라인 구성은 모두 자동으로 수행됩니다.

코드에서 다음 메서드 호출을 제거하십시오.

### 버전 3.x

* `setOnline`
* `setOffline`

### 버전 2.x

* `forceOffline`
* `forceOnline`

## Products 변수 {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

 변수는 처리 규칙에서 사용할 수 없으므로 다음 구문을 사용하여 `products`products를 설정할 수 있습니다.

```objective-c
//create a processing rule to set the corresponding product event. 
// for example, set prodView event when context data a.action = "product view" 
[ADBMobile trackAction:@"LikeButtonClicked"  
                  data:@{@"&&products" : @";Cool Shoe"}];
```

![](assets/prod-view.png)
