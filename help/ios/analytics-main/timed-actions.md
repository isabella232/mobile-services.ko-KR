---
description: 시간 작업을 사용하면 작업의 시작과 끝 사이의 인앱 시간 및 총 시간을 측정할 수 있습니다. 이 SDK는 각 세션의 시간과 작업을 완료하는 데 소요되는 총 세션 시간을 계산합니다. 시간 작업을 사용하여 세그먼트를 정의하고 구매, 전달 수준, 체크아웃 플로우 등에 걸리는 시간을 비교할 수 있습니다.
solution: Experience Cloud,Analytics
title: 시간 작업
topic-fix: Developer and implementation
uuid: dbcbac5a-6345-49f6-b050-0db05292f005
exl-id: 3499766b-55f6-4861-8291-2269d56ba983
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 100%

---

# 시간 작업 {#timed-actions}

시간 작업을 사용하면 작업의 시작과 끝 사이의 인앱 시간 및 총 시간을 측정할 수 있습니다. 이 SDK는 각 세션의 시간과 작업을 완료하는 데 소요되는 총 세션 시간을 계산합니다. 시간 작업을 사용하여 세그먼트를 정의하고 구매, 전달 수준, 체크아웃 플로우 등에 걸리는 시간을 비교할 수 있습니다.

Timed Action에 대해 다음 지표가 보고됩니다.

* 시작 및 종료 사이의 앱의 총 시간(초) - 세션 간
* 시작과 종료 사이의 총 시간(초)(시계 시간)

선택적 콜백을 사용하면 Timed Action이 완료될 때 추가 작업을 수행할 수 있습니다.

* 코드를 실행하고 임의 로직(기간 결과 기반 선택적 사용자 지정 로직)을 추가할 수 있습니다.
* 지속 시간을 전달하기 전에 컨텍스트 데이터를 추가합니다.
* 아직 전송되지 않은 히트와 기간을 취소합니다.

## 시간 작업 추적 {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 [핵심 구현 및 라이프사이클](/help/ios/getting-started/dev-qs.md)에서 *프로젝트에 SDK 및 구성 파일 추가*&#x200B;를 참조하십시오.
1. 라이브러리를 가져옵니다:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. `trackTimedActionStart`를 호출하고 시간 작업의 이름과 컨텍스트 데이터 옵션을 제공합니다.

   ```objective-c
   [ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                               data:@{@"ExperienceName" : experience}];
   ```

1. (선택 사항) 언제든지 컨텍스트 데이터를 추가하기 위해 `trackTimedActionUpdate`를 시간 작업 이름으로 호출할 수 있습니다.

   ```objective-c
   [ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                                data:@{@"myapp.ImageLiked" : imageName}];
   ```

1. 이벤트가 완료되면 `trackTimedActionEnd`를 호출하고 시간 작업의 이름과 `TimedActionBlock`(콜백)을 전달하여 모든 데이터를 조회하고 지속 시간을 계산합니다.

   시간 이벤트 지표는 자동 보고를 위해 모바일 솔루션에 저장됩니다.

   ```objective-c
   [ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                            logic:nil];
   ```

## 추가 데이터 보내기 {#section_3EBE813E54A24F6FB669B2478B5661F9}

시간 작업 이름 외에도 작업 시작 및 작업 업데이트 호출로 추가 컨텍스트 데이터를 전송할 수 있습니다.

```objective-c
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"myapp.ImageLiked" : imageName}];
```

컨텍스트 데이터 사용자 지정 변수에 매핑해야 합니다.

![](assets/map-variable-context-ltv.png)

## 예 {#section_7BA344B8BD4F48DCBAE27AC9320CBCEA}

```objective-c
// Timed Action Start Example 
[ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                            data:@{@"ExperienceName" : experience}];

// Timed Action Update Example 
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"ImageLiked" : imageName}];

// Timed Action End Example 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:nil]; 
 
// Timed Action End Example with Callback 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:^BOOL(NSTimeInterval inAppDuration,  
                                     NSTimeInterval totalDuration,  
                                     NSMutableDictionary *data) { 
                                        [data setObject:@"PurchaseItem" forKey:@"Item453"]; 
                                        return YES; //return YES to send the hit, NO to cancel 
                                     }];
```
