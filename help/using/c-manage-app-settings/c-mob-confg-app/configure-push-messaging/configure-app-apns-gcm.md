---
description: 앱에서 APNS(Apple 푸시 알림 서비스) 또는 FCM(Firebase 클라우드 메시징)을 사용하도록 구성할 수 있습니다.
keywords: mobile
seo-description: 앱에서 APNS(Apple 푸시 알림 서비스) 또는 FCM(Firebase 클라우드 메시징)을 사용하도록 구성할 수 있습니다.
seo-title: APNS 또는 FCM 사용을 위한 앱 구성
solution: Experience Cloud,Analytics
title: APNS 또는 FCM 사용을 위한 앱 구성
topic: Metrics
uuid: fa411f2a-ba47-4499-bbe5-1aedef6b49ad
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 100%

---


# APNS 또는 FCM 사용을 위한 앱 구성{#configure-app-to-use-apns-or-fcm}

앱에서 APNS(Apple 푸시 알림 서비스) 또는 FCM(Firebase 클라우드 메시징)을 사용하도록 구성할 수 있습니다.

## Android 앱 {#section_41D304102CDF4586911EC1413AD35A10}

### 앱에서 FCM이 활성화되지 않은 경우

이 시나리오에서 FCM을 사용하도록 Android 앱을 구성하려면 다음을 수행하십시오.

1. [https://firebase.google.com/](https://firebase.google.com/)으로 이동하고 Google 개발자 자격 증명으로 로그인합니다.

1. **[!UICONTROL 시작하기]**&#x200B;를 클릭하고 **[!UICONTROL 프로젝트 추가]**&#x200B;를 선택합니다.

1. 프로젝트 이름을 입력하고 Firebase용 Google 애널리틱스 데이터에 옵트인하는 경우 컨트롤러-컨트롤러 조건을 수락하는 확인란을 클릭합니다.

1. **[!UICONTROL 프로젝트 생성]**&#x200B;을 클릭하고 프로젝트가 생성될 때까지 기다립니다.

1. 생성된 프로젝트를 클릭하면 생성된 프로젝트에 대한 **[!UICONTROL 프로젝트 개요]** 페이지가 표시됩니다. Android 아이콘이 있는 단추를 클릭하여 Android 앱을 프로젝트에 추가합니다.

1. 필요한 경우 앱 패키지 이름, 앱 별명 및 서명 인증서를 입력합니다.

1. 설정 마법사에서 제안하는 추가 단계를 따릅니다. Firebase 서버와의 통신을 테스트하여 Firebase 설정을 확인한 후 **[!UICONTROL 프로젝트 개요]** 페이지로 돌아갑니다.

1. **[!UICONTROL 프로젝트 개요]** 단추 오른쪽에 있는 톱니바퀴 아이콘을 클릭하고 **[!UICONTROL 프로젝트 설정]**&#x200B;을 클릭합니다.

1. **[!UICONTROL 클라우드 메시징]** 탭을 클릭합니다.

1. 나중에 사용할 수 있도록 **[!UICONTROL 기존 서버 키]** 및 **[!UICONTROL 보낸 사람 ID]**&#x200B;를 복사합니다.

   예:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### 앱에서 FCM이 활성화된 경우

이 시나리오에서 FCM을 사용하도록 Android 앱을 구성하려면 다음을 수행하십시오.

1. [https://firebase.google.com/](https://firebase.google.com/)으로 이동하고 Google 개발자 자격 증명으로 로그인합니다.

1. **[!UICONTROL 시작하기]**&#x200B;를 클릭합니다. 그러면 프로젝트 인덱스 페이지가 열립니다. Android 앱에 연결된 Firebase 지원 프로젝트를 찾은 다음 프로젝트 카드를 클릭합니다.

1. 프로젝트에 대한 **[!UICONTROL 프로젝트 개요]**&#x200B;가 로드됩니다. **[!UICONTROL 프로젝트 개요]** 단추 오른쪽에 있는 톱니바퀴 아이콘을 클릭하고 **[!UICONTROL 프로젝트 설정]**&#x200B;을 클릭합니다.

1. **[!UICONTROL 클라우드 메시징]** 탭을 클릭합니다.

1. 나중에 사용할 수 있도록 **[!UICONTROL 기존 서버 키]** 및 **[!UICONTROL 보낸 사람 ID]**&#x200B;를 복사합니다.

   예:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## iOS 앱 {#section_2031DAB485FC4D2B9027E42AD90B294D}

APNS를 사용하도록 iOS 앱을 구성하려면 다음을 수행하십시오.

1. [https://developer.apple.com/account](https://developer.apple.com/account) 사이트로 이동하고 [Apple Developer 계정](https://developer.apple.com/account)에 로그인합니다.
1. **[!UICONTROL iOS 앱]**&#x200B;에서 **[!UICONTROL ID]**&#x200B;를 선택합니다.
1. 푸시용으로 설정된 앱 ID가 있는 경우 11단계로 이동합니다.
1. **[!UICONTROL +]** 단추를 눌러 새 앱 ID를 만듭니다.
1. 앱 ID 설명을 입력합니다.
1. 앱 ID 접미사를 입력합니다.

   >[!IMPORTANT]
   >
   >푸시를 지원하려면 와일드카드를 사용하지 **않는** 명시적 앱 ID를 사용해야 합니다(예: `- com.tester.pushSample`).

1. **[!UICONTROL 앱 서비스]**&#x200B;에서 **[!UICONTROL 푸시 알림]** 확인란을 선택합니다.
1. **[!UICONTROL 계속을 클릭합니다]**.
1. **[!UICONTROL 제출을 클릭합니다]**.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.
1. 목록에서 푸시 메시지를 사용하도록 설정된 앱 ID를 선택하고 **[!UICONTROL 편집]**&#x200B;을 클릭합니다.
1. 이미 만들어진 푸시 인증서가 있다면 15단계로 건너뛰십시오.
1. **[!UICONTROL 푸시 알림]**&#x200B;까지 아래로 스크롤한 다음 적합한 **[!UICONTROL 인증서 만들기...]** 버튼을 클릭합니다.

   클릭하는 단추는 Development 인증서를 만드는지 아니면 Production 인증서를 만드는지 여부에 따라 다릅니다.
1. Apple 웹 사이트에서 CSR을 만들고, CSR을 업로드하고, 인증서를 생성하는 방법에 대한 단계를 따릅니다.
1. **[!UICONTROL 푸시 알림]** 섹션까지 아래로 스크롤한 다음 방금 만든 SSL 인증서를 다운로드합니다.
1. 다운로드한 인증서를 두 번 클릭하여 키체인에 추가합니다.

### SSL 인증서 및 개인 키

SSL 인증서 및 개인 키(APNS)를 받으려면 다음을 수행합니다.

1. **[!UICONTROL 키체인 액세스]**&#x200B;를 엽니다.
1. **[!UICONTROL 내 인증서]**&#x200B;를 클릭하고 앱과 환경에 적합한 **[!UICONTROL iOS 푸시 서비스 인증서]**&#x200B;를 찾습니다.

   해당 번들 ID와 Development인지 Production인지 여부를 비교하여 올바른 인증서를 식별할 수 있습니다.

1. 인증서를 확장하고 개인 키가 있는지 확인합니다.
1. 개인 키를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL &quot;*`<name of key>`*]**내보내기를 선택합니다.
1. 대화 상자에 필요한 정보를 입력하고 새 `.p12` 파일을 저장합니다.

   암호를 입력하지 않아도 됩니다.

1. **[!UICONTROL 개인 키]**&#x200B;에 `.p12` 파일을 입력합니다.

