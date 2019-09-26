---
description: 다음은 iOS 라이브러리에서 제공하는 메서드 목록입니다.
seo-description: 다음은 iOS 라이브러리에서 제공하는 메서드 목록입니다.
seo-title: Configuration methods
solution: Marketing Cloud,Analytics
title: 구성 방법
topic: 개발자 및 구현
uuid: 623c7b07-fbb3-4d39-a5c4-e64faec4ca29
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Configuration methods {#configuration-methods}

다음은 iOS 라이브러리에서 제공하는 메서드 목록입니다.

SDK는 현재 Analytics, Target, Audience Manager, Adobe Experience Platform Identity Service 등 다양한 Adobe Experience Cloud 솔루션을 지원합니다.

* **setAppExtensionType**

   Adobe Mobile SDK 설정을 구성하여 현재 어떤 종류의 확장이 실행되고 있는지 확인합니다.

   다음 값 중 하나를 설정합니다.
   * `ADBMobileAppExtensionTypeRegular` - 익스텐션은 포함 앱과 번들로 제공됩니다.
   * `ADBMobileAppExtensionTypeStandAlone` - 확장명이 포함된 앱과 번들로 제공되지 않습니다.
   >[!TIP]
   >
   >This method should **only** be used if your app has an extension or is a stand-alone extension. For more information, see *ADBMobileAppExtensionType* below.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) setAppExtensionType:(ADBMobileAppExtensionType)type;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone]; 
      ```



* **버전**

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

   * `ADBMobilePrivacyStatusOptIn` - hits are sent immediately.
   * `ADBMobilePrivacyStatusOptOut` - hits are discarded.
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
   * `ADBMobilePrivacyStatusOptOut` - 히트가 무시됩니다.
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

   자동 생성된 방문자 식별자를 반환합니다. 이 식별자는 Adobe 서버에서 생성된 앱별 고유 방문자 ID입니다. 생성 당시 Adobe 서버에 도달할 수 없다면 이 ID가 Apple CFUUID를 사용하여 생성됩니다. 이 값은 처음 실행 시 생성된 다음 저장되며 그 이후부터 사용됩니다. 이 ID는 앱 업그레이드 시에도 보존되고, 표준 애플리케이션 백업 프로세스 중 저장 및 복원되며, 앱을 제거하면 삭제됩니다.

   >[!TIP]
   >
   >If your app upgrades from the Experience Cloud 3.x to the 4.x SDK, the previous custom or automatically generated visitor ID is retrieved and stored as the custom user identifier. 자세한 내용은 아래의 `userIdentifier` 행을 참조하십시오. 이렇게 하면 SDK 업그레이드 시에도 방문자 데이터가 보존됩니다. 4.x SDK에 새로 설치하는 경우 사용자 식별자는 `nil`이며 추적 식별자가 사용됩니다.

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
   >앱이 Experience Cloud 3.x에서 4.x SDK로 업그레이드하면 이전 사용자 지정 또는 자동으로 생성된 방문자 ID가 검색되어 사용자 지정 사용자 식별자로 저장됩니다. 이렇게 하면 SDK 업그레이드 시에도 방문자 데이터가 보존됩니다.

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
   >이 메서드는 앱이 백그라운드에 있을 때 알림을 등록하는 앱에 사용되며 앱이 백그라운드에 있을 때 실행하는 코드에서만 호출되어야 합니다.

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
   >The preferred location to invoke this method is in `application:didFinishLaunchingWithOptions:`.

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

   이 메서드는 앱의 시작 지점에서 호출해야 합니다. Where applicable, this may include one or both of the methods `application:didFinishLaunchingWithOptions:` and/or `applicationWillEnterForeground:` in your AppDelegate class.

   >[!IMPORTANT]
   >
   >Data that is passed to the SDK via `collectLifecycleDataWithAdditionalData:` will be persisted by the SDK in `NSUserDefaults`. SDK는 `NSDictionary` 또는 `NSString` 유형이 아닌 `NSNumber` 매개 변수에서 값을 제거합니다. To use  `collectLifecycleDataWithAdditionalData:`, you must have SDK **version 4.4** or later.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) collectLifecycleDataWithAdditionalData:(nullableNSDictionary*)data; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile collectLifecycleDataWithAdditionalData:@{@"entryType":@"appShortcutIcon"}]; 
      ```

* **overrideConfigPath**

   애플리케이션이 시작할 때 다른 ADBMobile JSON 구성 파일을 로드할 수 있게 합니다. 애플리케이션이 닫힐 때까지 다른 구성을 사용합니다.

   >[!IMPORTANT]
   >
   >To use `overrideConfigPath`, you must have SDK version 4.2 or later.

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
   >This method should only be used in the  `application:didRegisterForRemoteNotificationsWithDeviceToken:` method.

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

   SDK에 IDFA를 설정합니다. SDK에서 IDFA를 설정한 경우 IDFA가 라이프사이클에서 전송됩니다. 또한 IDFA는 신호(포스트백)에서 액세스할 수 있습니다.

   >[!TIP]
   >
   >Retrieve the IDFA from Apple APIs **only** if you are using an ad service. IDFA를 검색하고 올바르게 사용하지 않으면 앱이 거부될 수 있습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      +(void) setAdvertisingIdentifier:(NSString*)identifier;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSString *idfa = [[[ASIdentifierManager sharedManager]advertisingIdentifier] UUIDString]; 
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

