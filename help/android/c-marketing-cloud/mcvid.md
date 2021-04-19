---
description: Adobe Experience Platform ID 서비스는 Experience Cloud 솔루션 전반에 범용 방문자 ID를 제공합니다. ID 서비스는 타겟 분석, 비디오 하트비트 및 향후 Experience Cloud 통합에 필요합니다.
seo-description: Adobe Experience Platform ID 서비스는 Experience Cloud 솔루션 전반에 범용 방문자 ID를 제공합니다. ID 서비스는 타겟 분석, 비디오 하트비트 및 향후 Experience Cloud 통합에 필요합니다.
seo-title: Experience Cloud ID 구성
solution: Experience Cloud,Analytics
title: Experience Cloud ID 구성
topic-fix: Developer and implementation
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
exl-id: 97dc6768-bf31-4a0d-a460-9caf9ecda5fb
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 100%

---

# Experience Cloud ID 구성 {#experience-cloud-id-configuration}

Adobe Experience Platform ID 서비스는 Experience Cloud 솔루션 전반에 범용 방문자 ID를 제공합니다. ID 서비스는 타겟 분석, 비디오 하트비트 및 향후 Experience Cloud 통합에 필요합니다.

>[!TIP]
>
>Adobe Experience Platform ID 서비스를 사용하지 않는 경우에는 이 ID를 채우지 않아도 됩니다. 자세한 내용은 [Adobe Experience Platform ID 서비스](https://docs.adobe.com/content/help/ko-KR/id-service/using/home.html)를 참조하십시오.

>[!IMPORTANT]
>
>이 기능을 사용하려면 SDK 버전 4.3 이상이 필요합니다.

Experience Cloud ID를 사용하려면 다음을 수행하십시오.

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 [핵심 구현 및 라이프사이클](/help/android/getting-started/dev-qs.md)에서 *IntelliJ IDEA 또는 Eclipse 프로젝트에 SDK 및 구성 파일 추가*&#x200B;를 참조하십시오.

1. 라이브러리를 가져옵니다:

   ```java
   import com.adobe.mobile.*;
   ```

1. `ADBMobileConfig.json` 파일에 `marketingCloudorg`가 포함되어 있는지 확인합니다.

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
   >`@AdobeOrg`를 포함해야 합니다.

   이러한 ID가 구성되어 있지 않으면 업데이트된 `ADBMobileConfig.json` 파일을 Adobe Mobile Services에서 다운로드합니다. 자세한 내용은 [시작하기 전에](/help/android/getting-started/requirements.md)를 참조하십시오.

구성이 완료되면 Experience Cloud ID가 생성되고, 모든 히트 수에 포함됩니다. 사용자 지정 ID 및 자동 생성 ID 같은 다른 ID는 각 히트와 함께 계속 전송됩니다.
