---
description: 라이브러리를 프로젝트에 추가한 후에는 앱의 모든 위치에서 Analytics 메서드를 호출할 수 있습니다(ADBMobile.h를 클래스로 가져와야 함).
seo-description: 라이브러리를 프로젝트에 추가한 후에는 앱의 모든 위치에서 Analytics 메서드를 호출할 수 있습니다(ADBMobile.h를 클래스로 가져와야 함).
seo-title: Analytics
title: Analytics
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics {#analytics}

라이브러리를 프로젝트에 추가한 후에는 앱의 모든 위치에서 Analytics 메서드를 호출할 수 있습니다(ADBMobile.h를 클래스로 가져와야 함).

## Enable mobile application reports in Analytics {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

코드를 추가하기 전에, 모바일 앱 라이프사이클 추적을 사용하도록 설정하려면 Analytics 관리자가 다음을 완료하도록 하십시오. 이렇게 하면 개발을 시작할 때 보고서 세트가 메트릭을 캡처할 준비를 합니다.


1. Open **[!UICONTROL Admin Tools]** &gt; **[!UICONTROL Report Suites]** and select your mobile report suite(s).
1. Click **[!UICONTROL Edit Settings]** &gt; **[!UICONTROL Mobile Management]** &gt; **[!UICONTROL Mobile Application Reporting]**.

   ![](assets/mobile-settings.png)

1. **[!UICONTROL 최신 앱 보고서 사용을 클릭합니다]**.

   Optionally, you can also click **[!UICONTROL Enable Mobile Location Tracking]** and **[!UICONTROL Enable Legacy Reporting and Attribution for background hits]**.

   ![](assets/enable-lifecycle.png)

Lifecycle metrics are now ready to be captured, and Mobile Application Reports] appear in the **[!UICONTROL Reports]** menu in the marketing reports interface.

## 라이프사이클 지표 수집 {#task_25D469C62DF84573AEB5E8E950B96205}

1. To collect lifecycle metrics in your app, call `collectLifecycleData()` in the `ApplicationUI` constructor.

   예:

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   If `collectLifecycleData()` is called twice in the same session, then your application will report a crash on every call after the first. SDK는 애플리케이션이 성공적으로 종료되었을 때 플래그를 설정합니다. If this flag is not set, `collectLifecyleData()` reports a crash.

## Events, props, and eVars {#concept_B885D5A71A5D45129CE7C1C3426A7D28}


ADBMobile 클래스 및 [메서드 참조를](/help/blackberry/methods.md)살펴본 경우 이벤트, eVar, prop, 상속인 및 목록을 어디에 설정해야 하는지 궁금해 할 수 있습니다. 버전 4에서는 더 이상 이러한 유형의 변수를 앱에서 직접 할당할 수 없습니다. 대신 SDK는 컨텍스트 데이터 및 처리 규칙을 사용하여 Analytics 변수에 앱 데이터를 매핑하여 보고합니다.

처리 규칙은 몇 가지 장점을 제공합니다.

* 앱 스토어에 업데이트를 제출하지 않고도 데이터 매핑을 변경할 수 있습니다.
* 보고서 세트와 관련된 변수를 설정하는 대신 의미 있는 이름을 데이터에 사용할 수 있습니다.
* 추가 데이터를 보내는 작업에는 거의 영향을 미치지 않습니다. 이러한 값은 처리 규칙을 사용하여 매핑될 때까지 보고서에 표시되지 않습니다.

변수에 직접 할당한 값은 대신 `data` HashMap에 추가해야 합니다.

## 처리 규칙 {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

처리 규칙은 컨텍스트 데이터 변수로 보내는 데이터를 보고용으로 evar, prop 및 기타 변수에 복사하는 데 사용됩니다.

[처리 규칙 교육](https://tv.adobe.com/embed/1181/16506/)(Summit 2013)

[처리 규칙](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[처리 규칙 사용 권한 부여](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

'네임스페이스'를 사용하여 컨텍스트 데이터 변수를 그룹화하십시오. 이렇게 하면 논리적 순서를 유지할 수 있습니다. 예를 들어 제품에 대한 정보를 수집할 경우 다음 변수를 정의할 수 있습니다.

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

컨텍스트 데이터 변수는 처리 규칙 인터페이스에서 알파벳순으로 정렬되어 동일한 네임스페이스에 있는 변수를 빠르게 확인할 수 있습니다.

컨텍스트 데이터 키의 이름을 지정할 경우 evar 또는 prop 번호를 사용하지 마십시오.

```js
"eVar1":"jimbo"
```

이렇게 하면 처리 규칙에서 일회 매핑을 수행할 때 *약간* 간편해질 수 있지만 디버깅 및 향후 코드 업데이트에서는 가독성이 떨어져 더 어려워질 수 있습니다. 대신 키와 값에 대한 설명이 포함된 이름을 사용하는 것이 좋습니다.

```js
"username":"jimbo"
```

카운터 이벤트를 정의하는 컨텍스트 변수는 동일한 키 및 값을 가질 수 있습니다.

```js
"logon":"logon"
```

상향 이벤트를 정의하는 컨텍스트 데이터 변수는 이벤트를 키로, 상향할 값을 값으로 설정할 수 있습니다.

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe는 네임스페이스를 보유합니다 `a.`. 이러한 사소한 제한 사항 외에도 충돌을 방지하기 위해 컨텍스트 데이터 변수는 로그인 회사에서 고유해야 합니다.

## 오프라인 추적 사용 {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

To store hits when the device is offline, you can optionally enable offline tracking in the `ADBMobileConfig.json` file.

오프라인 추적을 사용하기 전에 구성 파일 참조에 설명된 타임스탬프 요구 사항에 주의하십시오. 

## 분석 방법

BlackBerry에 사용할 수 있는 Analytics 메서드 목록은 Adobe Mobile *클래스* 및 메서드 [참조의 Analytics 메서드를 참조하십시오](/help/blackberry/methods.md).