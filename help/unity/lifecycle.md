---
description: 모바일 라이브러리에서 자동으로 측정할 수 있는 측정 지표 및 차원 측정
keywords: Unity
solution: Experience Cloud
title: 라이프사이클 구현
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
exl-id: eca0cebb-6c69-4b0f-b003-c7fc422d0383
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 7%

---

# 라이프사이클 구현{#implement-lifecycle}

라이프사이클이 구현된 후 모바일 라이브러리에서 자동으로 측정할 수 있는 지표 및 차원에 대한 자세한 내용은 Android](/help/android/metrics.md)의 [라이프사이클 지표 또는 iOS](/help/ios/metrics.md)의 [라이프사이클을 참조하십시오.

## iOS

라이프사이클 지표는 iOS에서 자동으로 수집됩니다.

## Android

Unity 스크립트에서 Android SDK용 애플리케이션 컨텍스트를 설정합니다. 첫 번째 장면의 `Awake()` 함수에 다음 코드를 추가합니다.

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
