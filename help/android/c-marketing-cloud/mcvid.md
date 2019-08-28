---
description: Adobe Experience Platform Identity Service는 Experience Cloud 솔루션에서 범용 방문자 ID를 제공합니다. ID 서비스는 타겟 분석, 비디오 하트비트 및 향후 Experience Cloud 통합에 필요합니다.
seo-description: Adobe Experience Platform Identity Service는 Experience Cloud 솔루션에서 범용 방문자 ID를 제공합니다. ID 서비스는 타겟 분석, 비디오 하트비트 및 향후 Experience Cloud 통합에 필요합니다.
seo-title: Experience Cloud ID 구성
solution: Marketing Cloud, Analytics
title: Experience Cloud ID 구성
topic: 개발자 및 구현
uuid: 8 EBDF 2 BF-C 581-448 F -9542-F 99 A 19784 FE 7
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID configuration {#experience-cloud-id-configuration}

Adobe Experience Platform Identity Service는 Experience Cloud 솔루션에서 범용 방문자 ID를 제공합니다. ID 서비스는 타겟 분석, 비디오 하트비트 및 향후 Experience Cloud 통합에 필요합니다.

>[!TIP]
>
>Adobe Experience Platform Identity Service를 사용하고 있지 않은 경우 이 ID를 채울 필요가 없습니다. For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

>[!IMPORTANT]
>
>이 기능을 사용하려면 SDK 4.3 이상이 필요합니다.

Experience Cloud ID를 사용하려면 다음을 수행하십시오.

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 핵심 구현 *및* 라이프사이클에서 [Intellij 아이디어 또는 Eclipse 프로젝트에 SDK 및 구성 파일 추가를](/help/android/getting-started/dev-qs.md)참조하십시오.

1. 라이브러리를 가져옵니다:

   ```java
   import com.adobe.mobile.*;
   ```

1. `ADBMobileConfig.json` 파일에 다음이 포함되어 있는지 확인합니다 `marketingCloudorg`.

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud 조직 ID는 Adobe Experience Cloud에서 각 고객 회사를 고유하게 식별하며 다음 값과 유사합니다.

   ```js
   016D5C175213CCA80A490D05@AdobeOrg`
   ```

   >[!IMPORTANT]
   >
   >`@AdobeOrg`반드시 포함해야 합니다.

   If these IDs are not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. 자세한 내용은 [시작하기 전에](/help/android/getting-started/requirements.md)를 참조하십시오.

구성이 완료되면 Experience Cloud ID가 생성되며 모든 히트에 해당 ID가 포함됩니다. 사용자 지정 ID 및 자동 생성 ID 같은 다른 ID는 각 히트와 함께 계속 전송됩니다.
