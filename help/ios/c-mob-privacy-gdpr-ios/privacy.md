---
description: 이 정보는 GDPR 데이터 삭제를 요청하는 데 도움이 됩니다.
solution: Experience Cloud Services,Analytics
title: 사용자의 옵트 상태 설정
topic-fix: Developer and implementation
uuid: 44a09a25-93c6-4e1a-b69e-710018e8b6c3
exl-id: 8fd30bea-6316-46ac-9787-8ca594545d1b
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 100%

---

# 사용자의 옵트 상태 설정 {#setting-the-user-s-opt-status}

이 정보는 GDPR 데이터 삭제를 요청하는 데 도움이 됩니다.

>[!IMPORTANT]
>
>Experience Cloud iOS SDK 4.15부터 개인 정보 상태를 `unknown`으로 설정하면 Audience Manager 및 Experience Cloud ID 히트 수가 보관됩니다.

다음 설정을 사용하여 Analytics, Target 및 Audience Manager 활동을 장치에서 허용할지 여부를 제어할 수 있습니다.

* [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md)의 `privacyDefault`.

   이 설정은 코드에서 변경될 때까지 유지되는 초기 설정을 제어합니다.

* `setPrivacyStatus` 메서드를 사용합니다.

   이 방법을 사용하여 개인 정보 설정을 변경하면 다시 이 방법을 사용하여 변경하거나 앱을 제거하고 다시 설치할 때까지 변경 사항이 적용됩니다.

   방법에 대한 자세한 내용은 [구성 방법](/help/ios/configuration/json-config/json-config.md)을 참조하십시오.

다음은 각 개인 정보 상태에 대한 정보입니다.

* **옵트인**

   * Analytics: 히트가 전송됩니다.
   * Target: Mbox 요청을 전송합니다.
   *  Audience Manager: 신호 및 ID 동기화를 전송합니다.
   * JSON 구성 파일의 값: `optedin`
   * `setPrivacyStatus`의 값: `ADBMobilePrivacyStatusOptIn`

* **옵트아웃**

   * Analytics: 히트가 삭제됩니다.
   * Target: Mbox 요청을 허용하지 않습니다.
   * Audience Manager: 신호 및 ID 동기화를 허용하지 않습니다.
   * JSON 구성 파일의 값: `optedout`
   * `setPrivacyStatus`의 값: `ADBMobilePrivacyStatusOptOut`

* **알 수 없음**

   * Analytics: 오프라인 추적이 활성화되어 **있을** 경우, 개인 정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트가 삭제됨)으로 변경될 때까지 히트를 저장합니다.

      오프라인 추적이 활성화되어 있지 **않을** 경우, 개인 정보 상태가 옵트인으로 변경될 때까지 히트를 삭제합니다.

   * Target: Mbox 요청을 전송합니다.
   *  Audience Manager: 신호 및 ID 동기화를 전송합니다.
   * JSON 구성 파일의 값: `optunknown`
   * `setPrivacyStatus`의 값: `ADBMobilePrivacyStatusUnknown`

## 예시 {#section_128AC455EE024193B5D4E5A565B53D00}

```objective-c
- (IBAction) setPrivacyOptIn { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn]; 
} 
- (IBAction) setPrivacyOptOut { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptOut]; 
} 
- (IBAction) setPrivacyOptUnknown { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusUnknown]; 
}
```
