---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: 라이프사이클 구현
solution: Marketing Cloud, 개발자
title: 라이프사이클 구현
uuid: 7 FF 2 C 194-569 C -42 A 6-922 D-DCCD 2 AA 9 EB 8 D
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# 라이프사이클 구현{#implement-lifecycle}

라이프사이클이 구현된 후 모바일 라이브러리에서 자동으로 측정할 수 있는 지표와 차원에 대한 자세한 내용은 iOS의 [라이프사이클 지표](/help/android/metrics.md) 또는 iOS [의 라이프사이클을 참조하십시오](/help/ios/metrics.md).

## iOS

라이프사이클 지표는 iOS에서 자동으로 수집됩니다.

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

