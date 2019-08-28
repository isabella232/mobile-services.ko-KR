---
description: 포스트백 기능에 대한 정의 및 소스 코드 예입니다.
seo-description: 포스트백 기능에 대한 정의 및 소스 코드 예입니다.
seo-title: 포스트백 예시
solution: Marketing Cloud, Analytics
title: 포스트백 예시
topic: 개발자 및 구현
uuid: 809 c 5646-7 a 80-40 df -984 b -0 af 89 d 854259
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Postback example {#postback-example}

포스트백 기능에 대한 정의 및 소스 코드 예입니다.

>[!CAUTION]
>
>이 예는 정보용으로만 제공됩니다. `ADBMobileConfig.json` 파일은 Adobe Mobile UI에서 구성해야 하며 수동으로 수정하면 안 됩니다. 수동으로 편집한 구성 파일은 원격 메시지 구성이 활성화되었을 경우 위험할 수 있습니다.

## ADBMobileConfig.json definition {#section_0F6EC001AB6D488E815F50C7F5DA022E}

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

## Code sample {#section_8169B88A2C634CB788DA574EE8C4B1DC}

```objective-c
NSDictionary *contextData = @{@"user.name":@"bob", @"user.zip":@"90210"}; 
[ADBMobile trackState:@"MainMenu" data:contextData];
```

Because its state is `“MainMenu”`, this tracking call triggers the above postback message. URL는 모든 템플릿 변수를 히트의 값으로 대체합니다. 사용자의 이전 세션이 132 초 길었고 해당 사용자가 iOS SDK 버전 4.6.0를 사용하는 경우, 결과 URL의 예는 다음과 같습니다.

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-iOS&c27=cln,132`
