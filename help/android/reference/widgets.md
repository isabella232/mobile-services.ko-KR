---
description: Android 위젯은 앱과 동일한 방법을 사용하여 추적할 수 있습니다. 위젯은 애플리케이션 컨텍스트를 앱과 공유하므로 히트 순서와 방문자 식별이 유지됩니다.
keywords: android;라이브러리;모바일;sdk
solution: Experience Cloud Services,Analytics
title: Android 위젯
topic-fix: Developer and implementation
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
exl-id: 229ea987-256a-45f4-a5ca-afe17dd596b8
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 100%

---

# Android 위젯 {#android-widgets}

Android 위젯은 앱과 동일한 방법을 사용하여 추적할 수 있습니다. 위젯은 애플리케이션 컨텍스트를 앱과 공유하므로 히트 순서와 방문자 식별이 유지됩니다.

다음 지침은 Android 위젯을 추적하는 데 도움이 됩니다.

* 위젯에서 라이프사이클 지표(`startActivity`/`stopActivity`) 호출을 구현하지 마십시오.

* 위젯이 홈 화면에 추가되는 시기를 추적하려면 `trackState` 또는 `trackEvent` 호출을 위젯의 `onEnabled` 메서드에 추가합니다.

* 위젯에서 앱이 시작되는 시기를 추적하려면 애플리케이션을 시작하려는 의도를 생성하기 전에 `trackState` 또는 `trackEvent` 호출을 추가합니다.

* 작업 컨텍스트를 추적하려면 `AppExperienceType="widget"`과 `app`처럼 각 작업을 개별적으로 세그먼트화하는 옵션을 제공하는 `ContextData` 변수를 정의할 수 있습니다.
