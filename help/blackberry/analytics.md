---
description: 프로젝트에 라이브러리를 추가한 후 앱의 아무 곳이나 Analytics 메서드 호출(ADBMobile.h를 클래스에 가져와야 함)을 할 수 있습니다.
seo-description: 프로젝트에 라이브러리를 추가한 후 앱의 아무 곳이나 Analytics 메서드 호출(ADBMobile.h를 클래스에 가져와야 함)을 할 수 있습니다.
seo-title: Analytics
title: Analytics
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 5%

---


# Analytics {#analytics}

프로젝트에 라이브러리를 추가한 후 앱의 아무 곳이나 Analytics 메서드 호출(ADBMobile.h를 클래스에 가져와야 함)을 할 수 있습니다.

## Analytics에서 모바일 애플리케이션 보고서 활성화 {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

코드를 추가하기 전에 Analytics 관리자가 다음을 완료하여 모바일 앱 라이프사이클 추적을 활성화하도록 하십시오. 이렇게 하면 개발을 시작할 때 보고서 세트가 지표를 캡처할 준비가 됩니다.


1. 관리 **[!UICONTROL 도구]** > **[!UICONTROL 보고서 세트를]** 열고 모바일 보고서 세트를 선택합니다.
1. 설정 **[!UICONTROL 편집]** > **[!UICONTROL 모바일 관리]** > **[!UICONTROL 모바일 애플리케이션 보고]**&#x200B;를 클릭합니다.

   ![](assets/mobile-settings.png)

1. 최신 **[!UICONTROL 앱 보고서 활성화를 클릭합니다]**.

   원할 경우, 모바일 위치 추적 **[!UICONTROL 활성화]** 및 **[!UICONTROL 백그라운드 히트에 대한 레거시 보고 및 속성 활성화를 클릭할 수도 있습니다]**.

   ![](assets/enable-lifecycle.png)

이제 라이프사이클 지표를 캡처할 준비가 되었으며, 모바일 애플리케이션 보고서가 마케팅 보고서 인터페이스의 **[!UICONTROL 보고서]** 메뉴에 나타납니다.

## 라이프사이클 지표 수집 {#task_25D469C62DF84573AEB5E8E950B96205}

1. 앱에서 라이프사이클 지표를 수집하려면 생성자 `collectLifecycleData()` 에서 `ApplicationUI` 호출합니다.

   예:

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   동일한 세션 `collectLifecycleData()` 에서 두 번 호출되면 첫 번째 호출 후 모든 호출에서 충돌이 보고됩니다. 애플리케이션이 종료될 때 SDK는 성공적으로 종료되었음을 나타내는 플래그를 설정합니다. 이 플래그가 설정되지 않은 경우 `collectLifecyleData()` 충돌을 보고합니다.

## Event, Prop 및 eVar {#concept_B885D5A71A5D45129CE7C1C3426A7D28}


ADBMobile 클래스 및 [메서드 참조를](/help/blackberry/methods.md)살펴본 경우 이벤트, eVar, prop, 상속인 및 목록을 어디에 설정할지 궁금할 것입니다. 버전 4에서는 더 이상 앱에서 바로 이러한 유형의 변수를 할당할 수 없습니다. 대신, SDK는 컨텍스트 데이터 및 처리 규칙을 사용하여 보고를 위해 앱 데이터를 Analytics 변수에 매핑합니다.

처리 규칙은 다음과 같은 여러 이점을 제공합니다.

* App Store에 업데이트를 제출하지 않고 데이터 매핑을 변경할 수 있습니다.
* 보고서 세트에 고유한 변수를 설정하는 대신 데이터에 의미 있는 이름을 사용할 수 있습니다.
* 추가 데이터 전송에는 거의 영향을 주지 않습니다. 이러한 값은 처리 규칙을 사용하여 매핑되기 전까지는 보고서에 표시되지 않습니다.

Any values that you were assigning directly to variables should be added to the `data` HashMap instead.

## 처리 규칙 {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

처리 규칙은 컨텍스트 데이터 변수에서 전송한 데이터를 보고를 위해 evar, prop 및 기타 변수에 복사하는 데 사용됩니다.

[Summit 2013에서 처리 규칙](https://tv.adobe.com/embed/1181/16506/) 교육

[처리 규칙](https://docs.adobe.com/content/help/ko-KR/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[처리 규칙 사용 인증 받기](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

논리 순서를 유지하는 데 도움이 되므로 &quot;네임스페이스&quot;를 사용하여 컨텍스트 데이터 변수를 그룹화하는 것이 좋습니다. 예를 들어 제품에 대한 정보를 수집하려는 경우 다음 변수를 정의할 수 있습니다.

```js
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

카운터 이벤트를 정의하는 컨텍스트 변수는 동일한 키와 값을 가질 수 있습니다.

```js
"logon":"logon"
```

incrementor 이벤트를 정의하는 컨텍스트 데이터 변수에는 이벤트가 키로 사용되고 값이 값으로 증가할 수 있습니다.

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe는 `a.` 네임스페이스를 예약합니다. 이러한 작은 제한 사항 외에도 충돌을 방지하기 위해 컨텍스트 데이터 변수는 로그인 회사에서 고유해야 합니다.

## 오프라인 추적 사용 {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

장치가 오프라인 상태일 때 히트를 저장하려면 선택적으로 `ADBMobileConfig.json` 파일에서 오프라인 추적을 활성화할 수 있습니다.

오프라인 추적을 활성화하기 전에 구성 파일 참조에 설명된 타임스탬프 요구 사항에 주의하십시오.

## Analytics 메서드

BlackBerry에 사용할 수 있는 Analytics 메서드 목록은 *Adobe 모바일 클래스 및 메서드 참조에서* Analytics 메서드 [를 참조하십시오](/help/blackberry/methods.md).