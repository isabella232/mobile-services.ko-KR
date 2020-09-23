---
description: 애플리케이션이 시작될 때 다른 ADBMobile JSON 구성 파일을 로드할 수 있습니다.
seo-description: 애플리케이션이 시작될 때 다른 ADBMobile JSON 구성 파일을 로드할 수 있습니다.
seo-title: ADBMobile JSON 구성 경로 재정의
solution: Experience Cloud,Analytics
title: ADBMobile JSON 구성 경로 재정의
topic: Developer and implementation
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 100%

---


# ADBMobile JSON 구성 경로 재정의 {#override-the-adbmobile-json-config-path}

애플리케이션이 시작될 때 다른 ADBMobile JSON 구성 파일을 로드할 수 있습니다.

`ADBMobile overrideConfigPath:filePath` 메서드를 사용하면 애플리케이션이 시작될 때 경로를 다른 `ADBMobile.json` 구성 파일로 지정할 수 있습니다. 이 메서드는 `applicationDidFinishLaunchingWithOptions` 메서드에서 호출해야 하며, 이 호출은 `collectLifecycleData`와 같은 다른 Experience Cloud SDK 호출 전에 수행해야 합니다.

다른 경로를 사용하여 이 메서드를 호출하면 애플리케이션이 닫힐 때까지 구성 파일이 한 번 재정의됩니다.

예:

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```

