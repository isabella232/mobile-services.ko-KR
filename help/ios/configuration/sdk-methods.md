---
description: 다음은 iOS 라이브러리에서 제공하는 메서드 목록입니다.
solution: Experience Cloud Services,Analytics
title: 구성 메서드
topic-fix: Developer and implementation
uuid: 623c7b07-fbb3-4d39-a5c4-e64faec4ca29
exl-id: b6841808-8fa8-4090-8cb3-ce647a3d5d08
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '1183'
ht-degree: 100%

---

# 구성 메서드 {#configuration-methods}

다음은 iOS 라이브러리에서 제공하는 메서드 목록입니다.

현재 SDK는 Analytics, Target, Audience Manager 및 Adobe Experience Platform ID 서비스 등 여러 Adobe Experience Cloud 솔루션을 지원합니다.

* **setAppExtensionType**

   현재 실행 중인 확장 종류를 결정하도록 Adobe Mobile SDK 설정을 구성합니다.

   다음 값 중 하나를 설정합니다.
   * `ADBMobileAppExtensionTypeRegular` - 확장 프로그램이 포함된 앱과 번들로 제공됩니다.
   * `ADBMobileAppExtensionTypeStandAlone` - 확장 프로그램이 포함된 앱과 번들로 제공되지 않습니다.

   >[!TIP]
   >
   >이 메서드는 앱에 확장 프로그램이 있거나 독립형 확장 프로그램인 경우에&#x200B;**만** 사용해야 합니다. 자세한 내용은 아래 *ADBMobileAppExtensionType*&#x200B;을 참조하십시오.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) setAppExtensionType:(ADBMobileAppExtensionType)type;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone]; 
      ```



* **version**

   Adobe Mobile 라이브러리의 현재 버전을 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      +(NSString*) version;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSString*libraryVersion = [ADBMobileversion];
      ```

* **privacyStatus**

   현재 사용자에 대한 개인 정보 상태의 열거 표현을 반환합니다:

   * `ADBMobilePrivacyStatusOptIn` - 히트가 즉시 전송됩니다.
   * `ADBMobilePrivacyStatusOptOut` - 히트가 삭제됩니다.
   * `ADBMobilePrivacyStatusUnknown` - 오프라인 추적이 활성화되면 개인 정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트 삭제)으로 변경될 때까지 히트가 저장됩니다. 오프라인 추적이 비활성화되면 개인 정보 상태가 옵트인으로 변경될 때까지 히트가 무시됩니다.
기본값은 `ADBMobileConfig.json` 파일에서 설정되어 있습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (ADBMobilePrivacyStatus) privacyStatus;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobilePrivacyStatus privacyStatus = [ADBMobileprivacyStatus];
      ```

* **setPrivacyStatus**

   현재 사용자의 개인정보 상태를 `status`로 설정합니다.

   다음 값 중 하나를 설정합니다.

   * `ADBMobilePrivacyStatusOptIn` - 히트가 즉시 전송됩니다.
   * `ADBMobilePrivacyStatusOptOut` - 히트가 삭제됩니다.
   * `ADBMobilePrivacyStatusUnknown` - 오프라인 추적이 활성화되면 개인 정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트 삭제)으로 변경될 때까지 히트가 저장됩니다. 오프라인 추적이 비활성화되면 개인 정보 상태가 옵트인으로 변경될 때까지 히트가 무시됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) setPrivacyStatus:(ADBMobilePrivacyStatus)status;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn];
      ```

* **lifetimeValue**

   현재 사용자의 수명 값을 반환합니다. 기본값은 `0`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (NSDecimalNumber *) lifetimeValue;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSDecimalNumber *lifeValue = [ADBMobile lifetimeValue];
      ```

* **trackingIdentifier**

   자동 생성된 방문자 식별자를 반환합니다. Adobe 서버에서 생성된 앱별 고유 방문자 ID입니다. 생성 시 Adobe 서버에 연결할 수 없으면 Apple의 CFUUID를 사용하여 ID가 생성됩니다. 이 값은 시작 초기 기간에 생성되며 이 시점부터 저장되고 사용됩니다. 이 ID는 앱 업그레이드 간에 유지되고 표준 애플리케이션 백업 프로세스 동안 저장 및 복원되며 설치 제거 시 제거됩니다.

   >[!TIP]
   >
   >앱을 Experience Cloud 3.x에서 4.x SDK로 업그레이드할 경우 이전 사용자 지정 또는 자동 생성된 방문자 ID가 검색되어 사용자 지정 사용자 식별자로 저장됩니다. 자세한 내용은 아래의 `userIdentifier` 행을 참조하십시오. 이렇게 하면 SDK 업그레이드 시에도 방문자 데이터가 보존됩니다. 4.x SDK에 새로 설치하는 경우 사용자 식별자는 `nil`이며 추적 식별자가 사용됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (NSString *) trackingIdentifier;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSString *tid = [ADBMobile trackingIdentifier];
      ```

