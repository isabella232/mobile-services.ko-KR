---
description: 다음은 iOS 라이브러리에서 제공하는 Adobe Analytics 메서드 목록입니다.
seo-description: 다음은 iOS 라이브러리에서 제공하는 Adobe Analytics 메서드 목록입니다.
seo-title: 분석 방법
solution: Marketing Cloud,Analytics
title: 분석 방법
topic: 개발자 및 구현
uuid: d49fe6de-cb32-4b96-9891-c567310e59a6
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Analytics methods {#analytics-methods}

다음은 iOS 라이브러리에서 제공하는 Adobe Analytics 메서드 목록입니다.

The SDK currently has support for multiple Adobe Experience Cloud Solutions, including Analytics, Target, Audience Manager, and the Adobe Experience Platform Identity Service. 메서드에는 솔루션에 따라 접두사가 붙습니다. Experience Cloud ID 메서드 앞에는 `track`이 붙습니다.

이러한 각 메서드는 Adobe Analytics 보고서 세트로 데이터를 전송하는 데 사용됩니다.

* **trackState:&#x200B;data:**

   States are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on. 이 상태는 웹 사이트의 페이지와 유사하며 `trackState` 호출은 페이지 보기를 증가시킵니다. `state`가 비어 있는 경우 보고서에 *app name app version (build)*&#x200B;이 표시됩니다. 보고서에 이 값이 표시되면 각각의 `state` 호출에서 `trackState`를 반드시 설정해야 합니다.

   >[!TIP]
   >
   >이것은 페이지 보기를 증가시키는 유일한 추적 호출입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void)  trackState:(NSString  *)state
                      data:(NSDictionary  *)data;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile  trackState:@"loginScreen"
                        data:nil]; 
      ````

* **trackAction:&#x200B;data:**

   앱의 작업을 추적합니다. Actions that you want to measure, such as `logons`, `banner taps`, `feed subscriptions`, and other metrics, occur in your app.

   >[!TIP]
   >
   >If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      +  (void)  trackAction:(NSString  *)action
                        data:(NSDictionary  *)data; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile  trackAction:@"heroBannerTouched"
                         data:nil]; 
      ```

* **trackingIdentifier**

   분석 추적 식별자를 검색합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (NSString *) trackingIdentifier; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSString *trackingId = [ADBMobile trackingIdentifier];
      ```

* **trackActionFromBackground:&#x200B;data:**

   특정 시나리오에 대한 라이프사이클 이벤트 실행을 억제하는 작업이 백그라운드에서 발생하면 해당 작업을 추적합니다.

   >[!TIP]
   >
   >This method should only be called in code that runs while your app is in the background.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
       +  (void)  trackActionFromBackground:(NSString  *)action
                                       data:(NSDictionary  *)data; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile  trackActionFromBackground:@"downloadedUpdate"
                                       data:nil];
      ```

* **trackLocation:&#x200B;data:**

   현재 xy 좌표를 보냅니다. 또한 `ADBMobileConfig.json` 파일에서 정의된 관심 영역을 사용하여 매개 변수로 제공된 위치가 POI 내에 있는지 파악합니다. 정의된 POI 내에 현재 좌표가 있는 경우 컨텍스트 데이터 변수를 채워 `trackLocation` 호출로 전송합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      +  (void)  trackLocation:(CLLocation  *)location
                          data:(NSDictionary  *)data; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile  trackLocation:userLocation
                           data:nil]; 
      ```

* **trackBeacon:&#x200B;data:**

   사용자가 비콘 근접 위치에 들어오면 추적합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      +  (void)  trackLocation:(CLBeacon  *)beacon
                          data:(NSDictionary  *)data;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile  trackBeacon:beacon
                         data:nil];
      ```

* **trackingClearCurrentBeacon**

   사용자가 비콘 근접 위치를 떠난 후 비콘 데이터를 지웁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) trackingClearCurrentBeacon;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile trackingClearCurrentBeacon];
      ```

