---
description: Experience Cloud Device Co-op를 사용하려면 Adobe 담당자에게 문의하십시오.
title: Experience Cloud Device Co-op
uuid: 434a6f8f-ec24-439d-95f0-a246b384b3b5
exl-id: bf4f7a81-152c-4033-bcdf-22a939a3109e
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 90%

---

# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Experience Cloud Device Co-op를 사용하려면 Adobe 담당자에게 문의하십시오.

Experience Cloud Device Co-op에 모바일 앱을 활성화하려면 Experience Cloud iOS SDK에 대해 다음 단계를 완료하십시오.

>[!IMPORTANT]
>
>이 기능이 제대로 작동하려면 iOS SDK 버전 4.8.5 이상이 필요합니다.

SDK 버전 4.16.1부터 Device Co-op 구성원은 Experience Cloud Device Co-op에서 모바일 장치 데이터를 옵트아웃할 수 있습니다. 자세한 내용은 Adobe Experience Cloud Identity 서비스 설명서에서 [ADBMobile JSON 구성](/help/ios/configuration/json-config/json-config.md) 및 [isCoopSafe](https://experienceleague.adobe.com/docs/id-service/using/id-service-api/configurations/coopsafe.html)에 대한 `visitorAPI.js` 메서드를 참조하십시오.

1. Adobe Mobile SDK를 구현합니다.

   자세한 내용은 [핵심 구현 및 라이프사이클](/help/ios/getting-started/dev-qs.md)을 참조하십시오.
1. Experience Cloud ID를 사용으로 설정합니다.

   자세한 내용은 [Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md)를 참조하십시오.
1. 여기에 포함된 동기화 메서드 중 하나를 사용하여 CRM ID 또는 해시된 이메일과 같은 인증된 ID를 전달합니다.

   자세한 내용은 [Adobe Experience Platform ID 서비스 메서드](/help/ios/marketing-cloud/mc-methods.md)를 참조하십시오.

## `coopUnsafe` 플래그

다음은 `coopUnsafe` 플래그에 대한 일부 추가 정보입니다.

* 최소 SDK 버전: 4.16.1
* `marketingCloud`로 설정된 경우 `true` 개체의 부울 속성으로 인해 장치가 Experience Cloud의 Device Co-Op에서 옵트아웃됩니다.
* 기본값은 `false`입니다.
* 이 설정은 Device Co-op 프로비저닝 고객&#x200B;**에게만** 사용됩니다.

이 값을 `true` 로 설정해야 하는 Device Co-op 멤버의 경우, Device Co-op 계정에서 차단 목록 플래그를 요청하려면 Co-op 팀과 작업해야 합니다. 이 플래그를 활성화하기 위한 셀프 서비스 경로가 없습니다.

다음 정보를 숙지하십시오.

* `coopUnsafe`가 `true`로 설정되면 `coop_unsafe=1`이 항상 Audience Manager 및 방문자 ID 히트에 추가됩니다.
* Audience Manager에 Analytics 서버측 전달을 활성화하는 경우, Analytics 조회수에 `coop_unsafe=1`이 표시됩니다.
