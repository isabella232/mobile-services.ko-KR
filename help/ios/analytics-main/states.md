---
description: '상태는 애플리케이션의 다양한 화면 또는 보기입니다. 새로운 상태가 애플리케이션에 표시될 때마다(예: 사용자가 홈페이지에서 뉴스피드로 이동할 때) 상태 추적 호출이 전송됩니다. iOS에서 상태는 일반적으로 각 보기의 viewDidLoad 메서드에서 추적합니다.'
seo-description: '상태는 애플리케이션의 다양한 화면 또는 보기입니다. 새로운 상태가 애플리케이션에 표시될 때마다(예: 사용자가 홈페이지에서 뉴스피드로 이동할 때) 상태 추적 호출이 전송됩니다. iOS에서 상태는 일반적으로 각 보기의 viewDidLoad 메서드에서 추적합니다.'
seo-title: 앱 상태 추적
solution: Experience Cloud,Analytics
title: 앱 상태 추적
topic: Developer and implementation
uuid: 12cca4eb-1f15-4cec-a58f-76b69eaff99d
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '397'
ht-degree: 100%

---


# 앱 상태 추적 {#track-app-states}

상태는 애플리케이션의 다양한 화면 또는 보기입니다. 새로운 상태가 애플리케이션에 표시될 때마다(예: 사용자가 홈페이지에서 뉴스피드로 이동할 때) 상태 추적 호출이 전송됩니다. iOS에서 상태는 일반적으로 각 보기의 viewDidLoad 메서드에서 추적합니다.

>[!TIP]
>
>상태를 추적하려면 `trackState`를 호출하십시오. 상태는 자동으로 추적되지 않습니다.

## 추적 상태 {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 [핵심 구현 및 라이프사이클](/help/ios/getting-started/dev-qs.md)에서 *프로젝트에 SDK 및 구성 파일 추가*&#x200B;를 참조하십시오.
1. 라이브러리를 가져옵니다.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. `trackState`를 호출하여 이 상태 보기에 대한 히트를 보냅니다.

   ```objective-c
   [ADBMobile trackState:@"Login Screen"  
                    data:nil];
   ```

Adobe Mobile Services에서 **[!UICONTROL 상태 이름]**&#x200B;은 *`View State`* 변수에 보고되며, 각 `trackState` 호출에 대한 보기가 기록됩니다. 다른 분석 인터페이스에서 **[!UICONTROL 상태 보기]**&#x200B;는 **[!UICONTROL 페이지 이름]**&#x200B;으로 보고되며, 상태 보기는 페이지 보기 횟수로 보고됩니다.

## 추가 데이터 보내기 {#section_CFDB4F944496401786A145C209AB387C}

**[!UICONTROL 상태 이름]** 외에도 각 추적 작업 호출로 추가 컨텍스트 데이터를 보낼 수 있습니다.

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"logged in" forKey:@"myapp.login.LoginStatus"]; 
[ADBMobile trackState:@"Home Screen" data:contextData];
```

컨텍스트 데이터 사용자 지정 변수에 매핑해야 합니다.

![](assets/map-variable-context-state.png)

## 앱 상태 보고 {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

상태는 일반적으로 경로 지정 보고서를 사용하여 표시되므로 사용자가 앱을 이동하는 방법과 가장 많이 본 상태를 확인할 수 있습니다.

|  |  |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL 상태 보기]** 보고서. 이 보고서는 사용자가 애플리케이션을 통해 가져온 경로를 기반으로 합니다. 샘플 경로는 **[!UICONTROL 홈]** > **[!UICONTROL 설정]** > **[!UICONTROL 피드]**&#x200B;입니다. |
| Adobe Analytics | 상태는 **[!UICONTROL 페이지]** 보고서, **[!UICONTROL 페이지 보기]** 보고서 및 **[!UICONTROL 경로 보고서와 같이 페이지를 볼 수 있는 모든 위치에서 볼 수 있습니다 .]** |
| Ad hoc analytics | 상태는 **[!UICONTROL 페이지]** 차원, **[!UICONTROL 페이지 보기 횟수]** 지표 및 **[!UICONTROL 경로 보고서를 사용하여 페이지를 볼 수 있는 모든 위치에서 볼 수 있습니다.]** |
