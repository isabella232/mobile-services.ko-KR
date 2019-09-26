---
description: 이 정보는 GDPR 데이터 삭제를 요청하는 데 도움이 됩니다.
seo-description: 이 정보는 GDPR 데이터 삭제를 요청하는 데 도움이 됩니다.
seo-title: 사용자의 옵트 상태 설정
solution: Marketing Cloud,Analytics
title: 사용자의 옵트 상태 설정
topic: 개발자 및 구현
uuid: 44a09a25-93c6-4e1a-b69e-710018e8b6c3
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Setting the user's opt status {#setting-the-user-s-opt-status}

이 정보는 GDPR 데이터 삭제를 요청하는 데 도움이 됩니다.

>[!IMPORTANT]
>
>Starting with Experience Cloud iOS SDKs 4.15, setting the privacy status to `unknown` holds Audience Manager and Experience Cloud ID hits.

다음 설정을 사용하여 Analytics, Target 및 Audience Manager 활동을 장치에서 허용할지 여부를 제어할 수 있습니다.

* `privacyDefault` in [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md).

   이 설정은 코드에서 변경될 때까지 유지되는 초기 설정을 제어합니다.

* `setPrivacyStatus` 메서드를 사용합니다.

   이 메서드로 개인 정보 설정을 변경한 후에는 이 메서드로 다시 설정을 변경하거나 앱을 제거하고 다시 설치할 때까지 변경 사항이 적용됩니다.

   메서드에 대한 자세한 내용은 [구성 메서드](/help/ios/configuration/json-config/json-config.md).

다음은 각 개인 정보 상태에 대한 정보입니다.

* **옵트인**

   * Analytics: 히트가 전송됩니다.
   * Target: Mbox 요청을 전송합니다.
   *  Audience Manager: 신호 및 ID 동기화를 전송합니다.
   * Value in the JSON config file: `optedin`
   * 값 `setPrivacyStatus`위치: `ADBMobilePrivacyStatusOptIn`

* **옵트아웃**

   * Analytics: 히트가 삭제됩니다.
   * Target: Mbox 요청을 허용하지 않습니다.
   * Audience Manager: 신호 및 ID 동기화를 허용하지 않습니다.
   * Value in the JSON config file: `optedout`
   * 값 `setPrivacyStatus`위치: `ADBMobilePrivacyStatusOptOut`

* **알 수 없음**

   * Analytics: 오프라인 추적이 활성화되어 **있을** 경우, 개인 정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트가 삭제됨)으로 변경될 때까지 히트를 저장합니다.

      오프라인 추적이 활성화되어 있지 **않을** 경우, 개인 정보 상태가 옵트인으로 변경될 때까지 히트를 삭제합니다.

   * Target: Mbox 요청을 전송합니다.
   *  Audience Manager: 신호 및 ID 동기화를 전송합니다.
   * Value in the JSON config file: `optunknown`
   * 값 `setPrivacyStatus`위치: `ADBMobilePrivacyStatusUnknown`

## 예 {#section_128AC455EE024193B5D4E5A565B53D00}

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

