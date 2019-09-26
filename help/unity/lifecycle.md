---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: 라이프사이클 구현
solution: Marketing Cloud,Developer
title: 라이프사이클 구현
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# 라이프사이클 구현{#implement-lifecycle}

For more information about the metrics and dimensions that can be measured automatically by the mobile library after lifecycle is implemented, see Lifecycle Metrics in Android or Lifecycle in iOS.[](/help/android/metrics.md)[](/help/ios/metrics.md)

## iOS

Lifecycle metrics are automatically collected in iOS.

## Android

Unity 스크립트에서 Android SDK용 애플리케이션 컨텍스트를 설정합니다. Add the following code to the `Awake()` function of your FIRST scene:

```java
void Awake()
 {
  ...
  ADBMobile.SetContext();
  ...
 }
```

라이프사이클 지표를 수집하려면 모든 장면 스크립트에 다음 코드를 추가합니다.

```java
void OnEnable()
 {
  ...
  ADBMobile.CollectLifecycleData (); 
  ...
 }
 
 void OnDisable()
 {
  ...
  ADBMobile.PauseCollectingLifecycleData (); 
  ...
 }
  
 void OnApplicationPause(bool isPaused) 
 {
  ...
  if (isPaused) {
   ADBMobile.PauseCollectingLifecycleData (); 
  }  
  else {
   ADBMobile.CollectLifecycleData(); 
  }
  ...
 }
```