* **userIdentifier**

   사용자 지정 ID가 설정된 경우 사용자 ID가 반환됩니다. 사용자 지정 ID가 설정되지 않은 경우에는 `nil`이 반환됩니다. 기본값은 `nil`입니다.

   >[!TIP]
   >
   >앱을 Experience Cloud 3.x에서 4.x SDK로 업그레이드할 경우 이전 사용자 지정 또는 자동 생성된 방문자 ID가 검색되어 사용자 지정 사용자 식별자로 저장됩니다. 이렇게 하면 SDK 업그레이드 시에도 방문자 데이터가 보존됩니다.

   4.x SDK에 새로 설치하는 경우 사용자 식별자는 설정될 때까지 `nil`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      +(NSString *) userIdentifier;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSString *uid = [ADBMobileuserIdentifier];
      ```

* **setUserIdentifier**

   사용자 식별자를 `identifier`로 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      +(void)setUserIdentifier:(NSString*)identifier;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile setUserIdentifier:@"billybob"]; 
      ```

* **debugLogging**

   현재 디버그 로깅 기본 설정을 반환합니다. 기본값은 `NO`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (BOOL) debugLogging;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      BOOL debugging = [ADBMobile debugLogging];
      ```

* **setDebugLogging**

   디버그 로깅 기본 설정을 `debug`으로 설정합니다. 

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) setDebugLogging:(BOOL)debug;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile setDebugLogging:YES];
      ```

* **keepLifecycleSessionAlive**

   구성 파일의 라이프사이클 세션 시간 제한 값과 상관없이 다음 번에 백그라운드에서 세션이 다시 시작할 때 새 세션이 시작하지 않아야 함을 SDK에 표시합니다.

   >[!TIP]
   >
   >이 메서드는 앱이 백그라운드에 있을 때 알림을 등록하는 앱에 사용하기 위한 것으로, 앱이 백그라운드에 있을 때 실행하는 코드에서만 호출되어야 합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) keepLifecycleSessionAlive;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile keepLifecycleSessionAlive]; 
      ```

* **collectLifecycleData**

   SDK의 솔루션 전체에서 사용하기 위해 라이프사이클 데이터를 수집해야 함을 SDK에 표시합니다. 자세한 내용은 [라이프사이클 지표](/help/ios/metrics.md)를 참조하십시오.

   >[!TIP]
   >
   >이 메서드를 호출하는 기본 위치는 `application:didFinishLaunchingWithOptions:`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) collectLifecycleData;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile collectLifecycleData];
      ```

