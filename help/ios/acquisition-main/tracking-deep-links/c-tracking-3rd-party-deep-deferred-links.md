---
description: iOS SDK를 사용하여 타사의 지연 딥링크 추적을 구현할 수 있습니다.
seo-description: iOS SDK를 사용하여 타사의 지연 딥링크 추적을 구현할 수 있습니다.
seo-title: 타사 지연된 딥 링크 추적
title: 타사 지연된 딥 링크 추적
uuid: 5525b609-e926-44b9-b0f5-38e9dd7c9761
translation-type: tm+mt
source-git-commit: 4b5be6c51c716114e597a80d475f838e23abb1b1
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 90%

---


# 타사의 지연된 딥링크 추적 {#tracking-third-party-deferred-deep-links}

iOS SDK를 사용하여 타사의 지연 딥링크 추적을 구현할 수 있습니다.

## 클래식 Adobe Mobile SDK 딥링크 {#section_D114FA1EB9664EAA82E036A990694B26}

현재 Adobe Mobile SDK에서는 앱 개발자가 `trackAdobeDeepLink` API를 호출하고 딥링크 URL(Adobe Mobile Services에서 구성 중에 생성된 핑거프린터 URL)을 전달하는 딥링크 기능을 제공합니다. SDK는 핑거프린터를 핑하여 획득 데이터를 얻고 해당 데이터를 라이프사이클의 일부로 설치/시작 분석 호출 컨텍스트 데이터에 추가합니다. 또한 딥링크 URL 매개 변수의 딥링크 데이터도 추가합니다. 딥링크에 대한 자세한 내용은 [딥링크 추적](/help/ios/acquisition-main/tracking-deep-links/tracking-deep-links.md)을 참조하십시오.

## Facebook 딥링크 {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

광고 제작자는 Facebook에 게시하는 광고를 딥링크로 만들 수 있습니다. 사용자가 Facebook에서 광고를 클릭하면 앱에 관심이 있는 정보로 바로 이동합니다. 딥링크는 핑거프린터 URL이 **아닙니다**. 그러나 광고 구성 중에 타사 딥링크 URL을 제공하는 옵션이 있습니다. Experience Cloud Mobile SDK 및 서비스를 사용하는 앱 개발자는 이 필드에 지문 URL로 구성된 Mobile Services를 입력해야 합니다. 모든 것이 제대로 설정되면 Facebook SDK는 앱이 설치되거나 시작될 때 이 URL을 애플리케이션에 전달합니다.

## iOS에서 SDK {#section_834CD3109175432B8173ECB6EA7DE315}

1. Facebook SDK를 설정합니다.

   자세한 내용은 다음을 참조하십시오.

   * [iOS용 Facebook SDK 시작하기](https://developers.facebook.com/docs/ios/getting-started)
   * [설치 비활성화](https://developers.facebook.com/docs/app-ads/deep-linking#os)

1. SDK를 설정하려면 `trackAdobeDeepLink`를 호출하고 URL을 SDK에 전달합니다.

   ```objective-c
   - (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation 
   { 
     [ADBMobile trackAdobeDeepLink:url]; 
     return YES; 
   }
   ```

   >[!TIP]
   >
   >딥링크 URL에 `a.deeplink.id`라는 키가 있는지 확인합니다. URL에 `a.deeplink.id` 매개 변수가 없는 경우에는 URL 매개 변수가 컨텍스트 데이터에 추가되지 않습니다.

위에서 설명한 대로 애플리케이션을 설정하고 나면 현재 AMSDK 버전이 제대로 작동하며 딥링크 데이터가 설치/시작 분석 호출에 제대로 추가됩니다.

## 샘플 애플리케이션에서 기능 활성화 {#section_64C15E269E89424B8E3D029F88094620}

1. URL 스키마를 등록합니다.

   딥링크 URL과 동일한 URL 체계를 등록했는지 확인합니다.

   ```objective-c
   <key>CFBundleURLTypes</key> 
       <array> 
           <dict> 
               <key>CFBundleURLSchemes</key> 
               <array> 
                   <string>sampleapptest</string> 
               </array> 
           </dict> 
       </array>
   ```

1. Facebook SDK를 연결합니다.

   ![Facebook 자산](assets/link-fb-sdk.jpg)

1. 편집 `AppDelegate`.

   1. 헤더를 가져옵니다.

      ```objective-c
      /************************************************************************* 
      ADOBE SYSTEMS INCORPORATED 
      Copyright 2015 Adobe Systems Incorporated 
      All Rights Reserved. 
      NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the 
      terms of the Adobe license agreement accompanying it.  If you have received this file from a 
      source other than Adobe, then your use, modification, or distribution of it requires the prior 
      written permission of Adobe. 
      
      **************************************************************************/ 
      
      #import "AppDelegate.h" 
      #import "GalleryViewController.h" 
      #import "SimpleTrackingController.h" 
      #import "PostbackController.h" 
      #import "InAppMessageViewController.h" 
      #import "LifetimeValueController.h" 
      #import "LocationTargetingController.h" 
      #import "MediaViewController.h" 
      #import "TimedActionController.h"
      
      // Uncomment after including the facebook sdks. 
      @import FBSDKCoreKit; 
      @import Bolts;
      ```

   1. 지연된 딥링크에 대한 핸들을 추가합니다.

      ```objective-c
      - (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
          /* 
           * Adobe Tracking - Analytics 
           * 
           * turn on debug logging for the ADBMobile SDK 
           * enable the collection of lifecycle data 
           */ 
              if (launchOptions[UIApplicationLaunchOptionsURLKey] == nil) { 
                  if (NSClassFromString(@"FBSDKAppLinkUtility") != nil) 
                  { 
                      [NSClassFromString(@"FBSDKAppLinkUtility") performSelector:@selector(fetchDeferredAppLink:) withObject:^(NSURL *url, NSError *error) { 
                          if (error) { 
                              NSLog(@"Received error while fetching deferred app link %@", error); 
                          } 
                          if (url) { 
                              [[UIApplication sharedApplication] openURL:url]; 
                          } 
                      }]; 
                  } 
          } 
          ..... 
          ..... 
          return YES; 
      }
      ```

   1. `trackAdobeDeepLink` API를 호출하고 딥링크 URL를 SDK에 전달합니다.

      ```objective-c
      - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
          [self handleDeepLink:url]; 
      
          return YES; 
      }
      ```

