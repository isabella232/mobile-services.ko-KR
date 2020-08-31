---
description: Adobe SDK를 사용하여 PII(개인 식별 정보)를 수집하고 이를 타사 엔드포인트로 보낼 수 있습니다.
seo-description: Adobe SDK를 사용하여 PII(개인 식별 정보)를 수집하고 이를 타사 엔드포인트로 보낼 수 있습니다.
seo-title: PII 포스트백
title: PII 포스트백
uuid: 8d1f1fb8-6842-478b-a164-e7f727755bd9
translation-type: ht
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: ht
source-wordcount: '182'
ht-degree: 100%

---


# PII 포스트백 {#pii-postbacks}

Adobe SDK를 사용하여 PII(개인 식별 정보)를 수집하고 이를 타사 엔드포인트로 보낼 수 있습니다.

Adobe SDK를 사용하여 PII를 수집하려면 추적 PII 호출을 전송해야 합니다. 이 호출을 사용하면 PII 데이터를 수집할 수 있지만 SDK는 데이터를 Adobe 엔드포인트로 자동 전송하지 않습니다. PII 유형의 포스트백은 적절한 종단점으로 구성해야 합니다.

>[!TIP]
>
>HTTPS를 지원하는 엔드포인트는 PII 포스트백 유형을 사용해야 합니다.

## PII 포스트백 추적 {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 [핵심 구현 및 라이프사이클](/help/android/getting-started/dev-qs.md)에서 *IntelliJ IDEA 또는 Eclipse 프로젝트에 SDK 및 구성 파일 추가*&#x200B;를 참조하십시오.

1. 라이브러리를 가져옵니다:

   ```java
   #import "ADBMobile.h"
   ```

1. PII를 캡처할 준비가 되면 `trackPII`을 호출하여 다음 작업, 이벤트 또는 보기에 대한 히트를 보냅니다.

   ```java
   Config.collectPII(new HashMap<String, Object>(){{
     put("key","value");
   }});
   ```

