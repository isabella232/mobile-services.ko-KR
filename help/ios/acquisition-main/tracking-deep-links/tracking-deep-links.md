---
description: 다음은 Adobe Mobile iOS SDK를 사용하여 모바일 앱에서 딥링크와 지연된 딥링크를 추적하는 데 유용한 정보입니다.
seo-description: 다음은 Adobe Mobile iOS SDK를 사용하여 모바일 앱에서 딥링크와 지연된 딥링크를 추적하는 데 유용한 정보입니다.
seo-title: 딥링크 추적
solution: Experience Cloud,Analytics
title: 딥링크 추적
uuid: 08dc2820-7fd3-419f-ac2d-dcf12532578a
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '321'
ht-degree: 100%

---


# 딥링크 추적{#tracking-deep-links}

다음은 Adobe Mobile iOS SDK를 사용하여 모바일 앱에서 딥링크와 지연된 딥링크를 추적하는 데 유용한 정보입니다.

마케터가 애플리케이션에서 딥링크를 사용하는 방법에 대한 자세한 내용은 Mobile Services 설명서의 [획득](/help/ios/acquisition-main/acquisition.md)을 참조하십시오.

## 딥링크 추적

1. SDK를 프로젝트에 추가하고 라이프사이클 지표를 구현합니다.

   자세한 내용은 [핵심 구현 및 라이프사이클](/help/ios/getting-started/dev-qs.md)에서 *프로젝트에 SDK 및 구성 파일 추가*&#x200B;를 참조하십시오.
1. 앱 간 통신을 처리하거나 범용 링크를 지원할 애플리케이션을 등록합니다.

   자세한 내용은 [앱 간 통신](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html#//apple_ref/doc/uid/TP40007072-CH6-SW10) 또는 [범용 링크 지원](https://developer.apple.com/library/ios/documentation/General/Conceptual/AppSearch/UniversalLinks.html)을 참조하십시오.

1. openURL에서 딥링크를 추적합니다.

   딥링크 추적 샘플은 다음과 같습니다.

   ```objective-c
   - (BOOL)application:(UIApplication *)application handleOpenURL:(NSURL *)url { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
       return YES; 
   } 
   - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
   
       return YES; 
   }
   ```

Adobe Mobile SDK는 임의의 딥링크 또는 범용 링크에 `a.deeplink.id` 레이블과 null이 아닌 해당 사용자 생성 값이 포함된 키가 있을 경우 해당 링크에 추가된 데이터의 키 및 값 쌍을 구문 분석할 수 있습니다. 링크에 `a.deeplink.id` 키 및 값이 포함되어 있을 경우 해당 링크에 추가된 모든 키 및 값 쌍은 구문 분석하여 라이프사이클 히트에 추가된 다음 Adobe Analytics로 전송됩니다.

사용자 생성 값을 포함한 다음 예약 키 중 하나 이상을 딥링크 또는 범용 링크에 추가할 수도 있습니다.

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

이 키는 Adobe Analytics에 보고하기 위해 사전에 매핑된 변수입니다. 매핑 및 처리 규칙에 대한 자세한 내용은 [처리 규칙 및 컨텍스트 데이터](/help/ios/getting-started/proc-rules.md)를 참조하십시오.

### 지연된 딥링크 추적

1. Adobe 데이터 콜백을 등록합니다.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
   }];
   ```

1. `AdobeDataCallback` 내의 `ADBMobileDataEventDeepLink`를 처리합니다.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
       if (event == ADBMobileDataEventDeepLink) { 
           [self handleDeepLink:adobeData[ADBConfigKeyCallbackDeepLink]]; 
       } 
   }];
   ```

## 딥링크 공개 정보 {#section_44600E9AA68D4A53AA0C14BD86CC5284}

### 메서드에서 사용할 수 있습니다

```objective-c
/** 
 * @brief Tracks a Adobe Deep Link click-through 
 * @param url The URL resource received from UIApplication delegate method. 
 * @note Adobe Link data will be appended to the lifecycle call if it is a launch event, otherwise an extra call will be sent. 
 */ 
+ (void) trackAdobeDeepLink:(nullable NSURL *)url;
```

#### 상수

```objective-c
/* 
 * Used within ADBMobileDataCallback 
 * Key for deep link URL. 
 */ 
FOUNDATION_EXPORT NSString *const __nonnull ADBConfigKeyCallbackDeepLink;
```

