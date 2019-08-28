---
description: Adobe Mobile Services에서 고유한 추적 코드가 있는 획득 링크를 생성할 수 있습니다. 사용자가 생성된 링크를 클릭한 후 App Store에서 앱을 다운로드하고 실행하면 SDK는 자동으로 획득 데이터를 수집하여 Adobe Mobile Services에 보냅니다.
keywords: Android; 라이브러리; 모바일; SDK
seo-description: Adobe Mobile Services에서 고유한 추적 코드가 있는 획득 링크를 생성할 수 있습니다. 사용자가 생성된 링크를 클릭한 후 App Store에서 앱을 다운로드하고 실행하면 SDK는 자동으로 획득 데이터를 수집하여 Adobe Mobile Services에 보냅니다.
seo-title: 모바일 앱 획득
solution: Marketing Cloud, Analytics
title: 모바일 앱 획득
topic: 개발자 및 구현
uuid: 4 D 32 EAE 9-E 856-4 E 40-8 A 29-2 B 5 BCCD 106 E 0
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Mobile app acquisition {#mobile-app-acquisition}

Adobe Mobile Services에서 고유한 추적 코드가 있는 획득 링크를 생성할 수 있습니다. 사용자가 생성된 링크를 클릭한 후 App Store에서 앱을 다운로드하고 실행하면 SDK는 자동으로 획득 데이터를 수집하여 Adobe Mobile Services에 보냅니다.

## 새 Adobe Experience Cloud SDK 릴리스

Adobe Experience Platform Mobile SDK와 관련된 정보 및 문서 찾기 최신 문서를 보려면 [여기](https://aep-sdks.gitbook.io/docs/)를 클릭하십시오.

2018년 9월 일자로 SDK의 새로운 주요 버전을 릴리스하였습니다. 이러한 새로운 Adobe Experience Platform Mobile SDK는 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html)를 통해 구성할 수 있습니다.

* 시작하려면 [Launch](https://launch.adobe.com/)로 이동합니다.
* Experience Platform SDK 리포지토리의 항목을 보려면 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)로 이동하십시오.

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as Acquisition links. 자세한 내용은 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)를 참조하십시오. For more information about using Acquisition and Marketing Links with the Experience Cloud SDKs, see [Acquisition and Marketing Links](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#acquisition-and-marketing-links).

>[!IMPORTANT]
>
>획득을 사용하려면 **반드시** SDK 버전 4.1 이상이 있어야 합니다.

획득 링크는 Adobe Mobile Services에서 만들어야 합니다. 자세한 내용은 [획득을 참조하십시오.](/help/using/acquisition-main/acquisition-main.md)

**SDK 버전 4.13.1 이상**:

Adobe Mobile Services에서 생성된 획득 링크를 사용할 수 없는 경우 Google Play 획득을 사용하여 획득 데이터를 수집할 수 있고 SDK에서 보낼 수 있습니다.

표준 Google Play 획득 캠페인에서 획득 데이터를 수집하는 방법은 다음과 같습니다.

* 표준 Google Play 스토어 획득 메서드를 사용합니다.

   사용자 지정 획득 데이터는 표준 Google Play Acquisition 키 값 쌍과 함께 사용할 수 있습니다.

* 사용자가 Google Play 스토어를 통해 앱을 다운로드하고 실행하면 레퍼러의 데이터가 획득되어 Adobe Mobile Services로 전송됩니다.

   * The data is stored and available in the `AdobeDataCallback` instance that was registered earlier with the SDK.

      자세한 내용은 [구성 방법을](/help/android/configuration/methods.md)참조하십시오.

   * `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` OR `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` 이벤트 유형이 사용됩니다.

   * Google Play에서 획득한 데이터의 일부인 사용자 지정 키의 이름은 "`a.acquisition.custom.`"."으로 지정됩니다.

Adobe Mobile Services에서 만든 획득 링크를 사용하는 경우 다음 작업을 완료하여 획득 링크에 사용자 지정 데이터를 추가하십시오.

1. 획득 변수 접두사로 "`adb`"를 사용합니다.

   When the SDK receives the acquisition data from Adobe Mobile Services (on first launch), that data will be stored and also available in the `AdobeDataCallback` instance registered earlier with the SDK, as mentioned in [Configuration Methods](/help/android/configuration/methods.md).

1. `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` OR `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` 이벤트 유형이 사용됩니다.

1. 사용자 지정 데이터 키는 "`a.acquisition.custom.`

>[!TIP]
>
>여러 보고서 세트로 데이터를 전송하는 경우, 보고서 세트 ID의 목록에서 첫 번째 보고서 세트와 연관된 앱의 획득 데이터를 사용하십시오.

이 섹션의 업데이트를 통해 SDK는 획득 링크에서 획득 데이터를 전송할 수 있습니다.

## Tracking mobile acquisition {#section_CEA30C652AC8470784B8054E299B80FA}

1. 라이브러리를 프로젝트에 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 핵심 구현 *및* 라이프사이클에서 [Intellij 아이디어 또는 Eclipse 프로젝트에 SDK 및 구성 파일 추가를](/help/android/getting-started/dev-qs.md)참조하십시오.

1. 라이브러리를 가져옵니다:

   ```java
   import com.adobe.mobile.*;
   ```

1. 레퍼러에 대해 `BroadcastReceiver`를 구현합니다.

   ```java
   package com.your.package.name;  // replace with your app package name 
   
   import android.content.BroadcastReceiver; 
   import android.content.Context; 
   import android.content.Intent; 
   
   public class GPBroadcastReceiver extends BroadcastReceiver { 
     @Override 
     public void onReceive(Context c, Intent i) { 
      com.adobe.mobile.Analytics.processReferrer(c, i); 
     } 
   }
   ```

1. `AndroidManifest.xml`을 업데이트하여 이전 단계에서 생성된 `BroadcastReceiver`를 사용하도록 설정합니다.

   ```xml
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true"> 
    <intent-filter> 
     <action android:name="com.android.vending.INSTALL_REFERRER" /> 
    </intent-filter> 
   </receiver>
   ```

1. `ADBMobileConfig.json` 파일에 필수 획득 설정이 포함되어 있는지 확인합니다.

   ```xml
   "acquisition": { 
      "server": "c00.adobe.com", 
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f" 
   }, 
   "analytics": { 
     "referrerTimeout": 5, 
     ...
   ```

   >[!IMPORTANT]
   >
   >여러 보고서 세트로 데이터를 전송하는 경우, 보고서 세트 ID의 목록에서 첫 번째 보고서 세트와 연관된 앱의 획득 설정 (획득 서버 및 appid) 를 사용합니다.

   `acquisition` 설정은 Adobe Mobile Services에 의해 생성되므로 변경해서는 안 됩니다. For more information about how to download a customized `ADBMobileConfig.json` file with the `acquisition` settings pre-configured, see [Before You Start](/help/android/getting-started/requirements.md).

이 설정을 사용하면 첫 번째 앱 시작 이후 초기 라이프사이클 호출과 함께 획득 데이터가 자동으로 전송됩니다.

>[!CAUTION]
>
>`referrerTimeout` 앱 확보를 활성화하려면 0 보다 큰 값으로 설정해야 합니다.
