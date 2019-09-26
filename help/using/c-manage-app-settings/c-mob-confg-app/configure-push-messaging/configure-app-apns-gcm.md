---
description: You can configure your app to use Apple Push Notification Service (APNS) or Firebase Cloud Messaging (FCM).
keywords: mobile
seo-description: Apple 푸시 알림 서비스(APNS) 또는 FCM(Firebase Cloud Messaging)을 사용하도록 앱을 구성할 수 있습니다.
seo-title: APNS 또는 FCM을 사용하도록 앱 구성
solution: Marketing Cloud,Analytics
title: APNS 또는 FCM을 사용하도록 앱 구성
topic: 지표
uuid: fa411f2a-ba47-4499-bbe5-1aedef6b49ad
translation-type: tm+mt
source-git-commit: 608384f1fee2a05699ff13fbd51c3cc43aeb693c

---


# Configure your app to use APNS or FCM{#configure-app-to-use-apns-or-fcm}

You can configure your app to use Apple Push Notification Service (APNS) or Firebase Cloud Messaging (FCM).

## Android 앱 {#section_41D304102CDF4586911EC1413AD35A10}

### If FCM is not enabled in your app

To configure your Android app to use FCM in this scenario:

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. Click Get Started and select Add Project.********

1. 프로젝트 이름을 입력하고 Firebase 데이터를 위해 Google Analytics에 로그인하는 경우 컨트롤러-컨트롤러 조건을 수락하는 확인란을 클릭합니다.

1. 프로젝트 **[!UICONTROL 만들기를]** 클릭하고 프로젝트가 생성될 때까지 기다립니다.

1. 생성된 프로젝트를 클릭하면 생성된 **[!UICONTROL 프로젝트에]** 대한 프로젝트 개요 페이지가 표시됩니다. Android 아이콘이 있는 버튼을 클릭하여 Android 앱을 프로젝트에 추가합니다.

1. 필요한 경우 앱 패키지 이름, 앱 별칭 및 서명 인증서를 입력합니다.

1. 설치 마법사에서 제안하는 추가 단계를 따릅니다. Firebase 서버와 통신을 테스트하여 Firebase 설정을 확인한 후 프로젝트 개요 **[!UICONTROL 페이지로]** 돌아갑니다.

1. Click the gear icon to the right of the Project Overview button and click Project Settings.********

1. 클라우드 메시지 **[!UICONTROL 탭을]** 클릭합니다.

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   예:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### 앱에서 FCM이 활성화된 경우

이 시나리오에서 FCM을 사용하도록 Android 앱을 구성하려면:

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. 시작하기를 **[!UICONTROL 클릭합니다]**. 그러면 프로젝트 인덱스 페이지가 열립니다. Android 앱에 연결된 Firebase 지원 프로젝트를 찾아 프로젝트 카드를 클릭합니다.

1. 그런 **[!UICONTROL 다음]** 프로젝트에 대한 프로젝트 개요를 로드해야 합니다. [프로젝트 개요] 단추 오른쪽에 있는 톱니바퀴 **[!UICONTROL 아이콘을]** 클릭하고 [프로젝트 설정] **[!UICONTROL 을 클릭합니다]**.

1. 클라우드 메시지 **[!UICONTROL 탭을]** 클릭합니다.

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   예:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## iOS apps {#section_2031DAB485FC4D2B9027E42AD90B294D}

APNS를 사용하도록 iOS 앱을 구성하려면 다음을 수행하십시오.

1. [https://developer.apple.com/account](https://developer.apple.com/account)로 이동하고 [Apple 개발자 계정](https://developer.apple.com/account)에 로그인합니다.
1. Under **[!UICONTROL iOS Apps]**, select **[!UICONTROL Identifiers]**.
1. 푸시를 위해 앱 ID를 설정한 경우 11단계로 이동합니다.
1. Press the **[!UICONTROL +]** button to create a new App ID.
1. 앱 ID 설명을 입력합니다.
1. 앱 ID 접미사를 입력합니다.

   >[!IMPORTANT]
   >
   >To support push, you must use an Explicit App ID that does **not** use a wild card (for example, `- com.tester.pushSample`).

1. **[!UICONTROL 앱 서비스]**&#x200B;에서 **[!UICONTROL 푸시 알림]** 확인란을 선택합니다.
1. **[!UICONTROL 계속을 클릭합니다]**.
1. **[!UICONTROL 제출을 클릭합니다]**.
1. **[!UICONTROL 완료를 클릭합니다]**.
1. 목록에서 푸시 메시지를 사용하도록 설정된 앱 ID를 선택하고 **[!UICONTROL 편집]**&#x200B;을 클릭합니다.
1. 이미 만들어진 푸시 인증서가 있다면 15단계로 건너뛰십시오.
1. **[!UICONTROL 푸시 알림]**&#x200B;까지 아래로 스크롤한 다음 적합한 **[!UICONTROL 인증서 만들기...]** 버튼을 클릭합니다.

   클릭하는 단추는 개발 또는 제작용 인증서를 만드는지 여부에 따라 다릅니다.
1. Apple 웹 사이트에서 CSR을 만들고 CSR을 업로드하고 인증서를 생성하는 방법에 대한 단계를 따릅니다.
1. **[!UICONTROL 푸시 알림]** 섹션까지 아래로 스크롤한 다음 방금 만든 SSL 인증서를 다운로드합니다.
1. 다운로드한 인증서를 두 번 클릭하여 키체인에 추가합니다.

### SSL 인증서 및 개인 키

SSL 인증서 및 개인 키(APNS)를 가져오려면 다음을 수행하십시오.

1. **[!UICONTROL 키체인 액세스]**&#x200B;를 엽니다.
1. Click **[!UICONTROL My Certificates]** and find the appropriate **[!UICONTROL iOS Push Services Certificate]** for your app and environment.

   번들 ID를 일치시켜 올바른 인증서를 식별하고, 개발 인증서인지 아니면 프로덕션 인증서인지 식별할 수 있습니다.

1. 인증서를 확장하고 개인 키가 들어 있는지 확인합니다.
1. Right-click the private key and select **[!UICONTROL Export "*`<name of key>`*]**.
1. 대화 상자에 필요한 정보를 입력하고 새 `.p12` 파일을 저장합니다.

   암호를 입력하지 않아도 됩니다.

1. In the **[!UICONTROL Private Key]**, type the `.p12` file.

