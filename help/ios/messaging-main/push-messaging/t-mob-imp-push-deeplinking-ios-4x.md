---
description: Adobe Mobile Services UI에서 딥링크 URL을 구성하면 이 URL은 adb_deeplink 키를 사용하여 푸시 페이로드에 저장됩니다.
seo-description: Adobe Mobile Services UI에서 딥링크 URL을 구성하면 이 URL은 adb_deeplink 키를 사용하여 푸시 페이로드에 저장됩니다.
seo-title: 딥링크로 푸시 메시지 구현
title: 딥링크로 푸시 메시지 구현
uuid: ee9590fc-8bd3-4111-9221-9011d9edbd84
translation-type: ht
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# 딥링크로 푸시 메시지 구현 {#implement-push-messaging-with-deep-linking}

Adobe Mobile Services UI에서 딥링크 URL을 구성하면 이 URL은 `adb_deeplink` 키를 사용하여 푸시 페이로드에 저장됩니다.

1. AppDelegate에서 딥링크 URL을 다시 가져와서 다음 위치에서 직접 처리할 수 있습니다.

   *  `application:didFinishLaunchingWithOptions`:

      푸시 클릭스루가 발생할 때 앱이 실행되지 않을 경우 `launchOptions`에서 푸시 페이로드를 가져올 수 있습니다. 딥링크 URL은 `adb_deeplink`의 페이로드 사전에 있습니다.

   * 원격 알림용 위임 메서드

      `didReceiveRemoteNotification:` 애플리케이션이나 `didReceiveRemoteNotification:fetchCompletionHandler:` 애플리케이션에서 `adb_deeplink` 키를 사용하여 `userInfo` 사전에 액세스하여 URL을 가져올 수 있습니다.

   * `UNUserNotificationCenter`에 대한 위임 메서드

      `userNotificationCenter:didReceiveNotificationResponse:withCompletionHandler:` 메서드에서 `userInfo` 사전의 푸시 페이로드를 `adb_deeplink` 키에 가져올 수 있습니다.

예:

```objective-c
- (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    NSDictionary *remoteNotification = launchOptions[UIApplicationLaunchOptionsRemoteNotificationKey]; 
    if (remoteNotification && [remoteNotification isKindOfClass:[NSDictionary class]]) { 
        NSString *deeplink = remoteNotification[@"adb_deeplink"]; 
        // handle deep link url 
    }
    return YES; 
} 
  
// app target < iOS 7 
- (void) application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
    // only send the hit if the app is not active 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
} 
  
// app target >= iOS 7 
- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler { 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
    ... 
} 
 
// if using UNUserNotificationCenterDelegate and device is running iOS 10 or newer 
- (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
    if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
        [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
        NSString *deeplink = response.notification.request.content.userInfo[@"adb_deeplink"]; 
        // handle deep link url  
    } 
    ... 
}
```

