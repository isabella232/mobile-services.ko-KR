---
description: 작업은 측정할 Android 앱에서 발생하는 이벤트입니다.
seo-description: 작업은 측정할 Android 앱에서 발생하는 이벤트입니다.
seo-title: 앱 작업 추적
solution: Marketing Cloud,Analytics
title: 앱 작업 추적
topic: 개발자 및 구현
uuid: fe01c1df-f6bb-4b32-b3ef-959d2c724af6
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# 앱 작업 추적 {#track-app-actions}

작업은 측정할 Android 앱에서 발생하는 이벤트입니다.

각 작업에는 이벤트가 발생할 때마다 늘어나는 하나 이상의 해당 지표가 있습니다. 예를 들어 문서를 볼 때마다 또는 수준이 완료될 때마다 각각의 새 가입에 대한 `trackAction` 호출을 보낼 수 있습니다. 작업이 자동으로 추적되지 않으므로 추적하려는 이벤트가 발생할 때 `trackAction`을 호출한 다음 사용자 지정 이벤트에 해당 작업을 매핑해야 합니다.

## Tracking actions {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 코어 *구현 및 라이프사이클에서 IntelliJ IDEA 또는 Eclipse 프로젝트에* SDK 및 구성 파일 [추가를 참조하십시오](/help/android/getting-started/dev-qs.md).

1. 라이브러리를 가져옵니다:

   ```java
   import com.adobe.mobile.*;
   ```

1. 추적하려는 작업이 앱에서 발생하면 `trackAction`을 호출하여 이 작업에 대한 히트를 보냅니다:

   ```java
   Analytics.trackAction("myapp.ActionName", null);
   ```

1. Adobe Mobile Services UI에서 앱을 선택하고 **[!UICONTROL 앱 설정 관리를 클릭합니다]**.
1. **[!UICONTROL 변수 및 지표 관리]**&#x200B;를 클릭하고 **사용자 지정 지표[!UICONTROL 탭을 클릭합니다.]**

1. 코드에 정의된 컨텍스트 데이터 이름(예: `myapp.ActionName`)을 사용자 지정 이벤트에 매핑합니다.

   ![](assets/map-event-context-data.png)

You can also set a prop to hold all action values by mapping a custom prop with a name like **[!UICONTROL Custom Actions]** and setting the value to `a.action`.

![](assets/map-custom-prop.png)

## Sending additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

작업 이름 외에도 각 작업 추적 호출로 추가 컨텍스트 데이터를 전송할 수 있습니다.

```java
HashMap<String, Object> exampleContextData = new HashMap<String, Object>(); 
exampleContextData.put("myapp.social.SocialSource", "Twitter"); 
Analytics.trackAction("myapp.SocialShare", exampleContextData);
```

컨텍스트 데이터 값은 Adobe Mobile Services에서 사용자 지정 변수에 매핑되어야 합니다.

![](assets/map-variable-context-action.png)

## Action reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

| 인터페이스 | 보고서 |
|--- |--- |
| Adobe Mobile Services | ****&#x200B;작업 경로 보고서.  앱에서 작업이 발생하는 순서를 봅니다. 보고서에서 **[!UICONTROL 사용자 지정]을 클릭하여 등급이 매겨지거나, 트렌드가 분석되거나, 분류 보고서에 있는 작업을 보거나, 필터 적용을 통해 특정 세그먼트에 대한 작업을 볼 수도 있습니다.** |
| Marketing Reports &amp; Analytics | **[!UICONTROL 사용자 지정 이벤트]**&#x200B;를 보고합니다.  작업이 사용자 지정 이벤트에 매핑되면 다른 모든 Analytics 이벤트와 유사한 모바일 이벤트를 볼 수 있습니다. |
| Ad hoc analytics | **[!UICONTROL 사용자 지정 이벤트]**&#x200B;를 보고합니다.  작업이 사용자 지정 이벤트에 매핑되면 다른 모든 Analytics 이벤트와 유사한 모바일 이벤트를 볼 수 있습니다. |

