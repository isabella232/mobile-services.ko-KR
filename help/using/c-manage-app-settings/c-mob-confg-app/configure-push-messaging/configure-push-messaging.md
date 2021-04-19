---
description: 새 앱을 만들거나 기존 앱을 편집하는 동안 이 정보를 사용하여 앱 설정 관리 페이지에서 푸시 서비스 옵션을 구성할 수 있습니다.
keywords: mobile
seo-description: 새 앱을 만들거나 기존 앱을 편집하는 동안 이 정보를 사용하여 앱 설정 관리 페이지에서 푸시 서비스 옵션을 구성할 수 있습니다.
seo-title: 푸시 메시지 구성
solution: Experience Cloud,Analytics
title: 푸시 메시지 구성
topic-fix: Metrics
uuid: 6763858d-6046-4d36-87c0-cf3600a44fb1
exl-id: d4989c31-2692-4062-8fae-d41c3e3c179b
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 100%

---

# 푸시 메시지 구성{#configure-push-messaging}

새 앱을 만들거나 기존 앱을 편집하는 동안 이 정보를 사용하여 앱 설정 관리 페이지에서 푸시 서비스 옵션을 구성할 수 있습니다.

푸시 메시지를 구성하기 전에 [푸시 메시지를 활성화하기 위한 전제 조건](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)의 전제 조건 작업을 완료하십시오.

* **보고서 세트 고려 사항**

   각 보고서 세트에서 Apple용 앱스토어 앱 하나와 Google용 하나를 각각 구성할 수 있습니다. 프로덕션 환경용 앱과 개발 환경용 앱과 같은 앱이 추가로 필요한 경우 각 환경에 대해 새 앱스토어 앱과 새 보고서 세트를 설정하십시오.

>[!IMPORTANT]
>
>앱을 새 보고서 세트로 이동할 수 없습니다. 새 보고서 세트로 마이그레이션하는 경우 푸시 구성이 중단되고 메시지가 전송되지 않을 수 있습니다.

1. **[!UICONTROL 푸시 서비스]**&#x200B;의 다음 필드에 정보를 입력하십시오.

   * Apple

      **[!UICONTROL 개인 키]**

      올바른 개인 키(`.p12`, `.key` 또는 `.pen`)로 이동하여 선택합니다.

      >[!IMPORTANT]
      >**[!UICONTROL 개인 키]** 입력을 위해 선택한 파일에 인증서가 포함되어 있으면 인증서를 지정할 필요가 없습니다.

   * **[!UICONTROL 인증서]**

      올바른 인증서를 지정합니다. 이 옵션은 **[!UICONTROL 개인 키]** 입력에 인증서가 포함되어 있지 **않은** 경우에만 필요합니다. SSL 인증서 및 개인 키를 가져오는 방법에 대한 자세한 내용은 [APNS 또는 FCM 사용을 위한 앱 구성](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)을 참조하십시오.

   * Google

      **[!UICONTROL API 키]**

      올바른 API 키를 지정합니다. API 키를 가져오는 방법에 대한 자세한 내용은 [APNS 또는 FCM 사용을 위한 앱 구성](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)을 참조하십시오.

      자세한 내용은 다음 주제를 참조하십시오.

      * [Android의 푸시 메시지](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [iOS의 푸시 메시지](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
