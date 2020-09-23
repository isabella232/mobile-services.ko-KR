---
description: 'null'
seo-description: 'null'
seo-title: Analytics
solution: Experience Cloud,Analytics
title: Analytics
topic: Developer and implementation
uuid: c2cef3d3-77a7-4a8e-bbe4-3db10a77996a
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 11%

---


# Analytics {#analytics}

프로젝트에 라이브러리를 추가한 후 앱의 아무 곳에나 Analytics 메서드를 호출할 수 있습니다.

>[!TIP]
>
>클래스에 가져오기 `ADBMobile.h` 를 확인합니다.

## Analytics에서 모바일 애플리케이션 보고서 활성화 {#section_F2F9234009184F20BA36B5CDE872B424}

코드를 추가하기 전에 Analytics 관리자가 다음을 완료하여 모바일 앱 라이프사이클 추적을 활성화하도록 하십시오. 이렇게 하면 개발을 시작할 때 보고서 세트가 지표를 캡처할 준비가 됩니다.

1. 관리 **[!UICONTROL 도구]** > **[!UICONTROL 보고서 세트를]** 열고 모바일 보고서 세트를 선택합니다.

1. 설정 **[!UICONTROL 편집]** > **[!UICONTROL 모바일 관리]** > **[!UICONTROL 모바일 애플리케이션 보고]**&#x200B;를 클릭합니다.

   ![](assets/mobile-settings.png)

1. 최신 **[!UICONTROL 앱 보고서 활성화를 클릭합니다]**.

   원할 경우, 모바일 위치 추적 **[!UICONTROL 활성화]** 또는 **[!UICONTROL 백그라운드 히트에 대한 레거시 보고 및 속성 활성화를 클릭할 수도 있습니다]**.

   ![](assets/enable-lifecycle.png)

이제 라이프사이클 지표를 캡처할 준비가 되었으며, 모바일 애플리케이션 보고서가 마케팅 보고서 인터페이스의 **[!UICONTROL 보고서]** 메뉴에 나타납니다.

### 새로운 버전

모바일 애플리케이션 보고의 새로운 버전이 정기적으로 릴리스됩니다. 새 버전은 보고서 세트에 자동으로 적용되지 않으므로 업그레이드를 수행하려면 이러한 단계를 반복해야 합니다. 앱에 새 Experience Cloud 기능을 추가할 때마다 최신 구성을 유지하려면 이 단계를 반복하는 것이 좋습니다.

## 라이프사이클 지표 {#section_532702562A7A43809407C9A2CBA80E1E}

앱에서 라이프사이클 지표를 수집하려면 다음 예와 같이 애플리케이션이 활성화되면 호출을 추가합니다.

### default.js의 WinJS

```js
app.onactivated = function (args) { 
  if (args.detail.kind === activation.ActivationKind.launch) { 
   ... 
   // launched and resumed stuff  
   ADBMobile.Config.collectLifecycleData(); 
  } 
}; 
app.oncheckpoint = function (args) { 
  ADBMobile.Config.pauseCollectingLifecycleData(); 
}
```

### App.xaml.cs의 C#

```js
public App() 
{ 
    this.InitializeComponent(); 
    this.Resuming += OnResuming; 
    this.Suspending += OnSuspending; 
} 
protected override void OnLaunched(LaunchActivatedEventArgs e) 
{   ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnResuming(object sender, object e) 
{ 
    ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnSuspending(object sender, SuspendingEventArgs e) 
{ 
    ... 
    ADBMobile.Config.PauseCollectingLifecycleData(); 
    ... 
}
```

### App.xaml.cpp의 C++/CX

```js
App::App() 
{ 
 InitializeComponent(); 
 Resuming += ref new EventHandler<Object ^>(this, &App::OnResuming); 
 Suspending += ref new SuspendingEventHandler(this, &App::OnSuspending); 
} 
void App::OnResuming(Object ^sender, Object ^args) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
} 
void App::OnSuspending(Object^ sender, SuspendingEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::PauseCollectingLifecycleData(); 
 ... 
} 
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
}
```

