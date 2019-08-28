---
description: Adobe Experience Platform Identity Service는 Experience Cloud 솔루션에서 범용 방문자 ID를 제공합니다. ID 서비스는 타겟 분석, 비디오 하트비트 및 향후 Experience Cloud 통합에 필요합니다.
seo-description: Adobe Experience Platform Identity Service는 Experience Cloud 솔루션에서 범용 방문자 ID를 제공합니다. ID 서비스는 타겟 분석, 비디오 하트비트 및 향후 Experience Cloud 통합에 필요합니다.
seo-title: Experience Cloud ID
solution: Marketing Cloud, Analytics
title: Experience Cloud ID
topic: 개발자 및 구현
uuid: 13628 EA 8-3 CD 4-4 CFC -8 FF 6-722 C 33 F 7813 A
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID {#experience-cloud-id}

Adobe Experience Platform Identity Service는 Experience Cloud 솔루션에서 범용 방문자 ID를 제공합니다. ID 서비스는 타겟 분석, 비디오 하트비트 및 향후 Experience Cloud 통합에 필요합니다.

>[!TIP]
>
>Adobe Experience Platform Identity Service를 사용하는 경우 외에는 Experience Cloud ID를 채울 필요가 없습니다. For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

**SDK 버전 4.3 이상 필요**

## Experience Cloud ID 사용 {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 핵심 구현 *및* 라이프사이클에서 [프로젝트에 SDK 및 구성 파일 추가를](/help/ios/getting-started/dev-qs.md)참조하십시오.
1. 라이브러리를 가져옵니다:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. `ADBMobileConfig.json` 파일에 다음이 포함되어 있는지 확인합니다 `marketingCloud``org`.

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud organization IDs uniquely identify each client company in the Adobe Experience Cloud and are similar to the following value: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >`@AdobeOrg`반드시 포함해야 합니다.

   If these values are not present, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. 자세한 내용은 [Adbmobile JSON 구성을](/help/ios/getting-started/requirements.md)참조하십시오.

구성하고 나면 Experience Cloud ID가 생성되며 모든 히트에 해당 ID가 포함됩니다. 사용자 지정 ID 및 자동 생성 ID 같은 다른 방문자 ID는 각 히트와 함께 계속 전송됩니다.
