---
description: 새 앱을 만들거나 기존 앱을 편집하는 동안 이 정보를 사용하여 [앱 설정 관리] 페이지에서 [푸시 서비스] 옵션을 구성할 수 있습니다.
keywords: mobile
seo-description: 새 앱을 만들거나 기존 앱을 편집하는 동안 이 정보를 사용하여 [앱 설정 관리] 페이지에서 [푸시 서비스] 옵션을 구성할 수 있습니다.
seo-title: 푸시 메시지 구성
solution: Marketing Cloud, Analytics
title: 푸시 메시지 구성
topic: 지표
uuid: 6763858 D -6046-4 D 36-87 C 0-CF 3600 A 44 FB 1
translation-type: tm+mt
source-git-commit: 2c85c31d2fa54de26771553a6d349d3101e0048c

---


# Configure push messaging{#configure-push-messaging}

이 정보를 사용하여 새 앱을 만들거나 기존 앱을 편집할 때 앱 설정 관리 페이지에서 푸시 서비스 옵션을 구성할 수 있습니다.

푸시 메시지를 구성하기 전에 사전 요구 사항에 [있는 사전 요구 사항을 완료하여 푸시 메시지를 활성화합니다](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md).

* **보고서 세트 고려 사항**

   각 보고서 세트에서 Apple 및 Google에 대한 앱스토어 앱을 각각 하나씩 구성할 수 있습니다. 추가 앱이 필요한 경우, 예를 들어 프로덕션 환경에 대한 앱과 하나의 개발 환경에 대한 앱이 필요한 경우 새 앱스토어 앱과 각 환경에 대한 새 보고서 세트를 설정합니다.

>[!IMPORTANT]
>
>앱을 새 보고서 세트로 이동하는 것은 지원되지 않습니다. 새 보고서 세트로 마이그레이션하는 경우 푸시 구성이 중단되고 메시지가 전송되지 않을 수 있습니다.

1. Type information in the following fields under **[!UICONTROL Push Services]**:

   * Apple

      **[!UICONTROL 개인 키]**

      Browse to and select your valid private key `.p12`, `.key`, or `.pen`.

      >[!IMPORTANT]
      >**[!UICONTROL 개인 키]** 입력을 위해 선택하는 파일에 인증서가 포함되어 있으면 인증서를 지정할 필요가 없습니다.

   * **[!UICONTROL 인증서]**

      올바른 인증서를 지정합니다. 이 옵션은 **[!UICONTROL 개인 키]** 입력에 인증서가 포함되어 있지 **않은** 경우에만 필요합니다. SSL 인증서 및 개인 키 입수에 대한 자세한 내용은 APNS 또는 FCM를 사용하도록 앱 [구성을 참조하십시오](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

   * Google

      **[!UICONTROL API 키]**

      올바른 API 키를 지정합니다. API 키 입수에 대한 자세한 내용은 APNS 또는 FCM 사용을 위한 앱 [구성을 참조하십시오](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

      자세한 내용은 다음 주제를 참조하십시오.

      * [Android의 푸시 메시지](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [iOS의 푸시 메시지](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
