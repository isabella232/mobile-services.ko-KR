---
description: 이 정보는 GDPR 데이터 삭제를 요청하는 데 도움이 됩니다.
seo-description: 이 정보는 GDPR 데이터 삭제를 요청하는 데 도움이 됩니다.
seo-title: 사용자의 선택 상태 설정
solution: Marketing Cloud, Analytics
title: 사용자의 선택 상태 설정
topic: 개발자 및 구현
uuid: F 8 A 3 E 6 BE -44 DD -494 E -9 CDA-DBBAC 86 D 6772
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Setting the user's opt status{#setting-the-user-s-opt-status}

이 정보는 GDPR 데이터 삭제를 요청하는 데 도움이 됩니다.

>[!IMPORTANT]
>
>Starting with Android SDK 4.15 , setting the privacy status to `unknown` holds Audience Manager and Experience Cloud ID hits.

다음 설정을 사용하여 Analytics, Target 및 Audience Manager 활동을 장치에서 허용할지 여부를 제어할 수 있습니다.

* `privacyDefault`[](/help/android/configuration/json-config/json-config.md)를 참조하십시오.

   이 설정은 코드에서 변경될 때까지 유지되는 초기 설정을 제어합니다.

* `Config.setPrivacyStatus` 메서드.

   이 메서드로 개인 정보 설정을 변경한 후에는 다시 설정을 변경하거나 앱을 제거하고 다시 설치할 때까지 이 변경 사항이 적용됩니다. 메서드에 대한 자세한 내용은 [구성 메서드](/help/android/configuration/methods.md).

다음 표는 각 개인 정보 상태에 대해 설명합니다.

* **옵트인**

   * **Analytics**: 히트가 전송됩니다.
   * **Target**: Mbox 요청을 전송합니다.
   * **Audience Manager**: 신호 및 ID 동기화를 전송합니다.
   * Value in the JSON Config file: `optedin`
   * 값: `setPrivacyStatus``MOBILE_PRIVACY_STATUS_OPT_IN`

* **옵트아웃**

   * **Analytics**: 히트가 삭제됩니다.
   * **Target**: Mbox 요청을 허용하지 않습니다.
   * **Audience Manager**: 신호 및 ID 동기화를 허용하지 않습니다.
   * Value in the JSON config file: `optedout`
   * 값: `setPrivacyStatus``MOBILE_PRIVACY_STATUS_OPT_OUT`

* **알 수 없음**

   * **분석**: 오프라인 추적이 **활성화되면**&#x200B;개인 정보 상태가 옵트인 (히트 수) 로 변경될 때까지 히트가 저장됩니다 (히트가 무시됨).

      오프라인 추적이 활성화되어 있지 <b>않을</b> 경우, 개인 정보 상태가 옵트인으로 변경될 때까지 히트를 삭제합니다.
   * **Target**: Mbox 요청을 전송합니다.
   * **Audience Manager**: 신호 및 ID 동기화를 전송합니다.
   * Value in the JSON config file: `optunknown`
   * 값: `setPrivacyStatus``MOBILE_PRIVACY_STATUS_UNKNOWN`

## 예 {#section_128AC455EE024193B5D4E5A565B53D00}

```java
public void setOptIn(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptOut(View view) { 
 Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_OUT); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptUnknown(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_UNKNOWN); 
 currentStatus = Config.getPrivacyStatus(); 
}
```

