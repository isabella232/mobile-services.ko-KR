---
description: Adobe Experience Platform Identity Service는 Experience Cloud 솔루션 전체에서 범용 방문자 ID를 제공합니다. ID 서비스는 타겟 분석, 비디오 하트비트 및 향후 Experience Cloud 통합에 필요합니다.
seo-description: Adobe Experience Platform Identity Service는 Experience Cloud 솔루션 전체에서 범용 방문자 ID를 제공합니다. ID 서비스는 타겟 분석, 비디오 하트비트 및 향후 Experience Cloud 통합에 필요합니다.
seo-title: Experience Cloud ID
solution: Marketing Cloud,Analytics
title: Experience Cloud ID
topic: 개발자 및 구현
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID {#experience-cloud-id}

Adobe Experience Platform Identity Service는 Experience Cloud 솔루션 전체에서 범용 방문자 ID를 제공합니다. ID 서비스는 타겟 분석, 비디오 하트비트 및 향후 Experience Cloud 통합에 필요합니다.

>[!TIP]
>
>Adobe Experience Platform ID 서비스를 사용하지 않는 한 Experience Cloud ID를 채울 필요가 없습니다. For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

**SDK 버전 4.3 이상 필요**

## Experience Cloud ID 활성화 {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 핵심 구현 *및 라이프사이클에서 SDK 및 구성* 파일을 프로젝트에 [추가를 참조하십시오](/help/ios/getting-started/dev-qs.md).
1. 라이브러리를 가져옵니다:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 파일에 다음 항목이 포함되어 `ADBMobileConfig.json` 있는지 확인합니다 `marketingCloud` `org`.

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud organization IDs uniquely identify each client company in the Adobe Experience Cloud and are similar to the following value: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >포함시켜야 `@AdobeOrg`합니다.

   If these values are not present, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. For more information, see ADBMobile JSON config.[](/help/ios/getting-started/requirements.md)

구성하고 나면 Experience Cloud ID가 생성되며 모든 히트에 해당 ID가 포함됩니다. 사용자 지정 ID 및 자동 생성 ID 같은 다른 방문자 ID는 각 히트와 함께 계속 전송됩니다.