* **collectLifecycleDataWithAdditionalData:**

   라이프사이클 지표를 수집할 때 추가 데이터를 전달할 수 있게 합니다.

   이 메서드는 앱의 시작 지점에서 호출해야 합니다. 적용 가능한 경우 AppDelegate 클래스에서 `application:didFinishLaunchingWithOptions:` 및/또는 `applicationWillEnterForeground:` 메서드 중 하나 또는 둘 다를 포함할 수 있습니다.

   >[!IMPORTANT]
   >
   >`collectLifecycleDataWithAdditionalData:`를 통해 SDK에 전달되는 데이터는 `NSUserDefaults`에서 SDK에 의해 유지됩니다. SDK는 `NSDictionary` 또는 `NSString` 유형이 아닌 `NSNumber` 매개 변수에서 값을 제거합니다. `collectLifecycleDataWithAdditionalData:`를 사용하려면 SDK **버전 4.4** 이상이 있어야 합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) collectLifecycleDataWithAdditionalData:(nullableNSDictionary*)data; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile collectLifecycleDataWithAdditionalData:@{@"entryType":@"appShortcutIcon"}]; 
      ```

* **pauseCollectingLifecycleData**

   이 API를 사용하여 라이프사이클 데이터 수집을 일시 중지합니다. 자세한 내용은 [라이프사이클 지표](/help/ios/metrics.md)를 참조하십시오.

   >[!IMPORTANT]
   >
   >`applicationDidEnterBackground` delegate 메서드에서 먼저 `pauseCollectingLifecycleData` 메서드를 호출해야 합니다.
   >
   >iOS 13으로 운영되는 iPhone7/7s 또는 이전 장치의 세션 길이 지표가 비정상인 문제를 완화하도록 API가 제공됩니다. 이는 iOS 13에서 발생한 알 수 없는 변경 사항 때문이었으며, iOS에서 앱을 백그라운드로 백업할 때 백그라운드 작업이 완료되는 데 시간이 충분하지 않은 문제였습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) pauseCollectingLifecycleData;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      - (void)applicationDidEnterBackground:(UIApplication *)application{
          // manually stop the lifecycle of SDK
          // important: do NOT call any track state or track action after this line
          [ADBMobile pauseCollectingLifecycleData];   
      
      
          // the following code is optional, may help to mitigate the issue a bit more. If you have other logic to run here that probably takes more than 10ms, then there is no need to add this line of code.
          [NSThread sleepForTimeInterval:0.01];
      
      
          // app's code to handle applicationDidEnterBackground
      }
      ```


* **overrideConfigPath**

   애플리케이션이 시작될 때 다른 ADBMobile JSON 구성 파일을 로드할 수 있습니다. 애플리케이션이 닫힐 때까지 다른 구성을 사용합니다.

   >[!IMPORTANT]
   >
   >`overrideConfigPath`를 사용하려면 SDK 버전 4.2 이상이 있어야 합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
       + (void) overrideConfigPath: (nullableNSString *) path;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
      [ADBMobile overrideConfigPath:filePath];
      ```

* **setPushIdentifier**

   푸시 알림용 장치 토큰을 설정합니다.

   >[!IMPORTANT]
   >
   >이 메서드는 `application:didRegisterForRemoteNotificationsWithDeviceToken:` 메서드에만 사용해야 합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) setPushIdentifier:(NSData *)deviceToken;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      - (void) application:(UIApplication *) application  didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
      [ADBMobile setPushIdentifier:deviceToken];  
      }
      ```

* **setAdvertisingIdentifier**

   SDK에 IDFA를 설정합니다. SDK에 IDFA가 설정된 경우 라이프사이클에서 IDFA가 전송됩니다. 또한 신호(포스트백)에서 액세스할 수 있습니다.

   >[!TIP]
   >
   >광고 서비스를 사용하는 경우&#x200B;**에만** Apple API에서 IDFA를 검색합니다. IDFA를 검색하고 올바르게 사용하지 않으면 앱이 거부될 수 있습니다.
   >
   >애플리케이션에 IDFA가 필요한 경우, [Apple의 설명서](https://developer.apple.com/documentation/adsupport)를 통해 광고 추적에 대한 사용자의 선호도를 문의하고 IDFA 값을 검색하십시오.
   >
   >iOS 14+의 경우 IDFA 값을 성공적으로 검색하려면 새 [앱 추적 투명도 프레임워크](https://developer.apple.com/documentation/apptrackingtransparency)를 구현해야 합니다.
   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      +(void) setAdvertisingIdentifier:(NSString*)identifier;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSString *idfa = // retrieve IDFA using AdSupport (before iOS 14.0) and/or AppTrackingTransparency (iOS 14.0+)
      [ADBMobile setAdvertisingIdentifier:idfa]; 
      ```

## ADBMobileAppExtensionType enum {#section_18DB491D0ABC4765BB5A467D8FEF4F1B}

```objective-c
/** 
 * @brief An enum type. 
 * The possible types of app extension you might use 
 * @see setAppExtensionType 
 */ 
typedef NS_ENUM(NSUInteger, ADBMobileAppExtensionType) { 
    ADBMobileAppExtensionTypeRegular = 0, /*!< Enum value ADBMobileAppExtensionTypeRegular. */ 
    ADBMobileAppExtensionTypeStandAlone = 1 /*!< Enum value ADBMobileAppExtensionTypeStandAlone. */ 
};
```
