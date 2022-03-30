---
description: Adobe Mobile 및 Adobe Mobile SDK를 사용하면 푸시 메시지를 사용자에게 보낼 수 있습니다. 또한 SDK를 사용하면 푸시 메시지를 클릭하여 앱을 연 사용자를 쉽게 보고할 수도 있습니다.
solution: Experience Cloud Services,Analytics
title: 푸시 메시지
topic-fix: Developer and implementation
uuid: 2e2d8175-d7d0-4b6b-a14e-d419da1f9615
exl-id: 89796668-e0e7-45d2-8391-3c26a7ac8496
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 100%

---

# 푸시 메시지 {#push-messaging}

Adobe Mobile 및 Adobe Mobile SDK를 사용하면 푸시 메시지를 사용자에게 보낼 수 있습니다. 또한 SDK를 사용하면 푸시 메시지를 클릭하여 앱을 연 사용자를 쉽게 보고할 수도 있습니다.

>[!IMPORTANT]
>
>이 항목의 정보는 가능한 구현을 제안합니다. Apple의 iOS 설명서를 검토하여 앱에 가장 적합한 구현을 결정하는 것이 좋습니다. 사용 중인 프레임워크 및 앱이 대상으로 하는 iOS 버전에 따라 구현을 결정해야 합니다.

푸시 메시지를 사용하려면 **반드시** SDK 버전 4.6 이상이 있어야 합니다.

>[!IMPORTANT]
>
>앱 내의 Experience Cloud ID를 수동으로 설정하지 마십시오. 이로 인해 옵트인 상태 때문에 푸시 메시지를 받지 않는 고유한 사용자가 새로 생성됩니다. 예를 들어, 푸시 메시지를 수신하도록 옵트인한 사용자가 앱에 로그인한다고 가정합니다. 로그인 후 앱 내에서 ID를 수동으로 설정하는 경우 푸시 메시지 수신을 선택하지 않은 새로운 고유 사용자가 만들어집니다. 이 새로운 사용자는 푸시 메시지를 수신하지 않습니다.

## 전제 조건 {#section_06655ABE973743DC965897B229A2118D}

* 라이브러리를 프로젝트에 추가하고 라이프사이클 지표를 구현합니다.

   자세한 내용은 [라이프사이클 지표](/help/ios/metrics.md)를 참조하십시오.


* ID 서비스에 대해 SDK를 활성화해야 합니다.
자세한 내용은 [SDK ID 서비스 옵션 구성](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-visitor.md)을 참조하십시오.

>[!IMPORTANT]
>
>앱을 새 보고서 세트로 이동할 수 없습니다. 새 보고서 세트로 마이그레이션하는 경우 푸시 구성이 중단되고 메시지가 전송되지 않을 수 있습니다.

## 푸시 메시지 활성화 {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

1. `ADBMobileConfig.json` 파일에 푸시 메시지에 대한 필수 설정이 포함되어 있는지 확인합니다.

   `"marketingCloud"` 개체에는 푸시 메시지용으로 구성된 `"org"` 속성이 있어야 합니다.

   ```objective-c
   "marketingCloud": { 
       "org": "3CE342C92046435B0A490D4C@AdobeOrg" 
   }
   ```

