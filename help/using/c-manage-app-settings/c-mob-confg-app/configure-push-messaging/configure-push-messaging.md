---
description: 새 앱을 만들거나 기존 앱을 편집하는 동안 이 정보를 사용하여 [앱 설정 관리] 페이지에서 [푸시 서비스] 옵션을 구성할 수 있습니다.
keywords: mobile
seo-description: 새 앱을 만들거나 기존 앱을 편집하는 동안 이 정보를 사용하여 [앱 설정 관리] 페이지에서 [푸시 서비스] 옵션을 구성할 수 있습니다.
seo-title: 푸시 메시지 구성
solution: Marketing Cloud,Analytics
title: 푸시 메시지 구성
topic: 지표
uuid: 6763858d-6046-4d36-87c0-cf3600a44fb1
translation-type: tm+mt
source-git-commit: 2c85c31d2fa54de26771553a6d349d3101e0048c

---


# Configure push messaging{#configure-push-messaging}

You can use this information to help you configure the Push Services options on the Manage App Settings page when creating a new app or editing an existing app.

Before you configure push messaging, complete the prerequisite tasks in Prerequisites to Enable Push Messaging.[](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)

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
      >If the file that you select for the **[!UICONTROL Private Key]** input also contains a certificate, you do not need to specify the certificate.

   * **[!UICONTROL 인증서]**

      올바른 인증서를 지정합니다. 이 옵션은 **[!UICONTROL 개인 키]** 입력에 인증서가 포함되어 있지 **않은** 경우에만 필요합니다. For more information about obtaining the SSL certificate and private key, see Configure App to use APNS or FCM.[](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)

   * Google

      **[!UICONTROL API 키]**

      올바른 API 키를 지정합니다. For more information about obtaining the API key, see Configure App to use APNS or FCM.[](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)

      자세한 내용은 다음 주제를 참조하십시오.

      * [Push Messaging in Android](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [Push Messaging in iOS](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
