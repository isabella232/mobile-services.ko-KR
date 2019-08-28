---
description: 애플리케이션이 시작될 때 다른 ADBMobile JSON 구성 파일을 로드할 수 있습니다.
seo-description: 애플리케이션이 시작될 때 다른 ADBMobile JSON 구성 파일을 로드할 수 있습니다.
seo-title: ADBMobile JSON 구성 경로 재정의
solution: Marketing Cloud, Analytics
title: ADBMobile JSON 구성 경로 재정의
topic: 개발자 및 구현
uuid: 6872 a 5 d 7-0 c 5 a -4 fdc-b 7 bf-ad 1534763 a 6 a
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

애플리케이션이 시작될 때 다른 ADBMobile JSON 구성 파일을 로드할 수 있습니다.

`Config.overrideConfigStream(configInput)` 이 방법을 사용하면 응용 프로그램이 시작될 때 다른 `ADBMobile.json` 구성 파일의 경로를 지정할 수 있습니다. This method must be called before any other Experience Cloud SDK call (before `Config.collectLifecycleData()` ), typically in the `onCreate` method of your first loaded activity.

다른 경로를 사용하여 이 메서드를 호출하면 애플리케이션이 닫힐 때까지 구성 파일이 한 번 재정의됩니다.

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```

