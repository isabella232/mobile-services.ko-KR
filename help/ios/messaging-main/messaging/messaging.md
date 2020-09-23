---
description: 이 정보는 iOS 앱에서 인앱 메시지를 사용하는 데 도움이 됩니다.
seo-description: 이 정보는 iOS 앱에서 인앱 메시지를 사용하는 데 도움이 됩니다.
seo-title: 인앱 메시징
solution: Experience Cloud,Analytics
title: 인앱 메시징
topic: Developer and implementation
uuid: 21fa6a94-bb7f-4c78-843b-a50f1974db22
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 55%

---


# 인앱 메시징 {#in-app-messaging}

이 정보는 iOS 앱에서 인앱 메시지를 사용하는 데 도움이 됩니다.

To use in-app messaging, you **must** have SDK version 4.2 or later.

기억해야 할 정보:

* 메시지가 표시되는 시기를 정의하는 메시지 및 규칙이 Adobe Mobile Services에서 만들어집니다. For more information, see [Create an in-app message](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md).
* 인앱 메시지를 표시하려면 이 섹션에 설명된 업데이트를 SDK에 적용해야 합니다.

   >[!TIP]
   >
   >메시지가 정의되지 않은 경우에도 이 단계를 완료할 수 있습니다. 메시지를 정의하면 앱스토어를 업데이트하지 않아도 메시지가 앱에 동적으로 전달되어 표시됩니다.

## 인앱 메시지 사용 {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 [핵심 구현 및 라이프사이클](/help/ios/getting-started/requirements.md)에서 *프로젝트에 SDK 및 구성 파일 추가*&#x200B;를 참조하십시오.

1. 라이브러리를 가져옵니다:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. `ADBMobileConfig.json` 파일에 인앱 메시지에 대한 필수 설정이 포함되어 있는지 확인합니다.
1. 시작 시 인앱 메시지를 동적으로 업데이트하려면 `remotes` 개체가 존재하고 올바르게 구성되어 있어야 합니다.

   ```js
   “messages”: [ 
       { 
           “messageId”: “de45c43c-37bf-441f-8cbd-cc3ba3469ebe”, 
           “template”: “fullscreen”, 
           “showOffline”: false, 
           “showRule”: “always”, 
           “endDate”: 2524730400, 
           “startDate”: 0, 
           “audiences”: [], 
           “triggers”: [], 
           “payload”: { // contents change depending on template 
               “html”: “<html>html code goes here</html>” 
           }, 
       }, 
       … 
   ] 
   “remotes” : { 
       “analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”, 
       “messages”: “https://assets.adobedtm.com/…/yourfile.json” 
   }
   ```

   >[!TIP]
   >
   >`messages` 또는 `remotes`는 필수입니다.

   이러한 개체가 구성되어 있지 않으면 업데이트된 `ADBMobileConfig.json` 파일을 Adobe Mobile Services에서 다운로드합니다. 자세한 내용은 [핵심 구현 및 라이프사이클](/help/ios/getting-started/requirements.md)을 참조하십시오.

## 인앱 메시지 추적 {#section_B85CDF6929564AAEA79338B55E5CB1E8}

iOS Mobile Services SDK는 인앱 메시지에 대해 다음 지표를 추적합니다.

* 전체 화면 및 경고 스타일의 인앱 메시지:

   * **[!UICONTROL 노출 횟수]**: 사용자가 인앱 메시지를 트리거할 때입니다.
   * **[!UICONTROL 클릭스루]**: 사용자가 **[!UICONTROL 클릭스루]** 단추를 누를 때입니다.
   * **[!UICONTROL 취소]**: 사용자가 **[!UICONTROL 취소]** 단추를 푸시할 때입니다.

* 사용자 지정 전체 화면 in-app 메시지의 경우 메시지에서 HTML 컨텐츠에 다음 단추에 대한 SDK 추적을 알리는 올바른 코드를 포함해야 합니다.

   * ****&#x200B;클릭스루(리디렉션) 예 추적: `adbinapp://confirm/?url=https://www.yoursite.com`
   * **[!UICONTROL 취소]**(닫기) 예 추적: `adbinapp://cancel`

* 로컬(원격) 알림의 경우:

   * **[!UICONTROL 노출 회수]**: 사용자가 알림을 트리거할 때입니다.
   * **[!UICONTROL 시작]**: 사용자가 알림에서 앱을 열 때입니다.

   다음은 열린 추적을 포함하는 방법에 대한 예입니다.

   ```objective-c
   - (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
     // handle local notification click-throughs for iOS 10 and older 
     NSDictionary *localNotificationDictionary = launchOptions[UIApplicationLaunchOptionsLocalNotificationKey]; 
     if ([localNotificationDictionary isKindOfClass:[NSDictionary class]]) { 
          [ADBMobile trackLocalNotificationClickThrough:localNotificationDictionary]; 
     } 
   } 
   - (void) application:(UIApplication *)application didReceiveLocalNotification:(UILocalNotification *)notification { 
      [ADBMobile trackLocalNotificationClickThrough:notification.userInfo]; 
   }
   ```

## 로컬 대체 이미지 {#section_DEACC1CE549B4573B556A44A52409941}

Adobe Mobile Services에서 전체 화면 메시지를 만들 때 선택적으로 대체 이미지를 지정할 수 있습니다. 메시지가 웹에서 의도한 이미지를 검색할 수 없는 경우 SDK는 애플리케이션 번들의 이름과 동일한 이름으로 이미지를 로드합니다. 따라서 사용자가 오프라인 상태이거나 미리 결정된 이미지에 연결할 수 없는 경우에도 메시지를 원래 양식으로 표시할 수 있습니다.

대체 이미지 자산 이름은 Adobe Mobile Services에서 메시지를 구성할 때 지정됩니다.

>[!IMPORTANT]
>
>지정된 리소스가 사용 가능한지 확인해야 합니다.

