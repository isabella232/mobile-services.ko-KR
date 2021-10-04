---
description: 이 정보는 Android 앱에서 GDPR 데이터 액세스 요청으로 로컬에 저장된 SDK ID를 검색하는 데 도움이 됩니다.
title: 저장된 식별자 검색
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
exl-id: 86c990d8-334b-4003-b0ac-d5404cb598e4
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 64%

---

# 저장된 식별자 검색{#retrieving-stored-identifiers}

이 정보는 Android 앱에서 GDPR 데이터 액세스 요청으로 로컬에 저장된 SDK ID를 검색하는 데 도움이 됩니다.

>[!IMPORTANT]
>
>`getAllIdentifiersAsync` 메서드는 SDK에 저장된 ID를 검색합니다. 사용자가 옵트아웃하기 전에 **을 호출해야 합니다.**

SDK ID(해당하는 경우)는 로컬에 저장되고 다음을 포함할 수 있는 JSON 문자열로 반환됩니다.

* 회사 컨텍스트 - IMS 조직 ID
* 사용자 ID
* Experience Cloud iD(MID), 이전에 Marketing Cloud ID라고 함
* 통합 코드(ADID, 푸시 ID)
* 데이터 소스 ID(DPID, DPUUID)
* Analytics ID(AVID, AID, VID 및 관련 RSID)
* Target 기존 ID(TNTID, TNT3rdpartyID)
* Audience Manager ID(UUID)

다음은 Android의 `ADBMobile getAllIdentifiersAsync` 메서드에 대한 예입니다.

```java
Config.getAllIdentifiersAsync(new ConfigCallback<String>() { 
     @Override 
     public void call(String identitiesJson) {                 
         Log.d("ADBMobile Identities", identitiesJson); 
     } 
});
```
