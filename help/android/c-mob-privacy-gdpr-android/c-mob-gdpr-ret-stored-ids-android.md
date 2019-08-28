---
description: 이 정보는 Android 앱에서 GDPR 데이터 액세스 요청으로 로컬에 저장된 SDK ID를 검색하는 데 도움이 됩니다.
seo-description: 이 정보는 Android 앱에서 GDPR 데이터 액세스 요청으로 로컬에 저장된 SDK ID를 검색하는 데 도움이 됩니다.
seo-title: 저장된 식별자 검색
title: 저장된 식별자 검색
uuid: 6 FD 3 D 202-B 0 A 1-4 C 80-96 F 4-369 FC 24 AC 0 A 3
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Retrieving stored identifiers{#retrieving-stored-identifiers}

이 정보는 Android 앱에서 GDPR 데이터 액세스 요청으로 로컬에 저장된 SDK ID를 검색하는 데 도움이 됩니다.

>[!IMPORTANT]
>
>`getAllIdentifiersAsync` 이 메서드는 SDK에 저장된 ID를 검색합니다. 사용자가 옵트아웃하기 **전에** 이 메서드를 호출해야 합니다.

SDK ID(해당하는 경우)는 로컬로 저장되며, JSON 문자열에 반환됩니다. 이 문자열에는 다음이 포함될 수 있습니다.

* 회사 컨텍스트 - IMS 조직 ID
* 사용자 ID
* Experience Cloud iD(MID)(이전의 Marketing Cloud ID)
* 통합 코드(ADID, 푸시 ID)
* 데이터 소스 ID(DPID, DPUUID)
* Analytics ID(AVID, AID, VID 및 연관된 RSID)
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
