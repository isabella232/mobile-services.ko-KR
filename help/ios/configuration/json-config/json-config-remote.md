---
description: 애플리케이션이 시작될 때 다른 ADBMobile JSON 구성 파일을 로드할 수 있습니다.
seo-description: 애플리케이션이 시작될 때 다른 ADBMobile JSON 구성 파일을 로드할 수 있습니다.
seo-title: Adbmobile JSON 구성 경로 재정의
solution: Marketing Cloud, Analytics
title: Adbmobile JSON 구성 경로 재정의
topic: 개발자 및 구현
uuid: 0 D 1 BE 674-C 634-4 A 48-AA 31-5701681911 B 9
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

애플리케이션이 시작될 때 다른 ADBMobile JSON 구성 파일을 로드할 수 있습니다.

`ADBMobile overrideConfigPath:filePath` 이 방법을 사용하면 응용 프로그램이 시작될 때 다른 `ADBMobile.json` 구성 파일의 경로를 지정할 수 있습니다. 이 메서드는 `applicationDidFinishLaunchingWithOptions` 메서드에서 호출해야 하며, 이 호출은 `collectLifecycleData`와 같은 다른 Experience Cloud SDK 호출 전에 수행해야 합니다.

다른 경로로 이 메서드를 호출하면 응용 프로그램이 닫힐 때까지 구성 파일의 일회성 재정의가 발생합니다.

예:

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```

