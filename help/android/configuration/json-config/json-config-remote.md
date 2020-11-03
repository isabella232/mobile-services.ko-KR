---
description: 애플리케이션이 시작될 때 다른 ADBMobile JSON 구성 파일을 로드할 수 있습니다.
seo-description: 애플리케이션이 시작될 때 다른 ADBMobile JSON 구성 파일을 로드할 수 있습니다.
seo-title: ADBMobile JSON 구성 경로 재정의
solution: Experience Cloud,Analytics
title: ADBMobile JSON 구성 경로 재정의
topic: Developer and implementation
uuid: 6872a5d7-0c5a-4fdc-b7bf-ad1534763a6a
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '116'
ht-degree: 100%

---


# ADBMobile JSON 구성 경로 재정의 {#override-the-adbmobile-json-config-path}

애플리케이션이 시작될 때 다른 ADBMobile JSON 구성 파일을 로드할 수 있습니다.

`Config.overrideConfigStream(configInput)` 메서드를 사용하면 애플리케이션이 시작될 때 경로를 다른 `ADBMobile.json` 구성 파일로 지정할 수 있습니다. 이 메서드는 일반적으로 첫 번째로 로드된 활동의 `onCreate` 메서드에서 다른 Experience Cloud SDK 호출보다 먼저(`Config.collectLifecycleData()` 전에) 호출해야 합니다.

다른 경로를 사용하여 이 메서드를 호출하면 애플리케이션이 닫힐 때까지 구성 파일이 한 번 재정의됩니다.

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```

