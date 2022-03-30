---
description: 이 정보는 GDPR 데이터 삭제를 요청하는 데 도움이 됩니다.
solution: Experience Cloud Services,Analytics
title: 사용자의 옵트 상태 설정
topic-fix: Developer and implementation
uuid: f8a3e6be-44dd-494e-9cda-dbbac86d6772
exl-id: ef5160ac-5a73-4433-b217-1bd990f8456b
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 100%

---

# 사용자의 옵트 상태 설정{#setting-the-user-s-opt-status}

이 정보는 GDPR 데이터 삭제를 요청하는 데 도움이 됩니다.

>[!IMPORTANT]
>
>Android SDK 4.15부터 개인 정보 상태를 `unknown`으로 설정하면 Audience Manager 및 Experience Cloud ID 히트 수가 보관됩니다.

다음 설정을 사용하여 Analytics, Target 및 Audience Manager 활동을 장치에서 허용할지 여부를 제어할 수 있습니다.

* [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md)의 `privacyDefault`.

   이 설정은 코드에서 변경될 때까지 유지되는 초기 설정을 제어합니다.

* `Config.setPrivacyStatus` 메서드.

   이 방법을 사용하여 개인정보 설정을 변경한 후에는 다시 변경하거나 앱을 제거하고 다시 설치할 때까지 변경 사항이 적용됩니다. 방법에 대한 자세한 내용은 [구성 방법](/help/android/configuration/methods.md)을 참조하십시오.

다음 표는 각 개인 정보 상태에 대해 설명합니다.

* **옵트인**

   * **Analytics**: 히트가 전송됩니다.
   * **Target**: Mbox 요청을 전송합니다.
   * **Audience Manager**: 신호 및 ID 동기화를 전송합니다.
   * JSON 구성 파일의 값: `optedin`
   * `setPrivacyStatus`의 값: `MOBILE_PRIVACY_STATUS_OPT_IN`

* **옵트아웃**

   * **Analytics**: 히트가 삭제됩니다.
   * **Target**: Mbox 요청을 허용하지 않습니다.
   * **Audience Manager**: 신호 및 ID 동기화를 허용하지 않습니다.
   * JSON 구성 파일의 값: `optedout`
   * `setPrivacyStatus`의 값: `MOBILE_PRIVACY_STATUS_OPT_OUT`

* **알 수 없음**

   * **Analytics**: 오프라인 추적이 **활성화**&#x200B;되어 있을 경우, 개인 정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트가 삭제됨)으로 변경될 때까지 히트가 저장됩니다.

      오프라인 추적이 활성화되어 있지 <b>않을</b> 경우, 개인 정보 상태가 옵트인으로 변경될 때까지 히트를 삭제합니다.
   * **Target**: Mbox 요청을 전송합니다.
   * **Audience Manager**: 신호 및 ID 동기화를 전송합니다.
   * JSON 구성 파일의 값: `optunknown`
   * `setPrivacyStatus`의 값: `MOBILE_PRIVACY_STATUS_UNKNOWN`

## 예시 {#section_128AC455EE024193B5D4E5A565B53D00}

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
