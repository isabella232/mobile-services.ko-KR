---
description: 이 정보는 iOS 앱에서 GDPR 데이터 액세스 요청으로 로컬에 저장된 Experience Cloud SDK ID를 검색하는 데 도움이 됩니다.
title: 저장된 식별자 검색
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
exl-id: ec8592af-fb08-4ab3-99a1-51ac5697a3d8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 60%

---

# 저장된 식별자 검색{#retrieving-stored-identifiers}

이 정보는 iOS 앱에서 GDPR 데이터 액세스 요청으로 로컬에 저장된 Experience Cloud SDK ID를 검색하는 데 도움이 됩니다.

GDPR에 대한 자세한 내용은 [GDPR 및 비즈니스](https://www.adobe.com/kr/privacy/general-data-protection-regulation.html)를 참조하십시오.

>[!IMPORTANT]
>
>`getAllIdentifiersAsync` 메서드는 Experience Cloud SDK에 저장된 ID를 검색합니다. 사용자가 옵트아웃하기 전에 **을 호출해야 합니다.**

Experience Cloud SDK ID(해당하는 경우)는 로컬에 저장되고 JSON 문자열로 반환되며, 여기에는 다음 항목이 포함될 수 있습니다.

* 회사 컨텍스트 - IMS 조직 ID
* 사용자 ID
* Experience Cloud iD(MID), 이전에 Marketing Cloud ID라고 함
* 통합 코드(ADID, 푸시 ID)
* 데이터 소스 ID(DPID, DPUUID)
* Analytics ID(AVID, AID, VID 및 관련 RSID)
* Target 기존 ID(TNTID, TNT3rdpartyID)
* Audience Manager ID(UUID)

다음은 iOS의 `ADBMobile getAllIdentifiersAsync` 메서드에 대한 예입니다.

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```
