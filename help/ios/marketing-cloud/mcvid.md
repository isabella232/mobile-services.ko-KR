---
description: Adobe Experience Platform ID 서비스는 Experience Cloud 솔루션 전반에 범용 방문자 ID를 제공합니다. ID 서비스는 타겟 분석, 비디오 하트비트 및 향후 Experience Cloud 통합에 필요합니다.
seo-description: Adobe Experience Platform ID 서비스는 Experience Cloud 솔루션 전반에 범용 방문자 ID를 제공합니다. ID 서비스는 타겟 분석, 비디오 하트비트 및 향후 Experience Cloud 통합에 필요합니다.
seo-title: Experience Cloud ID
solution: Marketing Cloud,Analytics
title: Experience Cloud ID
topic: 개발자 및 구현
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID {#experience-cloud-id}

Adobe Experience Platform ID 서비스는 Experience Cloud 솔루션 전반에 범용 방문자 ID를 제공합니다. ID 서비스는 타겟 분석, 비디오 하트비트 및 향후 Experience Cloud 통합에 필요합니다.

>[!TIP]
>
>Adobe Experience Platform ID 서비스를 사용하지 않는 경우에는 Experience Cloud ID를 채우지 않아도 됩니다. 자세한 내용은 [Adobe Experience Platform ID 서비스](https://marketing.adobe.com/resources/help/ko_KR/mcvid/)를 참조하십시오.

**SDK 버전 4.3 이상 필요**

## Experience Cloud ID 활성화 {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 [핵심 구현 및 라이프사이클](/help/ios/getting-started/dev-qs.md)에서 *프로젝트에 SDK 및 구성 파일 추가*&#x200B;를 참조하십시오.
1. 라이브러리를 가져옵니다:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. `ADBMobileConfig.json` 파일에 `marketingCloud` `org`가 포함되어 있는지 확인합니다.

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud 조직 ID는 Adobe Experience Cloud에서 각 고객 회사를 고유하게 식별하며 `016D5C175213CCA80A490D05@AdobeOrg`의 형식입니다.

   >[!IMPORTANT]
   >
   >`@AdobeOrg`를 포함해야 합니다.

   이 값이 없으면 Adobe Mobile Services에서 업데이트된 `ADBMobileConfig.json` 파일을 다운로드하십시오. 자세한 내용은 [ADBMobile JSON 구성](/help/ios/getting-started/requirements.md)을 참조하십시오.

구성하고 나면 Experience Cloud ID가 생성되며 모든 히트에 해당 ID가 포함됩니다. 사용자 지정 ID 및 자동 생성 ID 같은 다른 방문자 ID는 각 히트와 함께 계속 전송됩니다.
