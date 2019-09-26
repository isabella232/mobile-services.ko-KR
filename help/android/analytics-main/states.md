---
description: 상태는 애플리케이션의 다양한 화면 또는 보기입니다.
seo-description: 상태는 애플리케이션의 다양한 화면 또는 보기입니다.
seo-title: 앱 상태 추적
solution: Marketing Cloud,Analytics
title: 앱 상태 추적
topic: 개발자 및 구현
uuid: 69c99d05-5816-4c86-97c5-d218dc26c129
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# 앱 상태 추적 {#track-app-states}

상태는 애플리케이션의 다양한 화면 또는 보기입니다.

새로운 상태가 애플리케이션에 표시될 때마다(예: 사용자가 홈페이지에서 뉴스피드로 이동할 때) `trackState` 호출이 전송됩니다. Android에서 `trackState`는 일반적으로 새 활동이 로드될 때마다 호출됩니다.

## Tracking states {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 코어 *구현 및 라이프사이클에서 IntelliJ IDEA 또는 Eclipse 프로젝트에* SDK 및 구성 파일 [추가를 참조하십시오](/help/android/getting-started/dev-qs.md).

1. 라이브러리를 가져옵니다:

   ```java
   import com.adobe.mobile.*;
   ```

1. `onCreate` 함수에서 `trackState`를 호출하여 이 상태 보기에 대한 히트를 보냅니다.

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Adobe - track when this state loads 
       Analytics.trackState("State Name", null); 
   }
   ```

The `"State Name"` is reported in the `View State` variable in Adobe Mobile services, and a view is recorded for each `trackState` call. 다른 Analytics 인터페이스에서는 `View State` 로 보고되며 `Page Name`로 `state views` 보고됩니다 `page views`.

## Send additional data {#section_CFDB4F944496401786A145C209AB387C}

In addition to the `"State Name"`, you can send additional context data with each track action call:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
    super.onCreate(savedInstanceState); 
    setContentView(R.layout.main); 
  
    // Adobe - track when this state loads 
    HashMap<String, Object> exampleContextData = new HashMap<String, Object>(); 
    exampleContextData.put("myapp.login.LoginStatus", "logged in"); 
    Analytics.trackState("Home Screen", exampleContextData); 
}
```

컨텍스트 데이터 값은 Adobe Mobile Services에서 사용자 지정 변수에 매핑되어야 합니다.

![](assets/map-variable-context-state.png)

## App state reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

상태는 일반적으로 경로 지정 보고서를 사용하여 표시되므로 사용자가 앱을 이동하는 방법과 가장 자주 본 상태를 볼 수 있습니다.

|  |  |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL 상태 보기]보고서.** 이 보고서는 사용자가 애플리케이션을 통해 가져온 경로를 기반으로 합니다. A sample path is  **[!UICONTROL Home]**  &gt;  **[!UICONTROL Settings]**  &gt; **[!UICONTROL Feed]**. |
| Adobe Analytics | 상태는 **페이지** 보고서, **[!UICONTROL 페이지 보기]** 보고서 및 **경로[!UICONTROL 보고서와 같이 페이지를 볼 수 있는 모든 위치에서 볼 수 있습니다 .]** |
| Ad hoc analytics | 상태는 **페이지** 차원, **[!UICONTROL 페이지 보기 횟수]** 지표 및 **경로[!UICONTROL 보고서를 사용하여 페이지를 볼 수 있는 모든 위치에서 볼 수 있습니다.]** |


