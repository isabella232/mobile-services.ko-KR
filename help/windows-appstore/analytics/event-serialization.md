---
description: 이벤트 직렬화는 처리 규칙에서 지원되지 않습니다. Mobile SDK에서는, 서버 호출 시 직접 직렬화된 이벤트를 설정하려면 컨텍스트 데이터 매개 변수 내의 특수 구문을 사용해야 합니다.
solution: Experience Cloud,Analytics
title: 이벤트 정리
topic-fix: Developer and implementation
uuid: a5966d05-e218-446f-9f19-8664a84b74cd
exl-id: 42ea5e0f-a69e-44ab-aa4e-bbec27815cc8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '70'
ht-degree: 31%

---

# 이벤트 정리{#event-serialization}

이벤트 직렬화는 처리 규칙에서 지원되지 않습니다. Mobile SDK에서는, 서버 호출 시 직접 직렬화된 이벤트를 설정하려면 컨텍스트 데이터 매개 변수의 특수 구문을 사용해야 합니다.

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
