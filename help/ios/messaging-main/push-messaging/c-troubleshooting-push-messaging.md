---
description: 다음은 푸시 메시지 문제를 해결하는 데 유용한 정보입니다.
keywords: mobile
seo-description: 다음은 푸시 메시지 문제를 해결하는 데 유용한 정보입니다.
seo-title: 푸시 메시지 문제 해결
solution: Experience Cloud,Analytics
title: 푸시 메시지 문제 해결
topic: Metrics
uuid: 87d7dcb6-82a8-46e3-a6ed-7f895a22f2af
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '363'
ht-degree: 100%

---


# 푸시 메시지 문제 해결 {#troubleshooting-push-messaging}

다음은 푸시 메시지 문제를 해결하는 데 유용한 정보입니다.

## 푸시 메시지를 보내는 데 가끔 지연되는 이유는 무엇입니까?

다음 유형의 지연이 Mobile Services의 푸시 메시지와 관련 있을 수 있습니다.

* **Analytics 히트 대기 중**

   모든 보고서 세트에는 들어오는 Analytics 히트를 처리할 시기를 결정하는 설정이 있습니다. 기본값은 매시 정각입니다. Analytics 히트의 실제 처리는 최대 30분이 소요될 수 있지만, 일반적으로 15-20분 정도 걸립니다.

   예를 들어, 보고서 세트는 매 시간마다 히트를 처리합니다. 최대 30분의 처리 시간을 고려할 경우, 수신되는 히트를 푸시 메시지에 사용하는 데 최대 90분이 소요될 수 있습니다. 만약 사용자가 오전 9:01에 앱을 시작했다면, 히트는 오전 10:15와 오전 10:30 사이에 새 고유 사용자로서 Mobile Services UI에 표시될 것입니다.

* **푸시 서비스 대기 중**

   푸시 서비스(APNS 또는 GCM)가 메시지를 곧바로 발송하지 않을 수 있습니다. 일반적이지는 않지만, 5-10분의 지연이 발생한 적이 있습니다. 메시지 페이지에서 메시지의 보기 링크를 클릭하여 푸시 메시지가 푸시 서비스로 전송되었는지 확인할 수 있습니다. 푸시 서비스로의 전송 횟수는 보고서의 게시됨 열에 나열됩니다.

   >[!TIP]
   >
   >푸시 서비스로 메시지의 전송이 보장되지는 않습니다. 서비스의 안정성에 대한 자세한 내용은 다음 설명서를 참조하십시오.
   >
   >* **APNS**: [서비스 품질](https://developer.apple.com/kr/documentation/usernotifications)
   >
   >* **GCM**: [메시지 라이프타임](https://developers.google.com/cloud-messaging/concept-options)


## Apple Push Service 인증서를 어떻게 갱신합니까?

푸시 메시지를 전송하려면 유효한 푸시 서비스 인증서가 필요합니다. 인증서가 곧 만료되거나 만료된 경우 Mobile Services에서 알림을 보냅니다. 이 알림을 받으면 다음 단계를 완료하여 인증서를 갱신하십시오.

1. **[!UICONTROL 앱 설정 관리를 클릭합니다]**.
2. 현재 인증서를 삭제하려면 **[!UICONTROL 푸시 서비스]**&#x200B;로 스크롤한 다음 **[!UICONTROL 삭제]**&#x200B;를 클릭합니다.
3. 새 인증서를 구성하고 테스트하십시오.

   자세한 내용은 [푸시 메시지 사용을 위한 전제 조건](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)을 참조하십시오.

4. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

## iOS 시뮬레이터에서 푸시 메시지가 표시되지 않는 이유는 무엇입니까?

iOS 시뮬레이터는 푸시 메시지를 지원하지 않습니다.
