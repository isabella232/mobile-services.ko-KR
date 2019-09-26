---
description: Android용 라이프사이클 지표를 구현하는 데 도움이 되는 정보입니다. iOS에서는 라이프사이클 지표가 자동으로 수집됩니다.
keywords: Xamarin
seo-description: Android용 라이프사이클 지표를 구현하는 데 도움이 되는 정보입니다. iOS에서는 라이프사이클 지표가 자동으로 수집됩니다.
seo-title: 라이프사이클 구현
solution: Marketing Cloud,Developer
title: 라이프사이클 구현
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Implement lifecycle {#implement-lifecycle}

This information helps you implement Lifecycle metrics for Android.

>[!TIP]
>
>iOS에서는 라이프사이클 지표가 자동으로 수집됩니다.

For the metrics and dimensions that can be measured automatically by the mobile library after lifecycle is implemented, see [Lifecycle Metrics](/help/ios/metrics.md).

## iOS

iOS에서는 라이프사이클 지표가 자동으로 수집됩니다.

## Android

기본 활동에서 Android SDK에 대한 애플리케이션 컨텍스트를 설정합니다.

```java
protected override void OnCreate (Bundle bundle) 
{
    ... 
    Config.SetContext (Application.Context); 
    ... 
}
```

In every activity, implement lifecycle calls.

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
