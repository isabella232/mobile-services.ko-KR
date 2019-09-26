---
description: Experience Cloud 솔루션용 iOS SDK 4.x를 사용하면 기본 Apple iPhone 및 iPad 애플리케이션을 측정하고 앱에 타깃팅된 콘텐츠를 제공하고 Audience Manager를 통해 대상 데이터를 활용하고 수집할 수 있습니다.
seo-description: Experience Cloud 솔루션용 iOS SDK 4.x를 사용하면 기본 Apple iPhone 및 iPad 애플리케이션을 측정하고 앱에 타깃팅된 콘텐츠를 제공하고 Audience Manager를 통해 대상 데이터를 활용하고 수집할 수 있습니다.
seo-title: Experience Cloud 솔루션용 iOS SDK 4.x
solution: Marketing Cloud,Analytics
title: Experience Cloud 솔루션용 iOS SDK 4.x
topic: 개발자 및 구현
uuid: 8b374cee-1432-460b-aac2-70623dd80a04
translation-type: tm+mt
source-git-commit: 6d92beff55f359d667b399e66bae4cbffa4a1a0a

---


# Experience Cloud 솔루션용 iOS SDK 4.x{#ios-sdk-x-for-experience-cloud-solutions}

Experience Cloud 솔루션용 iOS SDK 4.x를 사용하면 기본 Apple iPhone 및 iPad 애플리케이션을 측정하고 앱에 타깃팅된 콘텐츠를 제공하고 Audience Manager를 통해 대상 데이터를 활용하고 수집할 수 있습니다.

>[!IMPORTANT]
>
>Mobile Services가 모바일 확보, 딥 링크, 위치 정보 및 모바일 메시징 기능에 액세스할 수 있도록 하려면 Adobe Analytics Mobile Marketing Add-on SKU가 필요합니다. 자세한 내용은 Adobe CSM에 문의하십시오.

>[!IMPORTANT]
>
>Experience Cloud 솔루션용 iOS SDK 4.x는 이제 iOS 13 [및 Xcode 11을 지원합니다](https://developer.apple.com/ios/). 완벽한 호환성을 위해서는 최신 버전의 4.x iOS SDK를 사용하십시오. 최신 버전에 대한 자세한 내용은 [릴리스 정보를](/help/ios/rel-notes.md)참조하십시오.

## 새로운 Adobe Experience Platform Mobile SDK 릴리스

Adobe Experience Platform Mobile SDK와 관련된 정보 및 문서 찾기 최신 문서를 보려면 [여기](https://aep-sdks.gitbook.io/docs/)를 클릭하십시오.

2018년 9월 일자로 SDK의 새로운 주요 버전을 릴리스하였습니다. 이러한 새로운 Adobe Experience Platform Mobile SDK는 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html)를 통해 구성할 수 있습니다.

* 시작하려면 Adobe Experience Platform Launch로 이동합니다.
* Experience Platform SDK 리포지토리의 항목을 보려면 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)로 이동하십시오.

기억해야 할 정보:

* iOS 5 이상이 지원됩니다.

   iOS 11 이상에서는 SDK 버전 4.13.8 이상이 **있어야** 합니다.

* 이 SDK의 4.2 버전 이상에서는 모든 히트를 HTTP POST를 사용하여 전송합니다.

   이렇게 하면 수집되거나 보고되는 데이터에는 영향을 주지 않지만 히트를 보려면 POST 데이터 검사를 지원하는 패킷 분석기를 사용해야 합니다.

* If you are upgrading from a previous version (2.x or 3.x), see the [4.x Migration Guide](/help/ios/getting-started/migration-v3.md).

## Adobe Mobile 사용자 설명서 {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services는 Adobe Experience Cloud에서 모바일 애플리케이션에 대한 모바일 마케팅 기능을 종합하여 제공하는 신규 UI를 제공합니다. Initially, the Mobile service provides seamless integration of app analytics and targeting capabilities from the Adobe Analytics, Adobe Audience Manager, and Adobe Target solutions, and Adobe Experience Platform Identity Service.

Mobile Services UI에 대한 자세한 정보를 확인하고 사용자 설명서를 읽어 보려면 [Adobe Mobile Services](/help/using/home.md)를 참조하십시오.

## Bloodhound 사용

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been
sunset. 2017년 5월 1일부터 추가적인 개선이나 추가 엔지니어링 또는 Adobe Expert Care 지원이 제공되지 않습니다.
