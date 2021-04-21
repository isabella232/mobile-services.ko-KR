---
description: 프로젝트에 라이브러리를 추가하면 앱의 아무 곳에서나 Analytics 메서드를 호출할 수 있습니다.
solution: Experience Cloud,Analytics
title: Analytics
topic-fix: Developer and implementation
uuid: fa0ef6c4-c04d-4695-9eb4-ada4e9920e6c
exl-id: 1a7b32b8-731d-4ae3-9feb-dafbb7495590
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 20%

---

# Analytics {#analytics}

프로젝트에 라이브러리를 추가하면 앱의 아무 곳에서나 Analytics 메서드를 호출할 수 있습니다.

>[!TIP]
>
>`ADBMobile.h`을(를) 클래스에 가져왔는지 확인합니다.

## Analytics {#section_F2F9234009184F20BA36B5CDE872B424}에서 모바일 애플리케이션 보고서 활성화

코드를 추가하기 전에 Analytics 관리자가 다음을 완료하여 모바일 앱 라이프사이클 추적을 활성화하도록 하십시오. 이렇게 하면 개발을 시작할 때 보고서 세트가 지표를 캡처할 준비가 됩니다.

1. **[!UICONTROL 관리 도구]** > **[!UICONTROL 보고서 세트]**&#x200B;를 열고 모바일 보고서 세트를 선택합니다.
1. **[!UICONTROL 설정 편집]** > **[!UICONTROL 모바일 관리]** > **[!UICONTROL 모바일 애플리케이션 보고]**&#x200B;를 클릭합니다.

   ![](assets/mobile-settings.png)

1. **[!UICONTROL 최신 앱 보고서 활성화]**&#x200B;를 클릭합니다.

   원할 경우, **[!UICONTROL 모바일 위치 추적 활성화]** 및 **[!UICONTROL 백그라운드 히트에 대해 레거시 보고 및 속성 활성화를 클릭할 수도 있습니다]**.

   ![](assets/enable-lifecycle.png)

이제 라이프사이클 지표를 캡처할 준비가 되었으며 모바일 애플리케이션 보고서가 마케팅 보고서 인터페이스의 **[!UICONTROL 보고서]** 메뉴에 나타납니다.


### 새 버전

모바일 애플리케이션 보고의 새로운 버전이 정기적으로 릴리스됩니다. 새 버전은 보고서 세트에 자동으로 적용되지 않으므로 업그레이드를 수행하려면 이러한 단계를 반복해야 합니다. 앱에 새 Experience Cloud 기능을 추가할 때마다 최신 구성을 유지하려면 이 단계를 반복하는 것이 좋습니다.


## 라이프사이클 지표 {#section_532702562A7A43809407C9A2CBA80E1E}

