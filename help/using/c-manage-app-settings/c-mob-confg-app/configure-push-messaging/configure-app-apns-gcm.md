---
description: APNS (Apple Push Notification Service) 또는 Firebase 클라우드 메시지 (FCM) 를 사용하도록 앱을 구성할 수 있습니다.
keywords: mobile
seo-description: APNS (Apple Push Notification Service) 또는 Firebase 클라우드 메시지 (FCM) 를 사용하도록 앱을 구성할 수 있습니다.
seo-title: APNS 또는 FCM를 사용하도록 앱 구성
solution: Marketing Cloud, Analytics
title: APNS 또는 FCM를 사용하도록 앱 구성
topic: 지표
uuid: fa 411 f 2 a-ba 47-4499-bbe 5-1 aedef 6 b 49 ad
translation-type: tm+mt
source-git-commit: 608384f1fee2a05699ff13fbd51c3cc43aeb693c

---


# APNS 또는 FCM를 사용하도록 앱 구성{#configure-app-to-use-apns-or-fcm}

APNS (Apple Push Notification Service) 또는 Firebase 클라우드 메시지 (FCM) 를 사용하도록 앱을 구성할 수 있습니다.

## Android 앱 {#section_41D304102CDF4586911EC1413AD35A10}

### 앱에서 FCM 이 활성화되지 않은 경우

이 시나리오에서 FCM를 사용하도록 Android 앱을 구성하려면 다음을 수행하십시오.

1. [https://firebase.google.com/](https://firebase.google.com/) 로 이동하여 Google 개발자 자격 증명으로 로그인합니다.

1. **[!UICONTROL 시작하기를]** 클릭하고 프로젝트 **[!UICONTROL 추가를]**&#x200B;선택합니다.

1. 프로젝트 이름을 입력하고 Firebase 데이터에 대한 Google Analytics에 옵트인 옵션을 선택한 경우 컨트롤러 컨트롤러 용어에 동의하는 확인란을 클릭합니다.

1. 프로젝트 **[!UICONTROL 만들기를]** 클릭하고 프로젝트를 만들 때까지 기다립니다.

1. 생성된 프로젝트를 클릭하면 생성된 프로젝트의 **[!UICONTROL 프로젝트 개요]** 페이지가 표시됩니다. Android 아이콘이 있는 단추를 클릭하여 프로젝트에 Android 앱을 추가합니다.

1. 필요한 경우 앱 패키지 이름, 앱 별칭 및 서명 인증서를 입력합니다.

1. 설정 마법사에서 제안하는 추가 단계를 따릅니다. Firebase 서버와 통신을 테스트하여 Firebase 설정을 확인한 후 **[!UICONTROL 프로젝트 개요]** 페이지로 돌아갑니다.

1. **[!UICONTROL 프로젝트 개요]** 단추 오른쪽에 있는 톱니바퀴 아이콘을 클릭하고 **[!UICONTROL 프로젝트 설정을]**&#x200B;클릭합니다.

1. **[!UICONTROL 클라우드 메시지]** 탭을 클릭합니다.

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   예:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### 앱에서 FCM 이 활성화되어 있는 경우

이 시나리오에서 FCM를 사용하도록 Android 앱을 구성하려면 다음을 수행하십시오.

1. [https://firebase.google.com/](https://firebase.google.com/) 로 이동하여 Google 개발자 자격 증명으로 로그인합니다.

1. **[!UICONTROL 시작하기를]**&#x200B;클릭합니다. 프로젝트 색인 페이지가 열립니다. Android 앱에 연결된 Firebase 사용 프로젝트를 찾아 프로젝트 카드를 클릭합니다.

1. 프로젝트에 대한 **[!UICONTROL 프로젝트 개요를]** 로드해야 합니다. **[!UICONTROL 프로젝트 개요]** 단추 오른쪽에 있는 톱니바퀴 아이콘을 클릭하고 **[!UICONTROL 프로젝트 설정을]**&#x200B;클릭합니다.

1. **[!UICONTROL 클라우드 메시지]** 탭을 클릭합니다.

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
1. **[!UICONTROL iOS 앱에서]****[!UICONTROL 식별자를]**&#x200B;선택합니다.
1. 푸시에 대해 설정된 앱 ID가 있는 경우 11 단계로 이동합니다.
1. **[!UICONTROL +]** 단추를 눌러 새 앱 ID를 만듭니다.
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

   클릭하는 단추는 개발 또는 생산 인증서를 만드는지 여부에 따라 달라집니다.
1. Apple 웹 사이트에서 CSR를 만들고 CSR를 업로드하고 인증서를 생성하는 방법에 대한 단계를 따릅니다.
1. **[!UICONTROL 푸시 알림]** 섹션까지 아래로 스크롤한 다음 방금 만든 SSL 인증서를 다운로드합니다.
1. 다운로드한 인증서를 두 번 클릭하여 키체인에 추가합니다.

### SSL 인증서 및 개인 키

SSL 인증서 및 개인 키 (APNS) 를 받으려면:

1. **[!UICONTROL 키체인 액세스]**&#x200B;를 엽니다.
1. **[!UICONTROL 내 인증서를]** 클릭하고 앱과 환경에 적합한 **[!UICONTROL iOS 푸시 서비스 인증서를]** 찾습니다.

   번들 ID를 일치시켜 올바른 인증서를 식별하고, 개발 인증서인지 아니면 프로덕션 인증서인지 식별할 수 있습니다.

1. 인증서를 확장하고 개인 키가 들어 있는지 확인합니다.
1. Right-click the private key and select **[!UICONTROL Export "*`<name of key>`*]**.
1. 대화 상자에 필요한 정보를 입력하고 새 `.p12` 파일을 저장합니다.

   암호를 입력하지 않아도 됩니다.

1. **[!UICONTROL 개인 키에서]**`.p12` 파일을 입력합니다.

