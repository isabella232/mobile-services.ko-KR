---
description: 이 정보를 사용하면 포스트백과 포스트백의 작동 방식에 대해 이해할 수 있습니다.
keywords: android;라이브러리;모바일;sdk
solution: Experience Cloud Services,Analytics
title: 포스트백 예시
topic-fix: Developer and implementation
uuid: 8010cd00-d42b-4e16-8403-692fab2550f1
exl-id: 2ff41066-e2ee-425f-8aff-e5e3f3e5f0f5
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 100%

---

# 포스트백 예시 {#postbacks-example}

이 정보를 사용하면 포스트백과 포스트백의 작동 방식에 대해 이해할 수 있습니다.

>[!CAUTION]
>
>이 예는 정보 제공 용도로만 제공됩니다. `ADBMobileConfig.json` 파일은 Adobe Mobile UI에서 구성해야 하며 수동으로 수정하면 안 됩니다. 수동으로 편집한 구성 파일은 원격 메시지 구성이 활성화되었을 경우 위험할 수 있습니다.

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

## 코드 샘플 {#section_D063DE82976D4EDEA97E804BD1C4718F}

```js
HashMap<String, Object> contextData = new HashMap<String, Object>(); 
contextData.put("user.name", "bob"); 
contextData.put("user.zip", "90210"); 
Analytics.trackState("MainMenu", contextData);
```

상태가 `"MainMenu"`이므로 이 추적 호출은 위의 포스트백 메시지를 트리거합니다. 이 URL은 모든 템플릿 변수를 히트의 값으로 대체하게 됩니다. 사용자의 이전 세션이 132초였고 Android SDK 버전 4.6.0을 사용 중이라고 가정할 경우 그 결과로 나타나는 URL은 다음과 같습니다.

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-AN&c27=cln,132`
