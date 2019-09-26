---
description: 다음은 Android 웨어러블 앱에서 데이터를 수집할 수 있도록 Android 확장 기능을 구성할 때 참조할 수 있는 정보입니다.
seo-description: 다음은 Android 웨어러블 앱에서 데이터를 수집할 수 있도록 Android 확장 기능을 구성할 때 참조할 수 있는 정보입니다.
seo-title: Android 웨어러블 추가 메모
solution: Marketing Cloud,Analytics
title: Android Wearables  Additional Notes
topic: 개발자 및 구현
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Android Wearables: additional notes{#android-wearables-additional-notes}

다음은 Android 웨어러블 앱에서 데이터를 수집할 수 있도록 Android 확장 기능을 구성할 때 참조할 수 있는 정보입니다.

* Adobe Mobile Android 웨어러블 확장 기능을 사용하려면 Android 버전 4.4(KitKat) 이상이 필요합니다.
* 컨텍스트 값 `A.RunMode`가 추가되었으며, 이 값은 데이터의 출처가 포함 앱인지 아니면 확장 프로그램인지 나타냅니다.

   * `RunMode` = `Application`

      핸드헬드 앱의 히트

   * `RunMode` = `Extension`

      The hit comes from the wearable app.

* The SDK automatically syncs the `aid`/`vid`/`visitor` `service id`/`privacy` status from the handheld app to the wearable app, so do not call `setPrivacyStatus`/`setUserIdentifier`/`idSync` from the wearable app.
* [웨어러블 앱에 대해 인앱 메시지](/help/android/messaging-main/messaging/messaging.md), [Target](/help/android/target-main/target.md)및 [Audience Manager](/help/android/audience-manager/audiencemgmt.md) 를 사용할 수 없습니다.

