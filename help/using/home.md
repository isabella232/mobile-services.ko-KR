---
description: Adobe Mobile Services용 기술 문서
seo-description: 본 안내서에서는 Adobe Experience Cloud에서 모바일 애플리케이션의 모바일 마케팅 기능을 함께 제공하는 Adobe Mobile Services에 대한 기술 설명서와 자가 진단에 대해 간략하게 설명하므로, 이를 통해 모바일 애플리케이션에 대한 사용자 참여를 파악하고 개선할 수 있습니다.
seo-title: Adobe Mobile Services
solution: Marketing Cloud, Analytics, Experience Cloud
title: Adobe Mobile Services
uuid: e86a77c9-4ff1-403f-a5a1-4afbdc4e6f68
translation-type: ht
source-git-commit: 9e3f199582351165d0a76ce5042b5eaeec2cc981

---


# Adobe Mobile Services {#adobe-mobile-services}

본 안내서에서는 Adobe Experience Cloud에서 모바일 애플리케이션의 모바일 마케팅 기능을 함께 제공하는 Adobe Mobile Services에 대한 기술 설명서와 자가 진단에 대해 간략하게 설명하므로, 이를 통해 모바일 애플리케이션에 대한 사용자 참여를 파악하고 개선할 수 있습니다.

>[!IMPORTANT]
>
>Adobe Analytics Mobile Marketing 추가 기능 SKU는 Mobile Services를 사용하여 모바일 획득, 딥링크, 지리적 위치 및 모바일 메시징 기능에 액세스하는 데 필요합니다. 자세한 내용은 Adobe CSM에게 문의하십시오.

## 4x SDK 지원 종료 안내

2020년 9월 30일 이후에는 고객이 버전 4 SDK를 계속 다운로드하여 사용할 수 있지만 고객 지원 센터 또는 포럼에 액세스할 수는 없습니다. Adobe Experience Platform Mobile SDK(이전 이름 v5)는 예정된 Adobe Experience Cloud 기능 및 기능을 독점적으로 지원합니다.

자세한 내용은 지원 종료 [FAQ](https://aep-sdks.gitbook.io/docs/version-4-sdk-end-of-support-faq) 를 참조하십시오.

가능하면 새로운 Experience Platform Mobile SDK로 마이그레이션하는 것이 좋습니다.

## 새로운 Adobe Experience Cloud SDK 릴리스

Adobe Experience Platform Mobile SDK와 관련된 정보 및 설명서를 찾고 계십니까? [여기](https://aep-sdks.gitbook.io/docs/)를 클릭하여 최신 설명서를 확인하십시오.

2018년 9월 일자로 SDK의 새로운 주요 버전을 릴리스하였습니다. 이러한 새로운 Adobe Experience Platform Mobile SDK는 [Experience Platform Launch](https://www.adobe.com/kr/experience-platform/launch.html)를 통해 구성할 수 있습니다.

* 시작하려면 Launch로 이동합니다.
* Experience Platform SDK 리포지토리의 항목을 보려면 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)로 이동하십시오.

>[!IMPORTANT]
>
> Adobe Experience Platform Mobile SDK와 Adobe Launch를 함께 사용 중인 경우, Adobe Mobile Services 기능(예: 인앱 메시지, 푸시 알림 또는 획득 링크)을 사용하려면 Adobe Analytics Mobile Services 확장 프로그램을 설치&#x200B;**해야** 합니다. 자세한 내용은 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)를 참조하십시오.

>[!IMPORTANT]
>
>UI에서 기능을 구성할 수 있지만, 이러한 기능은 생성된 구성 파일을 다운로드하고 이 파일을 SDK에 추가할 때까지 작동하지 않습니다. SDK 다운로드 및 구성에 대한 자세한 내용은 이 페이지의 *SDK 설명서* 섹션을 참조하십시오.

최신 릴리스 노트는 [Experience Cloud 릴리스 노트](https://docs.adobe.com/content/help/ko-KR/release-notes/experience-cloud/current.html)를 참조하십시오.

## 인기 있는 항목 {#section_AFFBC9EDDE5B4E4493A7C2896121A773}

다음은 이 안내서에서 많이 참조하는 항목입니다.

* [시작하기](/help/using/gs/gs.md)
* [로그인 중](/help/using/gs/gs-signin.md)
* [역할 및 권한](/help/using/gs/c-mob-roles-and-permissions.md)
* [모바일 지표](/help/using/gs/metrics/metrics.md)
* [메시징](/help/using/in-app-messaging/in-app-messaging.md)
* [획득](/help/using/acquisition-main/acquisition-main.md)
* [위치](/help/using/location/c-location-overview.md)
* [FAQ - Mobile Services](/help/using/faq-mobile.md)

## 개발자

다음은 개발자를 위한 몇 가지 링크입니다.

* [모바일 SDK 및 도구 다운로드](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/download-sdk.md)
* [Developer](https://docs.adobe.com/content/help/ko-KR/analytics/implementation/home.html)

## 커뮤니티 리소스

다음은 추가 리소스입니다.

* [Experience Cloud 포럼](https://forums.adobe.com/community/experience-cloud)
* [Adobe Marketing Cloud 커뮤니티](https://helpx.adobe.com/kr/marketing-cloud.html?promoid=KAWSE)
* [Idea Exchange](https://forums.adobe.com/community/experience-cloud/analytics-cloud/analytics)
* [Adobe 교육 및 자습서](https://helpx.adobe.com/kr/learning.html?promoid=KAUDK)
* [주요 솔루션 센터](https://www.adobe.com/kr/marketing-cloud.html)

## SDK 설명서 {#section_3A500233347C4305AB545E298A827CEA}

사용 안내서 외에 Adobe Mobile에서 앱을 구성하는 데 필요한 구성 파일의 미리 입력된 버전을 포함하는 사용자 정의 패키지가 있는 SDK(Software Development Kit)를 다운로드할 수 있습니다.

기본 라이브러리는 다음 플랫폼에 제공됩니다.

* [Experience Cloud 솔루션용 Android SDK 4.x](/help/android/overview.md)
* [Experience Cloud 솔루션용 iOS SDK 4.x](/help/ios/overview.md)
* [iOS 및 Android 4.x SDK용 Unity 플러그인](/help/unity/get-started.md)
* [Experience Cloud 솔루션 4.x SDK용 Xamarin 구성 요소](/help/xamarin/get-started.md)
* [Experience Cloud 솔루션용 Universal Windows Platform SDK 4.x](/help/universal-windows/overview.md)
* [Windows 8.1 유니버설 앱스토어](/help/windows-appstore/overview.md)

   * [Experience Cloud 솔루션 4.x SDK용 Windows Visual Studio 확장 프로그램](/help/windows-appstore/extensions/win-vse-4x.md)

* [Experience Cloud 솔루션용 BlackBerry 10 SDK 4.x](/help/blackberry/overview.md)

## Adobe Mobile Webinar 시작하기 {#section_420EA66F39FE44B9B531ADF5F5465543}

*Adobe Mobile 시작하기* 웨비나를 시청해 보십시오. ([재생](https://adobe.ly/PsxCFn))

[  ![](assets/webinar.png) ](https://adobe.ly/PsxCFn)
