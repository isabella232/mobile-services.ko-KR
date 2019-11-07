---
description: 시간 작업을 사용하면 작업의 시작과 끝 사이의 인앱 시간 및 총 시간을 측정할 수 있습니다. SDK는 각 세션에서 시간의 길이를 계산하고 작업 완료까지 걸리는 총 시간을 모든 세션에 걸쳐 계산합니다. 시간 작업을 사용하여 세그먼트를 정의하고 구매, 전달 수준, 체크아웃 플로우 등에 걸리는 시간을 비교할 수 있습니다.
seo-description: 시간 작업을 사용하면 작업의 시작과 끝 사이의 인앱 시간 및 총 시간을 측정할 수 있습니다. SDK는 각 세션에서 시간의 길이를 계산하고 작업 완료까지 걸리는 총 시간을 모든 세션에 걸쳐 계산합니다. 시간 작업을 사용하여 세그먼트를 정의하고 구매, 전달 수준, 체크아웃 플로우 등에 걸리는 시간을 비교할 수 있습니다.
seo-title: 시간 작업
solution: Marketing Cloud,Analytics
title: 시간 작업
topic: 개발자 및 구현
uuid: dbcbac5a-6345-49f6-b050-0db05292f005
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# 시간 작업 {#timed-actions}

시간 작업을 사용하면 작업의 시작과 끝 사이의 인앱 시간 및 총 시간을 측정할 수 있습니다. SDK는 각 세션에서 시간의 길이를 계산하고 작업 완료까지 걸리는 총 시간을 모든 세션에 걸쳐 계산합니다. 시간 작업을 사용하여 세그먼트를 정의하고 구매, 전달 수준, 체크아웃 플로우 등에 걸리는 시간을 비교할 수 있습니다.

시간 작업에 대해 보고되는 지표는 다음과 같습니다.

* 전체 세션 시작 및 종료 사이의 총 인앱 시간(초)
* 시작 및 종료 간 총 클록 시간 (초)

콜백을 선택적으로 사용하면 시간 작업이 완료될 때 추가 작업을 실시할 수 있습니다.

* 코드 및 임의의 논리를 실행합니다. 이때 논리는 기간 결과를 기반으로 하는 사용자 지정 논리 옵션입니다.
* 지속 시간을 전달하기 전에 컨텍스트 데이터를 추가합니다.
* 아직 전송하지 않은 히트와 기간을 취소합니다.

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