앱에서 라이프사이클 지표를 수집하려면 다음 예와 같이 애플리케이션이 활성화될 때 호출을 추가합니다.


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
    this.Resuming *= OnResuming; 
    this.Suspending *= OnSuspending; 
} 
protected override void OnLaunched(LaunchActivatedEventArgs e) 
{ 
    ... 
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

### App.xaml.cpp의 C/CX

```js
App::App() 
{ 
 InitializeComponent(); 
 Resuming *= ref new EventHandler<Object ^>(this, &App::OnResuming); 
 Suspending *= ref new SuspendingEventHandler(this, &App::OnSuspending); 
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

동일한 세션에서 `CollectLifecycleData()`이 두 번 호출되면 첫 번째 호출 이후의 모든 호출에서 충돌이 보고됩니다. 애플리케이션이 종료되면 SDK에서 성공적으로 종료되었음을 나타내는 플래그를 설정합니다. 이 플래그가 설정되어 있지 않으면 `CollectLifecyleData()` 충돌이 보고됩니다.


## Event, Prop 및 eVar {#section_76EA6F5611184C5CAE6E62956D84D7B6}


[ADBMobile 클래스 및 메서드 참조](/help/windows-appstore/c-configuration/methods.md)를 본 경우 이벤트, eVars, prop, 상속인 및 목록을 어디에 설정해야 하는지 궁금해 할 것입니다. 버전 4에서는 더 이상 이러한 유형의 변수를 앱에서 바로 할당할 수 없습니다. 대신, SDK는 컨텍스트 데이터 및 처리 규칙을 사용하여 앱 데이터를 Analytics 변수에 매핑해서 보고에 사용합니다.

처리 규칙은 다음과 같은 여러 이점을 제공합니다.

* 앱스토어에 업데이트를 제출하지 않고 데이터 매핑을 변경할 수 있습니다.
* 보고서 세트에 고유한 변수를 설정하는 대신 데이터에 의미 있는 이름을 사용할 수 있습니다.
* 추가 데이터 전송에는 거의 영향을 주지 않습니다. 이러한 값은 처리 규칙을 사용하여 매핑되기 전까지는 보고서에 나타나지 않습니다.

변수에 직접 할당했던 모든 값을 컨텍스트 데이터에 추가해야 합니다.


## 처리 규칙 {#section_66EE762EEA5E4728864166201617DEBF}

처리 규칙은 컨텍스트 데이터 변수에서 데이터를 보고를 위해 evar, prop 및 기타 변수에 복사하는 데 사용됩니다.

[처리 규칙 교육](https://tv.adobe.com/embed/1181/16506/) @ Summit 2013

[처리 규칙 개요](https://docs.adobe.com/content/help/ko-KR/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[처리 규칙 사용 인증 받기](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

논리 순서를 유지하는 데 도움이 되므로 &quot;네임스페이스&quot;를 사용하여 컨텍스트 데이터 변수를 그룹화하는 것이 좋습니다. 예를 들어 제품에 대한 정보를 수집하려는 경우 다음 변수를 정의할 수 있습니다.

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

컨텍스트 데이터 변수는 처리 규칙 인터페이스에서 알파벳순으로 정렬되므로 네임스페이스를 통해 동일한 네임스페이스에 있는 변수를 빠르게 볼 수 있습니다.

또한 일부 사용자가 evar 또는 prop 번호를 사용하여 컨텍스트 데이터 키의 이름을 지정한다고 들었습니다.

```js
"eVar1":"jimbo"
```

이 경우 처리 규칙에서 한 번 매핑을 수행할 때 *약간*&#x200B;이 더 쉬워질 수 있지만, 디버깅 도중 가독성을 잃고 향후 코드 업데이트가 더 어려울 수 있습니다. 대신 키 및 값에 설명 이름을 사용하는 것이 좋습니다.

```js
"username":"jimbo"
```

카운터 이벤트를 정의하는 컨텍스트 변수를 &quot;1&quot; 값으로 설정합니다.

```js
"logon":"1"
```

incrementor 이벤트를 정의하는 컨텍스트 데이터 변수는 증가할 값을 가질 수 있습니다.

```js
"levels completed":"6"
```

>[!NOTE]
>
>Adobe는 `a.` 네임스페이스를 예약합니다. 이러한 사소한 제한 사항 외에도 충돌을 방지하기 위해 컨텍스트 데이터 변수는 로그인 회사에서 고유해야 합니다.

## Products 변수 {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

모바일 SDK에서 *`products`*&#x200B;을(를) 설정하려면 특수 구문을 사용해야 합니다. [제품 변수](/help/windows-appstore/analytics/products/products.md)를 참조하십시오.

## (선택 사항) 오프라인 추적 사용 {#section_955B2A03EB854742BDFC4A0A3C287009}

장치가 오프라인 상태일 때 히트를 저장하려면 [ADBMobileConfig.json 구성](/help/windows-appstore/c-configuration/methods.md)에서 오프라인 추적을 활성화할 수 있습니다. 오프라인 추적을 활성화하기 전에 구성 파일 참조에 설명된 타임스탬프 요구 사항에 주의하십시오.

## 지리적 위치 및 관심 영역 {#section_BAD34A8DD013454DB355121316BD7FD4}

지리적 위치를 사용하면 위치 데이터(위도/경도) 및 사전 정의된 관심 영역을 측정할 수 있습니다. 각 `TrackLocation` 호출은 다음을 전송합니다.

* 위도/경도 및 POI(`ADBMobileConfig.json` 구성 파일에 정의된 POI 내의 경우). 이러한 데이터는 자동 보고를 위해 모바일 솔루션 변수로 전달됩니다.
* 컨텍스트 데이터로 전달된 가운데 및 정확도와의 거리. 처리 규칙을 사용하여 캡처합니다.

위치를 추적하려면:

```js
var ADB = ADBMobile; 
ADB.Analytics.trackLocation(37.75345, -122.33207, null);
```

다음 POI가 `ADBMobileConfig.json` 구성 파일에 정의된 경우:

```js
"poi" : [ 
            ["San Francisco",37.757144,-122.44812,7000], 
        ]
```

장치 위치가 정의된 지점의 반경 7000m 내에 있다고 판단되면 &quot;San Francisco&quot; 값을 가진 `a.loc.poi` 컨텍스트 데이터 변수가 `TrackLocation` 히트와 함께 전송됩니다. `a.loc.dist` 컨텍스트 변수는 정의된 좌표로부터 미터 단위로 전송됩니다.

## 라이프타임 값 {#section_D2C6971545BA4D639FBE07F13EF08895}

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

시간 작업을 사용하면 작업의 시작과 끝 사이의 인앱 시간과 총 시간을 측정할 수 있습니다. SDK는 세션 중의 시간과 작업을 완료하는 데 소요되는 총 시간(세션 간)을 계산합니다. 세그먼트를 정의하여 구매, 전달 수준, 체크아웃 흐름 등을 적시에 비교할 수 있습니다.

* 시작 및 종료 사이의 앱의 총 시간(초) - 세션 간
* 시작과 종료 사이의 총 시간(초)(시계 시간)

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
