---
description: 다음은 Android Wearable 앱의 데이터를 수집할 수 있는 Android 확장 기능을 구성하는 데 도움이 되는 몇 가지 정보입니다.
seo-description: 다음은 Android Wearable 앱의 데이터를 수집할 수 있는 Android 확장 기능을 구성하는 데 도움이 되는 몇 가지 정보입니다.
seo-title: Android 웨어러블 기기 추가 참고 사항
solution: Experience Cloud,Analytics
title: Android 웨어러블 기기 추가 참고 사항
topic-fix: Developer and implementation
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
exl-id: ae8cf2d1-d2b0-456b-bbd3-3980e00bbc84
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 100%

---

# Android 웨어러블 기기: 추가 참고 사항{#android-wearables-additional-notes}

다음은 Android Wearable 앱의 데이터를 수집할 수 있는 Android 확장 기능을 구성하는 데 도움이 되는 몇 가지 정보입니다.

* Adobe Mobile Android 웨어러블 기기 확장 기능을 사용하려면 Android 버전 4.4(KitKat) 이상이 필요합니다.
* 컨텍스트 값 `A.RunMode`가 추가되었으며, 이 값은 데이터의 출처가 포함 앱인지 아니면 확장 프로그램인지 나타냅니다.

   * `RunMode` = `Application`

      히트는 휴대용 앱에서 가져옵니다.

   * `RunMode` =  `Extension`

      히트는 웨어러블 앱에서 가져옵니다.

* SDK는 휴대폰 앱에서 웨어러블 앱으로 `aid`/`vid`/`visitor`/`service id`/`privacy` 상태를 자동으로 동기화하므로 웨어러블 앱에서 `setPrivacyStatus`/`setUserIdentifier`/`idSync`를 호출하지 마십시오.
* 웨어러블 앱에 대해 [인앱 메시지](/help/android/messaging-main/messaging/messaging.md), [Target](/help/android/target-main/target.md)및 [Audience Manager](/help/android/audience-manager/audiencemgmt.md)가 비활성화됩니다.