1. `AppDelegate`에서 라이브러리를 가져옵니다.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 앱에서 권한을 요청해야 하는 설정을 결정하려면 [원격 알림 지원 구성](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/HandlingRemoteNotifications.html#//apple_ref/doc/uid/TP40008194-CH6-SW1)을 검토하십시오.

   다음은 경고, 배지, 사운드 및 원격 알림을 사용할 수 있는 권한을 요청하는 가능한 구현의 예입니다.

   ```objective-c
   // iOS 10 and newer 
   if (NSClassFromString(@"UNUserNotificationCenter")) { 
       UNUserNotificationCenter *center = [UNUserNotificationCenter currentNotificationCenter];   
       [center requestAuthorizationWithOptions:(UNAuthorizationOptionAlert + UNAuthorizationOptionSound + UNAuthorizationOptionBadge) 
           completionHandler:^(BOOL granted, NSError * _Nullable error) { 
           if (granted) { NSLog(@"authorization given"); } 
           else { NSLog(@"authorization rejected"); } 
           if (error) { NSLog(@"error during authorization: %@", error.localizedDescription); } 
       }]; 
       // have to ask for permission for remote notifications separately  
       [application registerForRemoteNotifications]; 
       // make this class the delegate for user notification handling  
       center.delegate = self; 
   } 
   // iOS 8.0 to iOS 9.3.5 
   else if ([application respondsToSelector:@selector(registerUserNotificationSettings:)]) { 
   #pragma GCC diagnostic push 
   #pragma GCC diagnostic ignored "-Wdeprecated-declarations" 
       UIUserNotificationTypetypes = UIUserNotificationTypeAlert | UIUserNotificationTypeBadge| UIUserNotificationTypeSound; 
       UIUserNotificationSettings *settings = [UIUserNotificationSettings settingsForTypes:types categories:nil]; 
       [application registerUserNotificationSettings:settings]; 
       // have to ask for permission for remote notifications separately  
       [application registerForRemoteNotifications]; 
   } 
   // older than iOS 8.0  
   else { 
       [application registerForRemoteNotificationTypes:UIRemoteNotificationTypeAlert | UIRemoteNotificationTypeBadge| UIRemoteNotificationTypeSound];  
   #pragma GCC diagnostic pop 
   }
   ```

1. 푸시 토큰은 ADBMobile 클래스의 `setPushIdentifier:` 메서드를 사용하여 SDK에 전달해야 합니다.

   ```objective-c
   - (void) application:(UIApplication *)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
       ... 
       [ADBMobile setPushIdentifier:deviceToken]; 
       ... 
   }
   ```

1. 환경에 대한 올바른 구현을 확인하려면 [UserNotifications](https://developer.apple.com/kr/documentation/usernotifications)로 이동합니다.

   이 단계는 사용자가 푸시 메시지의 클릭스루를 사용하여 앱을 열 경우 `userInfo` 사전을 SDK에 전달하여 푸시 보고를 사용하도록 설정하는 데 도움이 됩니다.

   다음 코드 샘플은 가능한 구현의 예제입니다.

   ```objective-c
   // device running < iOS 7 
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
       // only send the hit if the app is inactive 
       if (application.applicationState == UIApplicationStateInactive) {  
           [ADBMobile trackPushMessageClickThrough:userInfo]; 
       } 
   } 
   // device running between iOS 7 and iOS 9.3.5 
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult)) completionHandler { 
       // only send the hit if the app is inactive 
       if (application.applicationState == UIApplicationStateInactive) { 
           // only run this code if the UNUserNotificationCenterclass is not available or its delegate is not set (pre iOS 10) 
           if (!NSClassFromString(@"UNUserNotificationCenter") || ![UNUserNotificationCenter currentNotificationCenter].delegate) {  
               [ADBMobiletrackPushMessageClickThrough:userInfo]; 
           } 
       } 
       completionHandler(UIBackgroundFetchResultNoData); 
   } 
   // device running >= iOS 10 
   - (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
       if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
           [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
       } 
       completionHandler(); 
   }
   ```

1. 예상되는 푸시 대상을 정확하게 유지하려면 사용자가 `AppDelegate`의 `applicationDidBecomeActive:` 메서드에서 `[ADBMobile setPushIdentifier: nil]`을 호출하여 앱에 대한 푸시 메시지를 수동으로 사용하지 않도록 설정할 때 SDK에 알립니다.

   ```objective-c
   // device running < iOS 7 
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
       // only send the hit if the app is inactive 
       if (application.applicationState == UIApplicationStateInactive) {  
           [ADBMobile trackPushMessageClickThrough:userInfo]; 
       } 
   } 
   // device running between iOS 7 and iOS 9.3.5 
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult)) completionHandler { 
       // only send the hit if the app is inactive 
       if (application.applicationState == UIApplicationStateInactive) { 
           // only run this code if the UNUserNotificationCenterclass is not available or its delegate is not set (pre iOS 10) 
           if (!NSClassFromString(@"UNUserNotificationCenter") || ![UNUserNotificationCenter currentNotificationCenter].delegate) {  
               [ADBMobiletrackPushMessageClickThrough:userInfo]; 
           } 
       } 
       completionHandler(UIBackgroundFetchResultNoData); 
   } 
   // device running >= iOS 10 
   - (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
       if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
           [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
       } 
       completionHandler(); 
   }
   ```

## 예 {#section_20BEA0D64F7C4D45A5EBEF21066E62AD}

`AppDelegate.m` 구현의 예는 다음과 같습니다.

```objective-c
#import "AppDelegate.h" 
#import "ADBMobile.h" 
 
@implementation AppDelegate 
  
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
    if (NSClassFromString(@"UNUserNotificationCenter")) { 
        UNUserNotificationCenter *center = [UNUserNotificationCenter currentNotificationCenter]; 
        [center requestAuthorizationWithOptions:(UNAuthorizationOptionAlert + UNAuthorizationOptionSound + UNAuthorizationOptionBadge) 
                              completionHandler:^(BOOL granted, NSError * _Nullable error) {  
            if (granted) { NSLog(@"authorization given"); } 
            else { NSLog(@"authorization rejected"); } 
            if (error) { NSLog(@"error during authorization: %@", error.localizedDescription); } 
        }]; 
        center.delegate = self; 
        [application registerForRemoteNotifications]; 
    } 
    else if ([application respondsToSelector:@selector(registerUserNotificationSettings:)]) { 
#pragma GCC diagnostic push 
#pragma GCC diagnostic ignored "-Wdeprecated-declarations"  
        UIUserNotificationType types = UIUserNotificationTypeAlert | UIUserNotificationTypeBadge| UIUserNotificationTypeSound; 
        UIUserNotificationSettings *settings = [UIUserNotificationSettings settingsForTypes:types categories:nil]; 
        [application registerUserNotificationSettings:settings];  
        [application registerForRemoteNotifications]; 
    } 
    else { 
        [application registerForRemoteNotificationTypes:UIRemoteNotificationTypeAlert| UIRemoteNotificationTypeBadge| UIRemoteNotificationTypeSound]; 
#pragma GCC diagnostic pop 
    } 
 
    return YES; 
} 
 
- (void) applicationDidBecomeActive:(UIApplication *)application {  
    if (NSClassFromString(@"UNUserNotifcationCenter")) { 
        UNUserNotificationCenter *center = [UNUserNotificationCenter currentNotificationCenter]; 
        [center getNotificationSettingsWithCompletionHandler:^(UNNotificationSettings * _Nonnull settings) { 
            if (settings.authorizationStatus != UNAuthorizationStatusAuthorized) {  
                [ADBMobile setPushIdentifier:nil]; 
            } 
        }]; 
    } 
#pragma GCC diagnostic push 
#pragma GCC diagnostic ignored "-Wdeprecated-declarations"  
    else if ([application respondsToSelector:@selector(isRegisteredForRemoteNotifications)]) { 
        if (![application isRegisteredForRemoteNotifications]) {  
            [ADBMobile setPushIdentifier:nil]; 
        } 
    } 
    else if ([application enabledRemoteNotificationTypes] == UIRemoteNotificationTypeNone) { 
        [ADBMobile setPushIdentifier:nil]; 
    } 
#pragma GCC diagnostic pop 
} 
 
- (void) application:(UIApplication *)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
    [ADBMobile setPushIdentifier:deviceToken]; 
} 
 
- (void) application:(UIApplication *)application didFailToRegisterForRemoteNotificationsWithError:(NSError *)error { 
    [ADBMobile setPushIdentifier:nil]; 
} 
 
- (void) application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
    if (application.applicationState == UIApplicationStateInactive) {  
        [ADBMobile trackPushMessageClickThrough:userInfo];  
    } 
} 
 
- (void) application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler { 
    if (application.applicationState == UIApplicationStateInactive) {  
        if (!NSClassFromString(@"UNUserNotificationCenter") || ![UNUserNotificationCenter currentNotificationCenter].delegate) {  
            [ADBMobile trackPushMessageClickThrough:userInfo]; 
        } 
    } 
 
    completionHandler(UIBackgroundFetchResultNoData); 
} 
 
- (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
    if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
        [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
    } 
 
    completionHandler(); 
} 
 
@end
```
