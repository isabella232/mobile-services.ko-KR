---
description: Experience Cloud 솔루션용 iOS SDK 4.x를 사용하면 기본 Apple iPhone 및 iPad 애플리케이션을 측정하고 앱에 타깃팅된 콘텐츠를 제공하고 Audience Manager를 통해 대상 데이터를 활용하고 수집할 수 있습니다.
seo-description: Experience Cloud 솔루션용 iOS SDK 4.x를 사용하면 기본 Apple iPhone 및 iPad 애플리케이션을 측정하고 앱에 타깃팅된 콘텐츠를 제공하고 Audience Manager를 통해 대상 데이터를 활용하고 수집할 수 있습니다.
seo-title: Experience Cloud 솔루션용 iOS SDK 4.x
solution: Experience Cloud,Analytics
title: Experience Cloud 솔루션용 iOS SDK 4.x
topic: Developer and implementation
uuid: 8b374cee-1432-460b-aac2-70623dd80a04
translation-type: ht
source-git-commit: c7400359bc19150926a67b991ba219a7fa187442
workflow-type: ht
source-wordcount: '530'
ht-degree: 100%

---


# Experience Cloud 솔루션용 iOS SDK 4.x{#ios-sdk-x-for-experience-cloud-solutions}

Experience Cloud 솔루션용 iOS SDK 4.x를 사용하면 기본 Apple iPhone 및 iPad 애플리케이션을 측정하고 앱에 타깃팅된 콘텐츠를 제공하고 Audience Manager를 통해 대상 데이터를 활용하고 수집할 수 있습니다.

>[!IMPORTANT]
>
>버전 4.21.0부터 iOS SDK에는 필요한 최소 버전의 Xcode 12가 있습니다. Cocoapods를 사용하여 앱의 종속성을 관리하는 경우, Adobe SDK에 버전 1.10.0 이상이 필요합니다.

4.21.0 이상을 사용하는 경우 다음 변경 사항을 염두에 두고 설명서를 읽으십시오.

* 바이너리 라이브러리 파일이 언급될 때마다 대신 해당 XCFramework 대체 파일을 사용해야 합니다.
   * `AdobeMobileLibrary.a` > `AdobeMobile.xcframework`
   * `AdobeMobileLibrary_Extension.a` > `AdobeMobileExtension.xcframework`
   * `AdobeMobileLibrary_Watch.a` > `AdobeMobileWatch.xcframework`
   * `AdobeMobileLibrary_TV.a` > `AdobeMobileTV.xcframework`
* Adobe XCFrameworks를 프로젝트에 수동으로 추가하는 경우 XCFrameworks가 포함되지 않았는지 확인합니다.

>[!IMPORTANT]
>
>Adobe Analytics Mobile Marketing 추가 기능 SKU는 Mobile Services를 사용하여 모바일 획득, 딥링크, 지리적 위치 및 모바일 메시징 기능에 액세스하는 데 필요합니다. 자세한 내용은 Adobe CSM에게 문의하십시오.

>[!IMPORTANT]
>
>Experience Cloud 솔루션용 iOS SDK 4.x는 이제 [iOS 13 및 Xcode 11](https://developer.apple.com/ios/)을 지원합니다. 완벽한 호환성을 위해서는 4.x iOS SDK의 최신 버전을 사용하십시오. 최신 버전에 대한 자세한 내용은 [릴리스 노트](/help/ios/rel-notes.md)를 참조하십시오.

## 새로운 Adobe Experience Platform Mobile SDK 릴리스

Adobe Experience Platform Mobile SDK와 관련된 정보 및 설명서를 찾고 계십니까? [여기](https://aep-sdks.gitbook.io/docs/)를 클릭하여 최신 설명서를 확인하십시오.

2018년 9월 일자로 SDK의 새로운 주요 버전을 릴리스하였습니다. 이러한 새로운 Adobe Experience Platform Mobile SDK는 [Experience Platform Launch](https://www.adobe.com/kr/experience-platform/launch.html)를 통해 구성할 수 있습니다.

* 시작하려면 Adobe Experience Platform Launch로 이동합니다.
* Experience Platform SDK 리포지토리의 항목을 보려면 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)로 이동하십시오.

기억해야 할 정보:

* iOS 8 이상이 지원됩니다.

   iOS 11 이상 버전의 경우 SDK 버전 4.13.8 이상이 **반드시** 필요합니다.

* 이 SDK의 4.2 버전 이상에서는 모든 히트를 HTTP POST를 사용하여 전송합니다.

   이 작업은 수집 및 보고된 데이터에는 영향을 미치지 않지만 히트를 보려면 POST 데이터 검사를 지원하는 패킷 분석기를 사용해야 합니다.

* 이전 버전(2.x 또는 3.x)에서 업그레이드하는 경우 [4.x 마이그레이션 안내서](/help/ios/getting-started/migration-v3.md)를 참조하십시오.

## Adobe Mobile 사용자 설명서 {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services는 Adobe Experience Cloud에서 모바일 애플리케이션에 대한 모바일 마케팅 기능을 종합하여 제공하는 신규 UI를 제공합니다. 원래 Mobile 서비스는 Adobe Analytics, Adobe Audience Manager, Adobe Target 솔루션 및 Adobe Experience Platform ID 서비스에서 앱 분석 및 타깃팅 기능의 원활한 통합을 제공합니다.

Mobile Services UI에 대한 자세한 정보를 확인하고 사용자 설명서를 읽어 보려면 [Adobe Mobile Services](/help/using/home.md)를 참조하십시오.

## Bloodhound 사용

>[!IMPORTANT]
>
>**2017년 4월 30일** 현재 Adobe Bloodhound는 종료되었습니다. 2017년 5월 1일부터 추가적인 개선이나 추가 엔지니어링 또는 Adobe Expert Care 지원이 제공되지 않습니다.
