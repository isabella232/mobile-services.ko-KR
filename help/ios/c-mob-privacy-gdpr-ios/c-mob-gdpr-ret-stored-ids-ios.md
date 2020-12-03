---
description: 이 정보는 iOS 앱에서 GDPR 데이터 액세스 요청으로 로컬에 저장된 Experience Cloud SDK ID를 검색하는 데 도움이 됩니다.
seo-description: 이 정보는 iOS 앱에서 GDPR 데이터 액세스 요청으로 로컬에 저장된 Experience Cloud SDK ID를 검색하는 데 도움이 됩니다.
seo-title: 저장된 식별자 검색
title: 저장된 식별자 검색
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 64%

---


# 저장된 식별자 검색{#retrieving-stored-identifiers}

이 정보는 iOS 앱에서 GDPR 데이터 액세스 요청으로 로컬에 저장된 Experience Cloud SDK ID를 검색하는 데 도움이 됩니다.

GDPR에 대한 자세한 내용은 [GDPR 및 비즈니스를 참조하십시오](https://www.adobe.com/kr/privacy/general-data-protection-regulation.html).

>[!IMPORTANT]
>
>`getAllIdentifiersAsync` 메서드는 Experience Cloud SDK에 저장된 ID를 검색합니다. You must call this method **before** the user opts-out.

Experience Cloud SDK ID(해당되는 경우)는 로컬에 저장되고 다음을 포함할 수 있는 JSON 문자열에 반환됩니다.

* 회사 컨텍스트 - IMS 조직 ID
* 사용자 ID
* Experience Cloud iD(MID)(이전의 Marketing Cloud ID라고 함)
* 통합 코드(ADID, 푸시 ID)
* 데이터 소스 ID(DPID, DPUUID)
* Analytics ID(AVID, AID, VID 및 관련 RSID)
* Target 레거시 ID(TNTID, TNT3rdpartyID)
* Audience Manager ID(UUID)

다음은 iOS의 `ADBMobile getAllIdentifiersAsync` 메서드에 대한 예입니다.

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```

