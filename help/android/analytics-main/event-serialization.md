---
description: 이벤트 직렬화는 처리 규칙에서 지원되지 않습니다. Mobile SDK에서는, 서버 호출 시 직접 직렬화된 이벤트를 설정하려면 컨텍스트 데이터 매개 변수의 특수 구문을 사용해야 합니다.
keywords: android;라이브러리;모바일;sdk
solution: Experience Cloud,Analytics
title: 이벤트 정리
topic-fix: Developer and implementation
uuid: acdeda16-ab83-4cfc-907d-33448b801b31
exl-id: 03556912-fdcc-402e-b1de-233771f4e719
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 100%

---

# 이벤트 정리 {#event-serialization}

이벤트 직렬화는 처리 규칙에서 지원되지 않습니다. Mobile SDK에서는, 서버 호출 시 직접 직렬화된 이벤트를 설정하려면 컨텍스트 데이터 매개 변수의 특수 구문을 사용해야 합니다.

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