동일한 세션 `CollectLifecycleData()` 에서 두 번 호출되면 첫 번째 호출 후 모든 호출에서 충돌이 보고됩니다. 애플리케이션이 종료될 때 SDK는 성공적으로 종료되었음을 나타내는 플래그를 설정합니다. 이 플래그가 설정되지 않은 경우 `CollectLifecyleData()` 충돌을 보고합니다.

## Event, Prop 및 eVar {#section_76EA6F5611184C5CAE6E62956D84D7B6}

SDK 방법을 살펴본 [](/help/universal-windows/c-configuration/methods.md)경우 이벤트, eVar, prop, 상속인 및 목록을 어디에 설정해야 하는지 궁금해 할 것입니다. 버전 4에서는 더 이상 앱에서 바로 이러한 유형의 변수를 할당할 수 없습니다. 대신, SDK는 컨텍스트 데이터 및 처리 규칙을 사용하여 보고를 위해 앱 데이터를 Analytics 변수에 매핑합니다.

처리 규칙은 다음과 같은 여러 이점을 제공합니다.

* App Store에 업데이트를 제출하지 않고 데이터 매핑을 변경할 수 있습니다.
* 보고서 세트에 고유한 변수를 설정하는 대신 데이터에 의미 있는 이름을 사용할 수 있습니다.
* 추가 데이터 전송에는 거의 영향을 주지 않습니다. 이러한 값은 처리 규칙을 사용하여 매핑될 때까지 보고서에 표시되지 않습니다.

변수에 직접 할당했던 모든 값을 컨텍스트 데이터에 추가해야 합니다.

## 처리 규칙 {#section_66EE762EEA5E4728864166201617DEBF}

처리 규칙은 컨텍스트 데이터 변수에서 전송한 데이터를 보고를 위해 evar, prop 및 기타 변수에 복사하는 데 사용됩니다.

