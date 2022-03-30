---
description: Adobe Mobile Services에서 고유한 추적 코드가 있는 획득 링크를 생성할 수 있습니다. 사용자가 생성된 링크를 클릭한 후 Apple 앱스토어에서 앱을 다운로드하여 실행하면 SDK에서 자동으로 획득 데이터를 수집하여 Adobe Mobile Services로 보냅니다.
solution: Experience Cloud Services,Analytics
title: 모바일 앱 획득
topic-fix: Developer and implementation
uuid: 5fece619-e4b8-4d06-9250-dcb66fa32ce0
exl-id: a90dcb2f-babb-4c97-b67a-8468925ee5c8
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 100%

---

# 모바일 앱 획득 {#mobile-app-acquisition}

Adobe Mobile Services에서 고유한 추적 코드가 있는 획득 링크를 생성할 수 있습니다. 사용자가 생성된 링크를 클릭한 후 Apple 앱스토어에서 앱을 다운로드하여 실행하면 SDK에서 자동으로 획득 데이터를 수집하여 Adobe Mobile Services로 보냅니다.

획득을 사용하려면 SDK 버전 4.1 이상이 **있어야 합니다**.

획득 링크는 Adobe Mobile 서비스에서 만들어야 합니다. 자세한 내용은 [획득](/help/using/acquisition-main/acquisition-main.md)을 참조하십시오.

이 섹션의 정보를 사용하여 SDK에서는 획득 링크에서 획득 데이터를 전송할 수 있습니다.

## 모바일 앱 획득 추적 {#section_CEA30C652AC8470784B8054E299B80FA}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 [핵심 구현 및 라이프사이클](/help/ios/getting-started/dev-qs.md)에서 *프로젝트에 SDK 및 구성 파일 추가*&#x200B;를 참조하십시오.
1. 라이브러리를 가져옵니다:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. `ADBMobileConfig.json` 파일에 필요한 획득 설정이 포함되어 있는지 확인합니다.

   ```xml
   "acquisition": { 
      "server": "c00.adobe.com", 
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f" 
   }, 
   "analytics": { 
     "referrerTimeout": 5, 
     ...
   ```

   >[!IMPORTANT]
   >
   > 여러 보고서 세트로 데이터를 보내는 경우 보고서 세트 ID 목록의 첫 번째 보고서 세트와 연결된 앱의 획득 설정(획득 서버 및 appid)을 사용하십시오.

   `acquisition` 설정은 Adobe Mobile Services에 의해 생성되므로 변경해서는 안 됩니다. `acquisition` 설정이 미리 구성된 사용자 지정 `ADBMobileConfig.json` 파일을 다운로드하는 방법에 대한 자세한 내용은 [시작하기 전에](/help/ios/getting-started/requirements.md)를 참조하십시오.

이 설정을 사용하면 첫 번째 앱 시작 이후 초기 라이프사이클 호출과 함께 획득 데이터가 자동으로 전송됩니다.

>[!CAUTION]
>
>`referrerTimeout`  앱 획득을 사용하려면 을 0보다 큰 값으로 설정해야 합니다.

## 범용 링크에 대한 iOS 앱 활성화

앱에서 범용 링크를 사용하는 경우 Adobe Marketing Links 도메인을 앱에 대한 관련 도메인 목록에 추가합니다.

Xcode에서 Adobe Marketing Links 도메인을 관련 도메인 목록에 추가하려면 다음을 수행합니다.

1. 프로젝트 타겟으로 이동하고 **[!UICONTROL 기능]** 탭을 클릭합니다.
2. **[!UICONTROL 관련 도메인]** 섹션으로 스크롤한 후 켭니다.
3. 마케팅 링크 URL에서 마케팅 링크 도메인의 **[!UICONTROL 도메인]** 목록에 항목을 추가합니다.

항목 목양은 `applinks:5848561889a02a6996aea62b.c00.adobe.com`과 비슷합니다.
