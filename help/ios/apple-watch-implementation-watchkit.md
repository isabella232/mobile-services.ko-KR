---
description: WatchOS 2부터는 WatchKit Extention이 Apple Watch 장치에서 실행됩니다. 이 환경에서 실행되는 애플리케이션의 경우 WatchConnectivity 프레임워크는 포함된 iOS 앱과 데이터를 공유해야 합니다.
seo-description: WatchOS 2부터는 WatchKit Extention이 Apple Watch 장치에서 실행됩니다. 이 환경에서 실행되는 애플리케이션의 경우 WatchConnectivity 프레임워크는 포함된 iOS 앱과 데이터를 공유해야 합니다.
seo-title: WatchOS 2를 사용한 Apple Watch 구현
solution: Marketing Cloud, Analytics
title: WatchOS 2를 사용한 Apple Watch 구현
topic: 개발자 및 구현
uuid: 9498467 E-DB 5 E -411 E-A 00 E-D 19841 F 485 DE
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Apple Watch implementation with WatchOS 2{#apple-watch-implementation-with-watchos}

Watchos 2 부터 감시 키트를 Apple Watch에서 실행할 수 있습니다. Applications that run in this environment require the `WatchConnectivity` framework to share data with their containing iOS app.

>[!TIP]
>
>`AdobeMobileLibrary` v 4.6.0 부터는 `WatchConnectivity` 지원됩니다.

## 시작하기 {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>최소한 다음 타겟을 갖는 프로젝트가 있는지 확인합니다.
>
>* 포함된 앱
>* WatchKit 앱
>* WatchKit Extension
>



WatchKit 앱 개발에 대한 자세한 내용은 [Watch App Architecture](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1)를 참조하십시오.

## 포함된 앱 구성 {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

Xcode 프로젝트에서 다음 단계를 완료하십시오.

1. `AdobeMobileLibrary` 폴더를 프로젝트로 드래그합니다.
1. `ADBMobileConfig.json` 해당 파일이 포함된 앱의 대상인지 확인합니다.
1. 포함된 앱 타겟의 **[!UICONTROL 빌드 단계]** 탭에서 **바이너리를 라이브러리와 연결]섹션을 확장하고 다음 라이브러리를 추가합니다.[!UICONTROL **

   * `AdobeMobileLibrary.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. `UIApplicationDelegate` 프로토콜을 구현하는 클래스에서 `WCSessionDelegate` 프로토콜을 추가합니다.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface AppDelegate : UIResponder <UIApplicationDelegate, WCSessionDelegate>
   ```

1. 앱 위임 클래스의 구현 파일에서 `AdobeMobileLibrary`를 가져옵니다.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. `ADBMobile` 라이브러리를 호출하기 전에 앱 위임 `application:didFinishLaunchingWithOptions:` 에서를 `WCSession`구성합니다.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. In your app delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

   `syncSettings:``ADBMobile` 라이브러리에서 라이브러리의 소비를 위한 사전이 사용되었는지를 나타내는 bool를 `ADBMobile` 반환합니다. `No`를 반환하면 Adobe SDK에서 메시지가 시작되지 않습니다.

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## Watchkit 확장 구성 {#section_5ADE31741E514330A381F2E3CFD4A814}

1. `ADBMobileConfig.json` 해당 파일이 Watchkit 확장 대상의 구성원인지 확인합니다.
1. WatchKit Extension 타겟의 **[!UICONTROL 빌드 단계]** 탭에서 **바이너리를 라이브러리와 연결]섹션을 확장하고 다음 라이브러리를 추가합니다.[!UICONTROL **

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. `WKExtensionDelegate` 프로토콜을 구현하는 클래스에서 프로토콜을 가져오고 `WatchConnectivity``WCSessionDelegate` 추가합니다.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. 확장 위임 클래스의 구현 파일에서 `AdobeMobileLibrary`를 가져옵니다.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. In `applicationDidFinishLaunching` of your extension delegate, configure your `WCSession` before making any calls to the `ADBMobile` library.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. 확장 위임의 `applicationDidFinishLaunching`에서 SDK용 시계 앱을 초기화합니다.

   ```objective-c
   [ADBMobile initializeWatch];
   ```

1. In your extension delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

   `syncSettings:``ADBMobile` 라이브러리에서 라이브러리의 소비를 위한 사전이 사용되었는지를 나타내는 bool를 `ADBMobile` 반환합니다. `NO`를 반환하면 Adobe SDK에서 메시지가 시작되지 않습니다.

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## 추가 정보 {#section_7BCDB5CF0D424DCA97883753D1881233}

다음 정보를 숙지하십시오.

* For WatchKit apps, `a.RunMode` will be set to `Extension`.
* WatchKit 앱은 시계에서 실행되므로 앱은 `a.AppID`에 앱 이름을 올바르게 보고합니다.
* WatchOS2 앱에서는 라이프사이클 호출이 트리거되지 않습니다.

