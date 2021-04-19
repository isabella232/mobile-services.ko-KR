---
description: 이벤트 직렬화는 처리 규칙에서 지원되지 않습니다. 모바일 SDK에서는 컨텍스트 데이터 매개 변수 내의 특수 구문을 사용하여 서버 호출에서 직접 직렬화된 이벤트를 설정해야 합니다.
seo-description: 이벤트 직렬화는 처리 규칙에서 지원되지 않습니다. 모바일 SDK에서는 컨텍스트 데이터 매개 변수 내의 특수 구문을 사용하여 서버 호출에서 직접 직렬화된 이벤트를 설정해야 합니다.
seo-title: 이벤트 정리
solution: Experience Cloud,Analytics
title: 이벤트 정리
topic-fix: Developer and implementation
uuid: 7220a001-1174-4013-91ff-e8603d8ab265
exl-id: 9cb8d739-8b77-4fe7-8592-22e8cff172d4
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 30%

---

# 이벤트 정리 {#event-serialization}

이벤트 직렬화는 처리 규칙에서 지원되지 않습니다. 모바일 SDK에서는 서버 호출에서 직접 직렬화된 이벤트를 설정하려면 컨텍스트 데이터 매개 변수의 특수 구문을 사용해야 합니다.

```js
cdata["&&events"] = "event1:12341234";
```

예:

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add events 
cdata["&&events"] = "event1:12341234"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("action", cdata); 
// trackState example: 
ADB.Analytics.trackState("State Name", cdata);
```
