---
description: Adobe SDK를 사용하면 개인식별정보(PII)를 수집하여 타사 종단점으로 보낼 수 있습니다.
seo-description: Adobe SDK를 사용하면 개인식별정보(PII)를 수집하여 타사 종단점으로 보낼 수 있습니다.
seo-title: PII 포스트백
title: PII 포스트백
uuid: 08 F 76 A 52-75 DD -4 FC 1-B 4 CC -4 F 5 EEF 93 D 0 F 7
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# PII postbacks {#pii-postbacks}

Adobe SDK를 사용하면 개인식별정보(PII)를 수집하여 타사 종단점으로 보낼 수 있습니다.

Adobe SDK를 사용하여 PII를 수집하려면 PII 추적 호출을 전송해야 합니다. 이 호출을 사용하면 PII 데이터를 수집할 수 있지만 SDK에서 Adobe 종단점으로 데이터를 자동으로 보내지는 않습니다. PII 유형의 포스트백은 적절한 종단점으로 구성해야 합니다.

>[!TIP]
>
>PII 포스트백 유형을 사용하려면 HTTPS를 지원하는 종점이 필요합니다.

## Tracking PII postbacks {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 핵심 구현 *및* 라이프사이클에서 [프로젝트에 SDK 및 구성 파일 추가를](/help/ios/getting-started/dev-qs.md)참조하십시오.
1. 라이브러리를 가져옵니다:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. PII를 캡처할 준비가 되면 `trackPII`을 호출하여 다음 작업, 이벤트 또는 보기에 대한 히트를 보냅니다.

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```

