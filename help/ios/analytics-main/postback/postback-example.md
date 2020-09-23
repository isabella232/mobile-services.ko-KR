---
description: 포스트백 기능에 대한 정의 및 소스 코드 예입니다.
seo-description: 포스트백 기능에 대한 정의 및 소스 코드 예입니다.
seo-title: 포스트백 예시
solution: Experience Cloud,Analytics
title: 포스트백 예시
topic: Developer and implementation
uuid: 809c5646-7a80-40df-984b-0af89d854259
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 100%

---


# 포스트백 예시 {#postback-example}

포스트백 기능에 대한 정의 및 소스 코드 예입니다.

>[!CAUTION]
>
>이 예는 정보 제공 용도로만 제공됩니다. `ADBMobileConfig.json` 파일은 Adobe Mobile UI에서 구성해야 하며 수동으로 수정하면 안 됩니다. 수동으로 편집한 구성 파일은 원격 메시지 구성이 활성화되었을 경우 위험할 수 있습니다.

## ADBMobileConfig.json 정의 {#section_0F6EC001AB6D488E815F50C7F5DA022E}

```js
"messages": [ 
    { 
        "messageId": "79ae37c9-89b9-465e-af7f-d3351771f1dc", 
        "template": "callback", 
        "payload": {  
            "templateurl": "https://my.server.com/?user={user.name}&zip={user.zip}&c16={%sdkver%}&c27=cln,{a.PrevSessionLength}", 
            "templatebody": "c2RrdmVyPXslc2RrdmVyJX0mY2I9eyVjYWNoZWJ1c3QlfSZjbGllbnRJZD17bi5jbGllbnQuaWR9JnRzPXsldGltZXN0YW1wVSV9JnRzej17JXRpbWVzdGFtcFolfQ==", 
            "contenttype": "application/x-www-form-urlencoded",  
            "timeout": 4 
        }, 
        "showOffline": true, 
        "showRule": "always", 
        "endDate": 2524730400, 
        "startDate": 0, 
        "audiences": [], 
        "triggers": [ 
            { 
                "key": "pageName", 
                "matches": "eq", 
                "values": [ 
                    "MainMenu" 
                ] 
            } 
        ] 
    } 
] 
```

## 코드 샘플 {#section_8169B88A2C634CB788DA574EE8C4B1DC}

```objective-c
NSDictionary *contextData = @{@"user.name":@"bob", @"user.zip":@"90210"}; 
[ADBMobile trackState:@"MainMenu" data:contextData];
```

상태가 `“MainMenu”`이므로 이 추적 호출은 위의 포스트백 메시지를 트리거합니다. 이 URL은 모든 템플릿 변수를 히트의 값으로 대체합니다. 사용자의 이전 세션이 132초이고 사용자가 iOS SDK 버전 4.6.0을 사용하고 있다고 가정할 때 다음은 결과 URL의 예입니다.

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-iOS&c27=cln,132`
