---
description: Adobe Mobile Services용 기술 문서
seo-description: 본 가이드는 Adobe Experience Cloud에서 모바일 애플리케이션을 위한 모바일 마케팅 기능을 제공하는 Adobe Mobile Services에 대한 기술 설명서와 자체 지원에 대해 간략하게 설명합니다. 이를 통해 모바일 애플리케이션을 사용한 사용자 참여도를 이해하고 향상시킬 수 있습니다.
seo-title: Adobe Mobile Services
solution: Marketing Cloud, Analytics, Experience Cloud
title: Adobe Mobile Services
uuid: e86a77c9-4ff1-403f-a5a1-4afbdc4e6f68
translation-type: tm+mt
source-git-commit: 20fdbba819f7c182a23a01cd06e1738ad83eba38

---


# Adobe Mobile Services {#adobe-mobile-services}

본 가이드는 Adobe Experience Cloud에서 모바일 애플리케이션을 위한 모바일 마케팅 기능을 제공하는 Adobe Mobile Services에 대한 기술 설명서와 자체 지원에 대해 간략하게 설명합니다. 이를 통해 모바일 애플리케이션을 사용한 사용자 참여도를 이해하고 향상시킬 수 있습니다.

>[!IMPORTANT]
>
>Mobile Services가 모바일 확보, 딥 링크, 위치 정보 및 모바일 메시징 기능에 액세스할 수 있도록 하려면 Adobe Analytics Mobile Marketing Add-on SKU가 필요합니다. 자세한 내용은 Adobe CSM에 문의하십시오.

## 새 Adobe Experience Cloud SDK 릴리스

Adobe Experience Platform Mobile SDK와 관련된 정보 및 문서 찾기 최신 문서를 보려면 [여기](https://aep-sdks.gitbook.io/docs/)를 클릭하십시오.

2018년 9월 일자로 SDK의 새로운 주요 버전을 릴리스하였습니다. 이러한 새로운 Adobe Experience Platform Mobile SDK는 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html)를 통해 구성할 수 있습니다.

* 시작하려면 Launch로 이동합니다.
* Experience Platform SDK 리포지토리의 항목을 보려면 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)로 이동하십시오.

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. 자세한 내용은 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)를 참조하십시오.

>[!IMPORTANT]
>
>UI에서 기능을 구성할 수 있지만 생성된 구성 파일을 다운로드하고 이 파일을 SDK에 추가해야 이러한 기능이 작동합니다. For information about downloading and configuring the SDKs, see the *SDK documentation* section on this page.

최신 릴리스 노트는 [Experience Cloud 릴리스 노트](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html)를 참조하십시오.

## 인기 있는 항목 {#section_AFFBC9EDDE5B4E4493A7C2896121A773}

다음은 이 안내서에서 인기 있는 몇 가지 주제입니다.

* [시작하기](/help/using/gs/gs.md)
* [로그인 중](/help/using/gs/gs-signin.md)
* [역할 및 권한](/help/using/gs/c-mob-roles-and-permissions.md)
* [모바일 지표](/help/using/gs/metrics/metrics.md)
* [메시징](/help/using/in-app-messaging/in-app-messaging.md)
* [획득](/help/using/acquisition-main/acquisition-main.md)
* [위치](/help/using/location/c-location-overview.md)
* [FAQ - Mobile Services](/help/using/faq-mobile.md)

## 개발자

Here are some links to help developers:

* [모바일 SDK 및 도구 다운로드](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/download-sdk.md)
* [Developer](https://marketing.adobe.com/resources/help/en_US/reference/developer.html)

## 커뮤니티 리소스

Here are some additional resources:

* [Experience Cloud 포럼](https://forums.adobe.com/community/experience-cloud)
* [Adobe Marketing Cloud 커뮤니티](https://helpx.adobe.com/marketing-cloud.html?promoid=KAWSE)
* [Idea Exchange](https://forums.adobe.com/community/experience-cloud/analytics-cloud/analytics)
* [Adobe 교육 및 자습서](https://helpx.adobe.com/learning.html?promoid=KAUDK)
* [주요 솔루션 센터](https://www.adobe.com/marketing-cloud.html)

## SDK 설명서 {#section_3A500233347C4305AB545E298A827CEA}

사용자 안내서 외에, SDK(Software Development Kit)를 다운로드할 수 있습니다. SDK는 Adobe Mobile에서 앱을 구성하는 데 필요한 구성 파일의 미리 채워진 버전이 들어 있는 사용자 지정 패키지를 포함합니다.

다음 플랫폼에 대한 기본 라이브러리가 제공됩니다.

* [Experience Cloud 솔루션용 Android SDK 4.x](https://docs.adobe.com/content/help/en/mobile-services/android/overview.html)

* [Experience Cloud 솔루션용 iOS SDK 4.x](https://docs.adobe.com/content/help/en/mobile-services/ios/overview.html)

* [iOS 및 Android 4.x SDK용 Unity 플러그인](https://docs.adobe.com/content/help/en/mobile-services/unity/get-started.html)

* [Experience Cloud 솔루션 4.x SDK용 Xamarin 구성 요소](https://docs.adobe.com/content/help/en/mobile-services/xamarin/get-started.html)

* [Experience Cloud 솔루션용 Universal Windows Platform SDK 4.x](https://docs.adobe.com/content/help/en/mobile-services/universal-windows/overview.html)

* [Windows 8.1 유니버설 앱 스토어](https://docs.adobe.com/content/help/en/mobile-services/windows-universal-appstore/overview.html)

   * [Experience Cloud 솔루션 4.x SDK용 Windows Visual Studio Extension](https://docs.adobe.com/content/help/en/mobile-services/windows-universal-appstore/win-vse-4x.html)

* [Experience Cloud 솔루션용 BlackBerry 10 SDK 4.x](https://docs.adobe.com/content/help/en/mobile-services/blackberry/overview.html)

## Adobe Mobile Webinar 시작하기 {#section_420EA66F39FE44B9B531ADF5F5465543}

*Adobe Mobile 시작하기* 웨비나를 시청해 보십시오. ( [재생](https://adobe.ly/PsxCFn))

[  ![](assets/webinar.png) ](https://adobe.ly/PsxCFn)
