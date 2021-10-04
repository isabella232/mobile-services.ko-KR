---
description: Adobe SDK를 사용하여 PII(개인 식별 정보)를 수집하고 이를 타사 엔드포인트로 보낼 수 있습니다.
title: PII 포스트백
uuid: 08f76a52-75dd-4fc1-b4cc-4f5eef93d0f7
exl-id: 180c21f7-0fba-4b9b-ab7f-7afe81b85f38
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 86%

---

# PII 포스트백 {#pii-postbacks}

Adobe SDK를 사용하여 PII(개인 식별 정보)를 수집하고 이를 타사 엔드포인트로 보낼 수 있습니다.

Adobe SDK를 사용하여 PII를 수집하려면 추적 PII 호출을 전송해야 합니다. 이 호출을 사용하면 PII 데이터를 수집할 수 있지만 SDK는 데이터를 Adobe 엔드포인트로 자동 전송하지 않습니다. PII 유형의 포스트백은 적절한 종단점으로 구성해야 합니다.

>[!TIP]
>
>HTTPS를 지원하는 엔드포인트는 PII 포스트백 유형을 사용해야 합니다.

## PII 포스트백 추적 {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 [핵심 구현 및 라이프사이클](/help/ios/getting-started/dev-qs.md)에서 *프로젝트에 SDK 및 구성 파일 추가*&#x200B;를 참조하십시오.
1. 라이브러리를 가져옵니다:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. PII를 캡처할 준비가 되면 `trackPII`을 호출하여 다음 작업, 이벤트 또는 보기에 대한 히트를 보냅니다.

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```
