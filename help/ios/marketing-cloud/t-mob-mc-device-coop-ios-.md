---
description: Experience Cloud Device Co-op를 사용하려면 Adobe 담당자에게 문의하십시오.
seo-description: Experience Cloud Device Co-op를 사용하려면 Adobe 담당자에게 문의하십시오.
seo-title: Experience Cloud Device Co-op
title: Experience Cloud Device Co-op
uuid: 434 A 6 F 8 F-EC 24-439 D -95 F 0-A 246 B 384 B 3 B 5
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Experience Cloud Device Co-op를 사용하려면 Adobe 담당자에게 문의하십시오.

Experience Cloud Device Co-op에 모바일 앱을 활성화하려면 Experience Cloud iOS SDK에 대해 다음 단계를 완료하십시오.

>[!IMPORTANT]
>
>이 기능을 사용하려면 iOS SDK 버전 4.8.5 이상이 필요합니다.

SDK 4.16.1 버전부터 Device Co-op 멤버는 자신의 모바일 장치 데이터를 Experience Cloud Device Co-op에서 옵트아웃할 수 있습니다. 자세한 내용은 [ADBMobile JSON 구성](/help/ios/configuration/json-config/json-config.md) 및 `visitorAPI.js`isCoopSafe[에 대한 ](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-coopsafe.html) 메소드.

1. Adobe Mobile SDK를 구현합니다.

   자세한 내용은 [핵심 구현 및 라이프사이클을](/help/ios/getting-started/dev-qs.md)참조하십시오.
1. Experience Cloud ID를 사용으로 설정합니다.

   For more information, see [Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md).
1. 여기에 포함된 동기화 메서드 중 하나를 사용하여 CRM ID 또는 해시된 이메일과 같은 인증된 ID를 전달합니다.

   자세한 내용은 [Adobe Experience Platform Identity Service 방법을](/help/ios/marketing-cloud/mc-methods.md)참조하십시오.

## `coopUnsafe` flag

Here is some additional information on the `coopUnsafe` flag:

* 최소 SDK 버전: 4.16.1
* `marketingCloud` 로 설정하면 장치가 Experience Cloud의 Device `true`Co-op에서 옵트아웃되는 객체의 부울 속성입니다.
* Default value is `false`.
* 이 설정은 Device Co-op 프로비저닝 고객&#x200B;**에게만** 사용됩니다.

이 값을 `true` 로 설정해야 하는 Device Co-op 멤버의 경우, Device Co-op 계정에서 블랙리스트 플래그를 요청하려면 Co-op 팀과 작업해야 합니다. 이 플래그를 활성화하기 위한 셀프 서비스 경로가 없습니다.

다음 정보를 숙지하십시오.

* When `coopUnsafe` is set to `true`, `coop_unsafe=1` will always be appended to Audience Manager and Visitor ID hits.
* Audience Manager에 Analytics 서버측 전달을 활성화하는 경우, Analytics 조회수에 `coop_unsafe=1`이 표시됩니다.


