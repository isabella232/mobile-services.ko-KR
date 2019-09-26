---
description: Experience Cloud 솔루션용 Android SDK 4.x를 사용하면 기본 Android 애플리케이션을 측정하고, 앱에 타겟 콘텐츠를 제공하고, 대상 관리를 통해 대상 데이터를 활용하고 수집할 수 있습니다.
keywords: android;library;mobile;sdk
seo-description: Experience Cloud 솔루션용 Android SDK 4.x를 사용하면 기본 Android 애플리케이션을 측정하고, 앱에 타겟 콘텐츠를 제공하고, 대상 관리를 통해 대상 데이터를 활용하고 수집할 수 있습니다.
seo-title: Android SDK 4.x for Experience Cloud 솔루션
solution: Marketing Cloud,Analytics
title: Android SDK 4.x for Experience Cloud 솔루션
topic: 개발자 및 구현
uuid: 56f1ff41-0365-41dd-bdde-245c823dff07
translation-type: tm+mt
source-git-commit: 3b744229b3fc288363be74c3c4adcd71ecc4fad4

---


# Android SDK 4.x for Experience Cloud solutions{#android-sdk-x-for-experience-cloud-solutions}

Experience Cloud 솔루션용 Android SDK 4.x를 사용하면 기본 Android 애플리케이션을 측정하고, 앱에 타겟 콘텐츠를 제공하고, 대상 관리를 통해 대상 데이터를 활용하고 수집할 수 있습니다.

>[!IMPORTANT]
>
>The Adobe Analytics Mobile Marketing Add-on SKU is required to enable Mobile Services access to mobile acquisition, deep linking, geolocation, and mobile messaging capabilities. 자세한 내용은 Adobe CSM에 문의하십시오.

## 새 Adobe Experience Cloud SDK 릴리스

Adobe Experience Platform Mobile SDK와 관련된 정보 및 문서 찾기 최신 문서를 보려면 [여기](https://aep-sdks.gitbook.io/docs/)를 클릭하십시오.

>[!IMPORTANT]
>
>2018년 9월 일자로 SDK의 새로운 주요 버전을 릴리스하였습니다. 이러한 새로운 Adobe Experience Platform Mobile SDK는 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html)를 통해 구성할 수 있습니다.

* 시작하려면 [Launch](https://launch.adobe.com/)로 이동합니다.
* Experience Platform SDK 리포지토리의 항목을 보려면 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)로 이동하십시오.

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. 자세한 내용은 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)를 참조하십시오.

>[!IMPORTANT]
>
>UI에서 기능을 구성할 수 있지만 생성된 구성 파일을 다운로드하고 이 파일을 SDK에 추가해야 이러한 기능이 작동합니다. SDK 다운로드 및 구성에 대한 자세한 내용은 핵심 구현 [및 라이프사이클을 참조하십시오](/help/android/getting-started/dev-qs.md).

SDK에서 지원하는 Android 버전은 다음과 같습니다.

* 4.6.0 이전 버전은 Android 2.2(API 8) ~ Android 5.1.1(API 22)을 지원합니다.
* 4.6.1 이상 버전은 Android 2.3(API 9) 이상을 지원합니다.

기억해야 할 정보:

* 4.2 버전 이상에서는 모든 히트를 HTTP POST를 사용하여 전송합니다.

   이렇게 하면 수집되거나 보고되는 데이터에는 영향을 주지 않지만 히트를 보려면 POST 데이터 검사를 지원하는 패킷 분석기를 사용해야 합니다.

* If you are upgrading from a previous version, see the [4.x Migration Guide](/help/android/getting-started/migration-v3.md).

## Adobe Mobile user documentation {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services는 Adobe Experience Cloud에서 모바일 애플리케이션에 대한 모바일 마케팅 기능을 종합하여 제공하는 UI를 제공합니다. UI에 대한 자세한 정보를 확인하고 사용자 설명서를 읽어 보려면 [Adobe Mobile Services](https://marketing.adobe.com/resources/help/en_US/mobile/)를 참조하십시오.

## 릴리스 노트 {#section_F8181DC052D44DD2A99AB40A41F6792C}

Experience Cloud 릴리스에 대한 최신 정보는 [Experience Cloud 릴리스 노트](https://marketing.adobe.com/resources/help/en_US/whatsnew/)를 참조하십시오.

## Bloodhound 사용

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been
sunset. 2017년 5월 1일부터 추가적인 개선이나 추가 엔지니어링 또는 Adobe Expert Care 지원이 제공되지 않습니다.
