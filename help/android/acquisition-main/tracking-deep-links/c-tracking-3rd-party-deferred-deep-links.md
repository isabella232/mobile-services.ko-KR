---
description: Android SDK를 사용하여 타사의 지연 딥링크 추적을 구현할 수 있습니다.
seo-description: Android SDK를 사용하여 타사의 지연 딥링크 추적을 구현할 수 있습니다.
seo-title: 타사의 지연 딥링크 추적
title: 타사의 지연 딥링크 추적
uuid: 4c798e47-7988-4a06-a191-6c4d05f6ee61
translation-type: ht
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# 타사의 지연된 딥링크 추적 {#tracking-third-party-deferred-deep-links}

Android SDK를 사용하여 타사의 지연 딥링크 추적을 구현할 수 있습니다.

## 클래식 Adobe Mobile SDK 딥링크 {#section_D114FA1EB9664EAA82E036A990694B26}

현재 Adobe Mobile SDK에서는 앱 개발자가 딥링크 활동에서 `collectLifecycleData` SDK API를 사용해야 하는 딥링크 기능을 지원합니다. SDK는 딥링크 URL 매개 변수의 딥링크 데이터를 추가합니다. Adobe Mobile SDK에서의 딥링크 작동 방식에 대한 자세한 내용은 [딥링크 추적](/help/android/acquisition-main/tracking-deep-links/tracking-deep-links.md).

## Facebook 딥링크 {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

광고 제작자는 Facebook에 게시하는 광고를 딥링크로 만들 수 있습니다. 사용자가 광고를 클릭하면 앱에서 관심 있는 정보로 바로 이동합니다. 딥링크는 핑거프린터 URL이 **아닙니다**. 그러나 광고 구성 중에 타사 딥링크 URL을 제공하는 옵션이 있습니다. Adobe Mobile SDK 및 서비스를 사용하는 앱 개발자는 이 필드에 Adobe Mobile Service 구성 핑거프린터 URL을 입력해야 합니다. 모든 것이 제대로 설정되면 Facebook SDK는 앱이 설치되거나 시작될 때 이 URL을 애플리케이션에 전달합니다.

## iOS에서 SDK {#section_834CD3109175432B8173ECB6EA7DE315}

Adobe Mobile SDK를 사용하는 Facebook 딥링크 지원을 추가하려면 먼저 앱 개발자가 다음 작업을 완료합니다.

* Android SDK 시작하기

   자세한 내용은 [Android SDK 시작하기](https://developers.facebook.com/docs/android/getting-started)를 참조하십시오.

* 딥링크 설정

   자세한 내용은 [딥링크 설정](https://developers.facebook.com/docs/app-ads/deep-linking#os)을 참조하십시오.

애플리케이션이 제대로 설정되면 `trackAdobeDeepLink()` API에서 Facebook 획득 캠페인에서 딥링크 정보를 수집할 수 있도록 설정하고 해당 정보를 Adobe Mobile Service로 보냅니다. 첫 시작 시 설치 히트가 Adobe Mobile Service로 전송되지 않았다면 이 정보가 라이프사이클 히트에 추가됩니다. 첫 실행 시 전송된 경우에는 Adobe 딥링크 히트로 전송됩니다.

>[!TIP]
>
>딥링크 URL에 `a.deeplink.id`라는 키가 있는지 확인하십시오. URL에 딥링크 ID 매개 변수가 없으면 URL 매개 변수가 컨텍스트 데이터에 추가되지 않습니다.

획득이 링크에 기여한 경우 Adobe Mobile SDK는 `trackAdobeDeepLink()` () 호출에 사용된 Facebook 딥링크의 획득 데이터를 저장합니다. 이 데이터는 나중에 Adobe Mobile SDK를 실행할 때 사용할 수 있습니다. 콜백이 등록된 경우에는 데이터를 클라이언트로 다시 보내는 데 Adobe 콜백도 사용됩니다.

## Android 애플리케이션에서 딥링크 활성화 {#section_64C15E269E89424B8E3D029F88094620}

1. 딥링크를 처리할 애플리케이션을 등록합니다.

   자세한 내용은 [다른 앱이 자신의 액티비티를 시작하도록 허용](https://developer.android.com/training/basics/intents/filters.html)을 참조하십시오.

1. Facebook SDK를 연결합니다.

   앱에 Facebook Gradle 종속성을 추가하려면 [Android SDK 시작하기](https://developers.facebook.com/docs/android/getting-started)의 단계를 완료하십시오.

1. Facebook SDK를 초기화하려면 *Android Studio 설치* 섹션의 지침을 따릅니다.
1. 기본 활동에서 `trackAdobeDeepLink()`를 호출합니다.

   ```java
   @Override 
   protected void onResume() { 
      super.onResume(); 
      AppEventsLogger.activateApp(this); 
      /* 
       * Adobe Tracking - Config 
       * 
       * call collectLifecycleData() to begin collecting lifecycle data 
       * must be in the onResume() of every activity in your app 
       */ 
      Config.collectLifecycleData(this);
   
      AppLinkData.fetchDeferredAppLinkData(this, 
            new AppLinkData.CompletionHandler() { 
               @Override 
               public void onDeferredAppLinkDataFetched(AppLinkData appLinkData) { 
                  // Process app link data 
                  if (appLinkData != null) { 
                     Config.trackAdobeDeepLink(appLinkData.getTargetUri()); 
                  } 
               } 
            } 
      ); 
   }
   ```

