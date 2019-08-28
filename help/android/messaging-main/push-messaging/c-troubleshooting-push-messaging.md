---
description: 다음은 푸시 메시지 문제를 해결하는 데 유용한 정보입니다.
keywords: mobile
seo-description: 다음은 푸시 메시지 문제를 해결하는 데 유용한 정보입니다.
seo-title: 푸시 메시지 문제 해결
solution: Marketing Cloud, Analytics
title: 푸시 메시지 문제 해결
topic: 지표
uuid: 9 C 4 A 9371-6691-4 A 2 C-A 6 C 1-B 9 F 901 A 41599
translation-type: tm+mt
source-git-commit: 12e01e112debffd877dd62f1fd2505724b2aae7d

---


# 푸시 메시지 문제 해결 {#troubleshooting-push-messaging}

다음은 푸시 메시지 문제를 해결하는 데 유용한 정보입니다.

## 푸시 메시지를 보내는 데 가끔 지연되는 이유는 무엇입니까?

다음 유형의 지연이 Mobile Services의 푸시 메시지와 관련 있을 수 있습니다.

* Analytics 히트 대기 중

   모든 보고서 세트에는 들어오는 Analytics 히트를 처리할 시기를 결정하는 설정이 있습니다. 기본값은 매시 정각입니다. Analytics 히트의 실제 처리는 최대 30분이 소요될 수 있지만, 일반적으로 15-20분 정도 걸립니다. 예를 들어, 보고서 세트는 매시간 히트를 처리합니다. 최대 30분의 처리 시간을 고려할 때, 푸시 메시지에 대해 수신 히트를 사용하려면 최대 90분이 걸릴 수 있습니다. 만약 사용자가 오전 9:01에 앱을 시작했다면, 히트는 오전 10:15와 오전 10:30 사이에 새 고유 사용자로서 Mobile Services UI에 표시될 것입니다.

* 푸시 서비스 대기 중

   푸시 서비스 (APNS 또는 FCM) 는 메시지를 즉시 보낼 수 없습니다. 일반적이지는 않지만, 5-10분의 지연이 발생한 적이 있습니다. 메시지 페이지에서 메시지의 **보기** 링크를 클릭하여 푸시 메시지가 푸시 서비스로 전송되었는지 확인할 수 있습니다. 푸시 서비스로의 전송 횟수는 보고서의 **[!UICONTROL 게시됨]열에 나열됩니다.**

   >[!TIP]
   >
   >푸시 서비스는 메시지가 전송될 것이라고 보장하지 않습니다.

   서비스의 안정성에 대한 자세한 내용은 다음 설명서를 참조하십시오.

   * **APNS**: [서비스 품질](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   * **FCM**: [메시지 라이프타임](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)

## 푸시 메시지가 잘리거나 확장되지 않는 이유는 무엇입니까?

일부 Android 장치의 경우 메시지를 표시할 때 `NotificationCompat.BigTextStyle`을 사용해야 할 수 있습니다.
