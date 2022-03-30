---
description: Adobe Experience Platform ID 서비스는 Experience Cloud 솔루션 전반에 범용 방문자 ID를 제공합니다. ID 서비스는 타겟 분석, 비디오 하트비트 및 향후 Experience Cloud 통합에 필요합니다.
solution: Experience Cloud Services,Analytics
title: Experience Cloud ID
topic-fix: Developer and implementation
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
exl-id: aa7db365-ad21-431f-bff6-2a6da212dd0c
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 91%

---

# Experience Cloud ID {#experience-cloud-id}

Adobe Experience Platform ID 서비스는 Experience Cloud 솔루션 전반에 범용 방문자 ID를 제공합니다. ID 서비스는 타겟 분석, 비디오 하트비트 및 향후 Experience Cloud 통합에 필요합니다.

>[!TIP]
>
>Adobe Experience Platform ID 서비스를 사용하지 않는 경우에는 Experience Cloud ID를 채우지 않아도 됩니다. 자세한 내용은 [Adobe Experience Platform Identity 서비스](https://experienceleague.adobe.com/docs/id-service/using/home.html) 설명서.

## Experience Cloud ID 활성화 {#section_79F984271C3B4366B7B04F864F4FF8C2}

이러한 단계에는 SDK 버전 4.3 이상이 필요합니다.

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

구성 후 Experience Cloud ID가 생성되고, 모든 히트 수에 포함됩니다. 사용자 지정 ID 및 자동 생성 ID 같은 다른 방문자 ID는 각 히트와 함께 계속 전송됩니다.
