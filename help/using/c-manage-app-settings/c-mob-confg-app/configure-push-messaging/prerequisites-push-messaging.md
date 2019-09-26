---
description: 응용 프로그램에서 푸시 메시지를 구성하기 전에 이러한 작업을 완료해야 합니다.
keywords: mobile
seo-description: 응용 프로그램에서 푸시 메시지를 구성하기 전에 이러한 작업을 완료해야 합니다.
seo-title: 푸시 메시지를 활성화하기 위한 전제 조건
solution: Marketing Cloud,Analytics
title: 푸시 메시지를 활성화하기 위한 전제 조건
topic: 지표
uuid: 194e6e07-b794-4152-a838-a4125c3292d4
translation-type: tm+mt
source-git-commit: 92b1e430293fbded666e8af3f01393898c0e5811

---


# Prerequisites to enable push messaging {#prerequisites-to-enable-push-messaging}

응용 프로그램에서 푸시 메시지를 구성하기 전에 이러한 작업을 완료해야 합니다.

## Enable the Experience Cloud for your company

Adobe Analytics를 사용하는 회사에서는 Experience Cloud가 활성화되어 있어야 합니다. Adobe 계정 담당자의 상태를 확인할 수 있습니다.

## Install and configure the Mobile SDK

* **Mobile SDK 설치**

   To configure push messaging, you must download and install at least version 4.6 or later of the Mobile SDK. For more information, see [Download the SDKs](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/download-sdk.md).

* **푸시 서비스 구성**

   Mobile SDK에서 푸시 서비스를 구성해야 합니다.
자세한 정보는 다음 내용을 참조하십시오.

   * [Push Messaging in Android](/help/android/messaging-main/push-messaging/push-messaging.md)
   * [iOS의 푸시 메시지](/help/ios/messaging-main/push-messaging/push-messaging.md)

## Adobe ID를 사용하여 Mobile 핵심 서비스에 로그인합니다

>[!IMPORTANT]
>
>To use the Push Services functionality users must log in to the Mobile Core Service by using their Adobe ID and their Analytics account must be linked to their Adobe IDs. 푸시 서비스 기능은 기존 Adobe Analytics 계정을 사용하여 로그인한 경우에는 사용할 수 없습니다.

사용자에게 Adobe ID가 없는 경우 다음 단계를 완료하십시오.

1. (**Experience Cloud Administrator**) Invite users to the Experience Cloud.

1. (**User**) Create a personal Adobe ID using the instructions that you received from the Experience Cloud administrator.

   이메일 메시지는 관리자가 이전 단계를 완료한 후 각 사용자에게 자동으로 전송됩니다.

1. (**Users**) Log in to Mobile using their Adobe ID.

## Link users' accounts in the Experience Cloud

각 사용자는 Experience Cloud 조직의 Analytics 솔루션 계정을 연결해야 합니다.

1. Adobe ID로 Experience Cloud에 로그인하려면 브라우저에 [https://marketing.adobe.com](https://marketing.adobe.com)을 입력합니다.

1. 오른쪽 상단 모서리에서 Analytics 회사 이름을 선택합니다.

1. **[!UICONTROL 조직 추가]**&#x200B;를 클릭한 다음, 드롭다운 목록에서 **Adobe SiteCatalyst/Adobe Social[!UICONTROL 을 선택합니다.]**

1. 회사 이름, 즉 지정된 회사의 레거시 자격 증명을 입력하고 **[!UICONTROL 계정 연결을 클릭합니다]**.

   이제 Adobe ID가 Analytics 계정, 회사 및 로그인 자격 증명에 연결됩니다.

자세한 내용은 [계정 연결 문제 해결](https://marketing.adobe.com/resources/help/en_US/mcloud/organizations.html)을 참조하십시오.

## Configure push services and the SDK ID service in the Mobile User Interface

앱에 대해 ID 서비스를 활성화하기 전에는 **[!UICONTROL 푸시 서비스]섹션이 비활성화되어 있습니다.** 그러나 ID 서비스를 활성화하면 푸시 서비스 섹션이 활성화됩니다. 푸시 서비스 활성화에 대한 자세한 내용은 SDK ID [서비스 옵션](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-visitor.md)구성을 참조하십시오.

>[!IMPORTANT]:저장을 클릭하여 **[!UICONTROL 변경 사항을]** 저장하고 푸시 서비스를 새로 고쳐야 합니다.
>
>각 보고서 세트에서 Apple 및 Google에 대한 앱스토어 앱을 각각 하나씩 구성할 수 있습니다. 추가 앱이 필요한 경우, 예를 들어 프로덕션 환경에 대한 앱과 하나의 개발 환경에 대한 앱이 필요한 경우 새 앱스토어 앱과 각 환경에 대한 새 보고서 세트를 설정합니다.

* **Apple**&#x200B;에 대해 개인 키 및/또는 인증서를 드래그하여 놓습니다. 개인 키가 암호로 암호화되어 있는 경우, 해당 암호를 입력합니다.

   * **개인 키**&#x200B;에 대해 개인 키 파일을 상자로 드래그하여 놓습니다.

      **[!UICONTROL 찾아보기]를 클릭하여 파일을 선택할 수도 있습니다.** 이 파일에는 개인 키가 들어 있습니다. The certificate might also be included in this file (`.p12`, `pkcs12`, `.pfx`, `.key`, `.pem`).

   * **개인 키 암호**&#x200B;에 대해 개인 키 파일이 암호화된 경우 암호 입력합니다.

      (조건) **인증서**&#x200B;에 대해 인증서 파일을 상자로 드래그하여 놓습니다. **[!UICONTROL 찾아보기]를 클릭하여 파일을 선택할 수도 있습니다.** This field is not required if the private-key file also contains the certificate ( `.cert`, `.cer`, `.crt`, `.pem`).

* **Google**&#x200B;에 대해 앱용 API 키를 지정합니다.

   **[!UICONTROL 테스트]를 클릭하여 앱 및 Mobile Services가 올바르게 구성되어 있는지 확인합니다.** 이 옵션은 디버그 및 문제 해결에 유용합니다.

   메시지를 보낼 장치의 푸시 토큰을 입력합니다. 토큰을 쉼표로 구분된 목록으로 지정하면 메시지를 여러 장치에 보낼 수 있습니다.

   ![푸시 테스트 메시지](assets/push_test_list.png)
