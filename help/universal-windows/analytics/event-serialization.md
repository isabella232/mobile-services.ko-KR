---
description: 처리 규칙에서는 이벤트 일련화가 지원되지 않습니다. Mobile SDK에서 컨텍스트 데이터 매개 변수에 특수 구문을 사용하여 서버 호출에 대해 직접 이벤트 일련화를 설정해야 합니다.
seo-description: 처리 규칙에서는 이벤트 일련화가 지원되지 않습니다. Mobile SDK에서 컨텍스트 데이터 매개 변수에 특수 구문을 사용하여 서버 호출에 대해 직접 이벤트 일련화를 설정해야 합니다.
seo-title: 이벤트 정리
solution: Marketing Cloud, Analytics
title: 이벤트 정리
topic: 개발자 및 구현
uuid: 7220 A 001-1174-4013-91 FF-E 8603 D 8 AB 265
translation-type: tm+mt
source-git-commit: f5ba33fe805c502b8ae91ddafcaa0b57e68704b8

---


# 이벤트 정리 {#event-serialization}

처리 규칙에서는 이벤트 일련화가 지원되지 않습니다. Mobile SDK 에서는 컨텍스트 데이터 매개 변수에서 특수 구문을 사용하여 직렬화된 이벤트를 서버 호출에서 직접 설정해야 합니다.

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

