---
description: Android용 라이프사이클 지표를 구현하는 데 도움이 되는 정보입니다. iOS에 대해 라이프사이클 지표가 자동으로 수집됩니다.
keywords: Xamarin
solution: Experience Cloud Services
title: 라이프사이클 구현
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
exl-id: c76e63d1-48a5-4831-85d5-f3d3e9798a43
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 7%

---

# 라이프사이클 구현 {#implement-lifecycle}

다음은 Android용 라이프사이클 지표를 구현하는 데 유용한 정보입니다.

>[!TIP]
>
>iOS에 대해 라이프사이클 지표가 자동으로 수집됩니다.

라이프사이클이 구현된 후 모바일 라이브러리에서 자동으로 측정할 수 있는 지표 및 차원은 를 참조하십시오 [라이프사이클 지표](/help/ios/metrics.md).

## iOS

iOS에서 라이프사이클 지표는 자동으로 수집됩니다.

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
