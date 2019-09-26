---
description: 처리 규칙에서는 이벤트 일련화가 지원되지 않습니다. Mobile SDK에서 컨텍스트 데이터 매개 변수에 특수 구문을 사용하여 서버 호출에 대해 직접 이벤트 일련화를 설정해야 합니다.
seo-description: 처리 규칙에서는 이벤트 일련화가 지원되지 않습니다. Mobile SDK에서 컨텍스트 데이터 매개 변수에 특수 구문을 사용하여 서버 호출에 대해 직접 이벤트 일련화를 설정해야 합니다.
seo-title: 이벤트 정리
solution: Marketing Cloud,Analytics
title: 이벤트 정리
topic: 개발자 및 구현
uuid: a5966d05-e218-446f-9f19-8664a84b74cd
translation-type: tm+mt
source-git-commit: 4faf66df50c8b65198fd139bb15927fc2c2849bc

---


# 이벤트 정리{#event-serialization}

처리 규칙에서는 이벤트 일련화가 지원되지 않습니다. 모바일 SDK에서는 컨텍스트 데이터 매개 변수에 특수 구문을 사용하여 서버 호출에서 직접 직렬화된 이벤트를 설정해야 합니다.

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

