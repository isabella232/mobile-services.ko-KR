---
description: 이벤트 직렬화는 처리 규칙에서 지원되지 않습니다. 모바일 SDK에서는 컨텍스트 데이터 매개 변수 내의 특수 구문을 사용하여 서버 호출에서 직접 직렬화된 이벤트를 설정해야 합니다.
seo-description: 이벤트 직렬화는 처리 규칙에서 지원되지 않습니다. 모바일 SDK에서는 컨텍스트 데이터 매개 변수 내의 특수 구문을 사용하여 서버 호출에서 직접 직렬화된 이벤트를 설정해야 합니다.
seo-title: 이벤트 정리
solution: Experience Cloud,Analytics
title: 이벤트 정리
topic: Developer and implementation
uuid: a5966d05-e218-446f-9f19-8664a84b74cd
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 30%

---


# 이벤트 정리{#event-serialization}

이벤트 직렬화는 처리 규칙에서 지원되지 않습니다. 모바일 SDK에서는 컨텍스트 데이터 매개 변수의 특수 구문을 사용하여 서버 호출에서 직접 직렬화된 이벤트를 설정해야 합니다.

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

