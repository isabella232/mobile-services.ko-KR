---
description: 이 정보를 사용하면 포스트백과 포스트백의 작동 방식에 대해 이해할 수 있습니다.
keywords: android;library;mobile;sdk
seo-description: 이 정보를 사용하면 포스트백과 포스트백의 작동 방식에 대해 이해할 수 있습니다.
seo-title: 포스트백 예시
solution: Marketing Cloud,Analytics
title: 포스트백 예시
topic: 개발자 및 구현
uuid: 8010cd00-d42b-4e16-8403-692fab2550f1
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Postbacks example {#postbacks-example}

이 정보를 사용하여 포스트백이 무엇이고 포스트백이 어떻게 작동하는지 이해할 수 있습니다.

>[!CAUTION]
>
>이 예는 정보 제공용으로만 제공됩니다. `ADBMobileConfig.json` 파일은 Adobe Mobile UI에서 구성해야 하며 수동으로 수정하면 안 됩니다. 수동으로 편집한 구성 파일은 원격 메시지 구성이 활성화되었을 경우 위험할 수 있습니다.

## `ADBMobileConfig.json` 정의 {#section_8751E8176F3546C09420341A39758AFF}

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

## Code sample {#section_D063DE82976D4EDEA97E804BD1C4718F}

```js
HashMap<String, Object> contextData = new HashMap<String, Object>(); 
contextData.put("user.name", "bob"); 
contextData.put("user.zip", "90210"); 
Analytics.trackState("MainMenu", contextData);
```

Because its state is `“MainMenu”`, this tracking call triggers the above postback message. 이 URL은 모든 템플릿 변수를 히트의 값으로 대체하게 됩니다. 사용자의 이전 세션이 132초이고 사용자가 Android SDK 버전 4.6.0을 사용하고 있다고 가정할 경우 결과 URL은 다음과 같습니다.

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-AN&c27=cln,132`