[Summit 2013에서 처리 규칙](https://tv.adobe.com/embed/1181/16506/) 교육

[처리 규칙 도움말](https://docs.adobe.com/content/help/ko-KR/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[처리 규칙 사용 권한 부여](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

논리 순서를 유지하는 데 도움이 되므로 &quot;네임스페이스&quot;를 사용하여 컨텍스트 데이터 변수를 그룹화하는 것이 좋습니다. 예를 들어 제품에 대한 정보를 수집하려는 경우 다음 변수를 정의할 수 있습니다.

```javascript
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

컨텍스트 데이터 변수는 처리 규칙 인터페이스에서 알파벳순으로 정렬되므로 네임스페이스에 동일한 변수가 있는 것을 빠르게 볼 수 있습니다.

또한 일부 사용자가 evar 또는 prop 번호를 사용하여 컨텍스트 데이터 키의 이름을 지정한다는 소식을 들었습니다.

```js
"eVar1":"jimbo"
```

이 경우 처리 규칙에서 한 번 매핑을 수행할 때 *약간* 더 쉬워질 수 있지만 디버깅 및 향후 코드 업데이트 중에 가독성을 잃게 될 수 있습니다. 대신 키 및 값에 설명 이름을 사용하는 것이 좋습니다.

```js
"username":"jimbo"
```

카운터 이벤트를 정의하는 컨텍스트 변수를 &quot;1&quot; 값으로 설정합니다.

```js
"logon":"1"
```

상향 조정기 이벤트를 정의하는 컨텍스트 데이터 변수는 증가할 값을 가질 수 있습니다.

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe는 `a.` 네임스페이스를 예약합니다. 이러한 제한 사항 외에, 충돌을 방지하기 위해 컨텍스트 데이터 변수는 로그인 회사에서 고유해야 합니다.

## Products 변수 {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

모바일 SDK *`products`* 에서 설정하려면 특수 구문을 사용해야 합니다. 자세한 내용은 [제품 변수를 참조하십시오](/help/universal-windows/analytics/products.md).

## (선택 사항) 오프라인 추적 활성화 {#section_955B2A03EB854742BDFC4A0A3C287009}

장치가 오프라인 상태일 때 히트를 저장하려면 [SDK 메서드](/help/universal-windows/c-configuration/methods.md) 파일에서 오프라인 추적을 활성화할 수 있습니다. 오프라인 추적을 활성화하기 전에 구성 파일 참조에 설명된 타임스탬프 요구 사항에 주의하십시오.

## 지리적 위치 및 관심 영역 {#section_BAD34A8DD013454DB355121316BD7FD4}

지리적 위치를 사용하면 위치 데이터(위도/경도) 및 사전 정의된 관심 영역을 측정할 수 있습니다. 각 `TrackLocation` 호출은 다음을 전송합니다.

* 위도/경도 및 POI(구성 파일에 정의된 POI 내 `ADBMobileConfig.json` 의 경우).

   이러한 값은 자동 보고를 위해 모바일 솔루션 변수로 전달됩니다.

* 컨텍스트 데이터로 전달된 중앙으로부터의 거리 및 정확도

   처리 규칙을 사용하여 캡처합니다.

위치를 추적하려면

```js
var ADB = ADBMobile; 
ADB.Analytics.trackLocation(37.75345, -122.33207, null);
```

구성 파일에 다음 POI가 정의된 `ADBMobileConfig.json` 경우:

```js
"poi" : [ 
            ["San Francisco",37.757144,-122.44812,7000], 
        ]
```

장치 위치가 정의된 지점의 7000미터 반경 내에 있다고 판단되면, 값이 있는 `a.loc.poi` 컨텍스트 데이터 변수 `San Francisco` 가 `TrackLocation` 히트와 함께 전송됩니다. An `a.loc.dist` context variable is sent with the distance in meters from the defined coordinates.

## Lifetime value {#section_D2C6971545BA4D639FBE07F13EF08895}

라이프타임 값을 통해 각 사용자의 라이프타임 값을 측정하고 타깃팅할 수 있습니다. `TrackLifetimeValueIncrease`를 사용하여 값을 보낼 때마다 값이 기존 값에 추가됩니다. 라이프타임 값은 장치에 저장되며 `GetLifetimeValue`를 호출하여 언제든지 검색할 수 있습니다. 이 값은 라이프타임 구매, 광고 보기, 비디오 전체 보기, 소셜 네트워크 공유, 사진 업로드 등을 저장하는 데 사용할 수 있습니다.

```js
// Lifetime Value Example 
var ADB = ADBMobile; 
var purchasePrice = 39.95; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ItemPurchaseEvent"] = "ItemPurchaseEvent"; 
cdata["PurchaseItem"] = "Item453"; 
cdata["PurchasePrice"] = purchasePrice; 
ADB.Analytics.trackLifetimeValueIncrease(purchasePrice, cdata);
```

## 시간 작업 {#section_7FF8B6A913A0460EAA4CAE835E32D8C1}

시간 작업을 사용하면 작업의 시작과 끝 사이의 인앱 시간과 총 시간을 측정할 수 있습니다. SDK는 세션 시간과 작업을 완료하는 데 소요되는 총 시간(세션 간)을 계산합니다. 세그먼트를 정의하여 구매, 전달 수준, 체크아웃 흐름 등을 비교할 수 있습니다.

* 시작 및 종료 간 앱의 총 시간(초) - 세션 간
* 시작과 종료 사이의 총 시간(초)

```js
// Timed Action Start Example 
var ADB = ADBMobile; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ExperienceName"] = experience; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
```

```js
// Timed Action Update Example 
var ADB = ADBMobile; 
var cdataUpdate = new Windows.Foundation.Collections.PropertySet(); 
cdataUpdate["ImageLiked"] = imageName; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata); 
```

```js
// Timed Action End Example 
var ADB = ADBMobile; 
ADB.Analytics.trackTimedActionEnd("TimeUntilPurchase");
```
