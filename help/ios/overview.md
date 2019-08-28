---
description: Experience Cloud 솔루션용 iOS SDK 4.x를 사용하면 기본 Apple iPhone 및 iPad 애플리케이션을 측정하고 앱에 타깃팅된 콘텐츠를 제공하고 Audience Manager를 통해 대상 데이터를 활용하고 수집할 수 있습니다.
seo-description: Experience Cloud 솔루션용 iOS SDK 4.x를 사용하면 기본 Apple iPhone 및 iPad 애플리케이션을 측정하고 앱에 타깃팅된 콘텐츠를 제공하고 Audience Manager를 통해 대상 데이터를 활용하고 수집할 수 있습니다.
seo-title: Experience Cloud 솔루션용 iOS SDK 4.x
solution: Marketing Cloud, Analytics
title: Experience Cloud 솔루션용 iOS SDK 4.x
topic: 개발자 및 구현
uuid: 8 B 374 CEE -1432-460 B-AAC 2-70623 DD 80 A 04
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Experience Cloud 솔루션용 iOS SDK 4.x{#ios-sdk-x-for-experience-cloud-solutions}

Experience Cloud 솔루션용 iOS SDK 4.x를 사용하면 기본 Apple iPhone 및 iPad 애플리케이션을 측정하고 앱에 타깃팅된 콘텐츠를 제공하고 Audience Manager를 통해 대상 데이터를 활용하고 수집할 수 있습니다.

>[!IMPORTANT]
>
>Mobile Services의 모바일 확보, 딥 링크, 지리적 위치 및 모바일 메시징 기능에 액세스하려면 Adobe Analytics Mobile Marketing Add-on SKU가 필요합니다. 자세한 내용은 Adobe CSM에 문의하십시오.

## 새 Adobe Experience Cloud SDK 릴리스

Adobe Experience Platform Mobile SDK와 관련된 정보 및 문서 찾기 최신 문서를 보려면 [여기](https://aep-sdks.gitbook.io/docs/)를 클릭하십시오.

2018년 9월 일자로 SDK의 새로운 주요 버전을 릴리스하였습니다. 이러한 새로운 Adobe Experience Platform Mobile SDK는 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html)를 통해 구성할 수 있습니다.

* 시작하려면 Launch로 이동합니다.
* Experience Platform SDK 리포지토리의 항목을 보려면 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)로 이동하십시오.

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. 자세한 내용은 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)를 참조하십시오.

기억해야 할 정보:

* iOS 5 이상이 지원됩니다.

   iOS 11 이상에서는 SDK 버전 4.13.8 이상이 **있어야** 합니다.

* 이 SDK의 4.2 버전 이상에서는 모든 히트를 HTTP POST를 사용하여 전송합니다.

   이 방법은 수집 또는 보고되는 데이터에 영향을 주지 않지만 히트 데이터를 검사하도록 지원하는 패킷 분석기를 사용해야 히트를 볼 수 있습니다.

* If you are upgrading from a previous version (2.x or 3.x), see the [4.x Migration Guide](/help/ios/getting-started/migration-v3.md).

## Adobe Mobile 사용자 설명서 {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services는 Adobe Experience Cloud에서 모바일 애플리케이션에 대한 모바일 마케팅 기능을 종합하여 제공하는 신규 UI를 제공합니다. 초기에 모바일 서비스는 Adobe Analytics, Adobe Audience Manager 및 Adobe Target 솔루션의 앱 분석 및 타깃팅 기능과 Adobe Experience Platform Identity Service를 매끄럽게 통합합니다.

Mobile Services UI에 대한 자세한 정보를 확인하고 사용자 설명서를 읽어 보려면 [Adobe Mobile Services](/help/using/home.md)를 참조하십시오.

## Bloodhound 사용

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been
sunset. 2017년 5월 1일부터 추가적인 개선이나 추가 엔지니어링 또는 Adobe Expert Care 지원이 제공되지 않습니다.
