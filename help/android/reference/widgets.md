---
description: Android 위젯은 앱과 동일한 메서드를 사용하여 추적할 수 있습니다. 위젯은 애플리케이션 컨텍스트를 앱과 공유하므로 히트 순서와 방문자 식별이 유지됩니다.
keywords: Android; 라이브러리; 모바일; SDK
seo-description: Android 위젯은 앱과 동일한 메서드를 사용하여 추적할 수 있습니다. 위젯은 애플리케이션 컨텍스트를 앱과 공유하므로 히트 순서와 방문자 식별이 유지됩니다.
seo-title: Android 위젯
solution: Marketing Cloud, Analytics
title: Android 위젯
topic: 개발자 및 구현
uuid: 1 A 3718 FF -967 B -4 C 8 E-AE 0 B-BA 0 B-BA 15 BDDBDA 0 A
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Android widgets {#android-widgets}

Android 위젯은 앱과 동일한 메서드를 사용하여 추적할 수 있습니다. 위젯은 애플리케이션 컨텍스트를 앱과 공유하므로 히트 순서와 방문자 식별이 유지됩니다.

다음 지침은 Android 위젯을 추적하는 데 도움이 됩니다.

* Do not implement lifecycle metrics ( `startActivity`/ `stopActivity`) calls in the widget.

* 위젯이 홈 화면에 추가되는 시기를 추적하려면 `trackState` 또는 `trackEvent` 호출을 위젯의 `onEnabled` 메서드에 추가합니다.

* 위젯에서 앱이 시작되는 시기를 추적하려면 애플리케이션을 시작하려는 의도를 생성하기 전에 `trackState` 또는 `trackEvent` 호출을 추가합니다.

* To track the context of an action, you can define a `ContextData` variable that provides the option to segment each action separately (for example, `AppExperienceType="widget"` vs. `app`).

