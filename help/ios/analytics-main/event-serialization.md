---
description: 처리 규칙에서는 이벤트 일련화가 지원되지 않습니다. Mobile SDK에서 컨텍스트 데이터 매개 변수에 특수 구문을 사용하여 서버 호출에 대해 직접 이벤트 일련화를 설정해야 합니다.
seo-description: 처리 규칙에서는 이벤트 일련화가 지원되지 않습니다. Mobile SDK에서 컨텍스트 데이터 매개 변수에 특수 구문을 사용하여 서버 호출에 대해 직접 이벤트 일련화를 설정해야 합니다.
seo-title: 이벤트 정리
solution: Marketing Cloud,Analytics
title: 이벤트 정리
topic: 개발자 및 구현
uuid: 19a27df4-0998-403d-800c-26ff61149208
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# 이벤트 정리 {#event-serialization}

처리 규칙에서는 이벤트 일련화가 지원되지 않습니다. Mobile SDK에서 컨텍스트 데이터 매개 변수에 특수 구문을 사용하여 서버 호출에 대해 직접 이벤트 일련화를 설정해야 합니다.

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

