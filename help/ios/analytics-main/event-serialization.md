---
description: 이벤트 직렬화는 처리 규칙에서 지원되지 않습니다. Mobile SDK에서는, 서버 호출 시 직접 직렬화된 이벤트를 설정하려면 컨텍스트 데이터 매개 변수의 특수 구문을 사용해야 합니다.
seo-description: 이벤트 직렬화는 처리 규칙에서 지원되지 않습니다. Mobile SDK에서는, 서버 호출 시 직접 직렬화된 이벤트를 설정하려면 컨텍스트 데이터 매개 변수의 특수 구문을 사용해야 합니다.
seo-title: 이벤트 정리
solution: Experience Cloud,Analytics
title: 이벤트 정리
topic: Developer and implementation
uuid: 19a27df4-0998-403d-800c-26ff61149208
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 100%

---


# 이벤트 정리 {#event-serialization}

이벤트 직렬화는 처리 규칙에서 지원되지 않습니다. Mobile SDK에서는, 서버 호출 시 직접 직렬화된 이벤트를 설정하려면 컨텍스트 데이터 매개 변수의 특수 구문을 사용해야 합니다.

```objective-c
[contextData setObject:@"eventN:serial number" forKey:@"&&events"];
```

예:

```objective-c
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
 
// add events 
[contextData setObject:@"event1:12341234" forKey:@"&&events"]; 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"action" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"State Name" data:contextData]; 
```