* **trackLifetimeValueIncrease:&#x200B;data:**

   사용자의 라이프타임 값에 `amount`를 추가합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
       +  (void)  trackLifetimeValueIncrease:(NSDecimalNumber  *)amount
                                       data:(NSDictionary  *)data; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile  trackLifetimeValueIncrease:30
                                         data:nil];
      ```

* **trackTimedActionStart:&#x200B;data:**

   `action` 이름으로 시간 작업을 시작합니다.. 이미 시작한 작업에 대해 이 메서드를 호출하는 경우 이전 시간 제한 작업을 덮어씁니다.

   >[!TIP]
   >
   >이 호출은 히트를 전송하지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      +  (void)  trackTimedActionStart:(NSString  *)action
                                  data:(NSDictionary  *)data; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile  trackTimedActionStart:@"cartToCheckout"
                                  data:nil]; 
      ```

* **trackTimedActionUpdate:&#x200B;data:**

   `data`를 전달하여 제공된 `action`과 연관된 컨텍스트 데이터를 업데이트합니다. 전달된 `data`는 기존 작업 데이터에 추가되며 동일한 키가 `action`에 이미 정의되어 있으면 데이터를 덮어씁니다.

   >[!TIP]
   >
   >이 호출은 히트를 전송하지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
       +  (void)  trackTimedActionUpdate:(NSString  *)action
                                    data:(NSDictionary  *)data; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile  trackTimedActionUpdate:@"cartToCheckout"
                                    data:@{@"quantity":@"3"}];
      ```

* **trackTimedActionEnd:&#x200B;logic:**

   시간 제한 작업을 종료합니다. `block`을 지정하면 최종 시간 값에 액세스할 수 있고 최종 히트를 전송하기 전에 `data`를 조작할 수 있습니다.

   >[!TIP]
   >
   >If you provide `block`, you must return `YES` to send a hit. Passing in `nil` for `block` sends the final hit.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      +  (void)  trackTimedActionEnd:(NSString  *)action
                          logic:(BOOL  (^)  (NSTimeInterval  inAppDuration,
                                                  NSTimeInterval totalDuration,
                                                  NSMutableDictionary *data))block; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile  trackTimedActionEnd:@"cartToCheckout"
                    logic:^(NSTimeInterval inApp,
                    NSTimeInterval  total,
                    NSMutableDictionary  *data)  {
                        data[@"price"]  =  @"49.95";
                        return  YES;
                    }];
      ```

* **trackingTimedActionExists**

   시간 작업이 진행 중인지 여부를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (BOOL) trackingTimedActionExists:(NSString *)action;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      BOOL *actionExists = [ADBMobile trackingTimedActionExists];
      ```

* **trackingSendQueuedHits**

   SDK 4.1이 필요합니다.현재 큐에 있는 히트 수에 관계없이 라이브러리는 오프라인 큐의 모든 히트를 강제로 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) trackingSendQueuedHits;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile trackingSendQueuedHits]; 
      ```

* **trackingGetQueueSize**

   현재 오프라인 큐에 올라가 있는 히트 수를 검색합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
       + (NSUInteger) trackingGetQueueSize;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSUInteger *queueSize = [ADBMobile trackingGetQueueSize];
      ```

* **trackingClearQueue**

   오프라인 큐에서 모든 히트를 지웁니다.

   >[!CAUTION]
   >
   >큐를 수동으로 지울 때는 주의하십시오. 이 프로세스는 되돌릴 수 없습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) trackingClearQueue;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile trackingClearQueue]; 
      ```



* **trackPushMessageClickThrough**

   푸시 메시지 클릭스루를 추적합니다.

   >[!IMPORTANT]
   >
   >이 방법은 페이지 보기를 증가시키지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) trackPushMessageClickThrough:(NSDictionary *)userInfo;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      -  (void)application:(UIApplication  *)application  
      didReceiveRemoteNotification:(NSDictionary  *)userInfo  
      fetchCompletionHandler:(void  (^)
      (UIBackgroundFetchResult))completionHandler  {
          // only send the hit if the app is not active
          if (application.applicationState !=  UIApplicationStateActive)  {
              [ADBMobile  trackPushMessageClickThrough:userInfo];
      
          }
          completionHandler(UIBackgroundFetchResultNoData);
      }
      ```
