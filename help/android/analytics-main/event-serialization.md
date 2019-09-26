---
description: 처리 규칙에서는 이벤트 일련화가 지원되지 않습니다. Mobile SDK에서 컨텍스트 데이터 매개 변수에 특수 구문을 사용하여 서버 호출에 대해 직접 이벤트 일련화를 설정해야 합니다.
keywords: android;library;mobile;sdk
seo-description: 처리 규칙에서는 이벤트 일련화가 지원되지 않습니다. Mobile SDK에서 컨텍스트 데이터 매개 변수에 특수 구문을 사용하여 서버 호출에 대해 직접 이벤트 일련화를 설정해야 합니다.
seo-title: 이벤트 정리
solution: Marketing Cloud,Analytics
title: 이벤트 정리
topic: 개발자 및 구현
uuid: acdeda16-ab83-4cfc-907d-33448b801b31
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# 이벤트 정리 {#event-serialization}

처리 규칙에서는 이벤트 일련화가 지원되지 않습니다. Mobile SDK에서 컨텍스트 데이터 매개 변수에 특수 구문을 사용하여 서버 호출에 대해 직접 이벤트 일련화를 설정해야 합니다.

```java
cdata.put("&&events", "event1:12341234");
```

예:

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
 
// add events 
cdata.put("&&events", "event1:12341234"); 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("action", cdata); 
// trackState example: 
Analytics.trackState("State Name", cdata);
```

