---
description: Android용 라이프사이클 지표를 구현하는 데 도움이 되는 정보입니다. 라이프사이클 지표는 iOS에 대해 자동으로 수집됩니다.
keywords: Xamarin
seo-description: Android용 라이프사이클 지표를 구현하는 데 도움이 되는 정보입니다. 라이프사이클 지표는 iOS에 대해 자동으로 수집됩니다.
seo-title: 라이프사이클 구현
solution: Experience Cloud
title: 라이프사이클 구현
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 7%

---


# 라이프사이클 구현 {#implement-lifecycle}

이 정보는 Android용 라이프사이클 지표를 구현하는 데 도움이 됩니다.

>[!TIP]
>
>라이프사이클 지표는 iOS에 대해 자동으로 수집됩니다.

라이프사이클이 구현된 후 모바일 라이브러리에서 자동으로 측정할 수 있는 지표와 차원은 라이프사이클 지표 [를 참조하십시오](/help/ios/metrics.md).

## iOS

iOS에서는 라이프사이클 지표가 자동으로 수집됩니다.

## Android

기본 활동에서 Android SDK용 애플리케이션 컨텍스트를 설정합니다.

```java
protected override void OnCreate (Bundle bundle) 
{
    ... 
    Config.SetContext (Application.Context); 
    ... 
}
```

모든 활동에서 라이프사이클 호출을 구현합니다.

```java
protected override void OnResume()
{
    ...
    Config.CollectLifecycleData (this);
    ...
}
protected override void OnPause() 
{
    ...
    Config.PauseCollectingLifecycleData ();
    ...
}
```
