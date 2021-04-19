---
description: Experience Cloud 솔루션용 Android SDK 4.x를 사용하면 기본 Android 애플리케이션을 측정하고, 앱에 타겟 콘텐츠를 제공하고, 대상 관리를 통해 대상 데이터를 활용하고 수집할 수 있습니다.
keywords: android;라이브러리;모바일;sdk
seo-description: Experience Cloud 솔루션용 Android SDK 4.x를 사용하면 기본 Android 애플리케이션을 측정하고, 앱에 타겟 콘텐츠를 제공하고, 대상 관리를 통해 대상 데이터를 활용하고 수집할 수 있습니다.
seo-title: Experience Cloud 솔루션용 Android SDK 4.x
solution: Experience Cloud,Analytics
title: Experience Cloud 솔루션용 Android SDK 4.x
topic-fix: Developer and implementation
uuid: 56f1ff41-0365-41dd-bdde-245c823dff07
exl-id: c2454e94-a9af-42f3-ab45-14f68531faab
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 100%

---

# Experience Cloud 솔루션용 Android SDK 4.x{#android-sdk-x-for-experience-cloud-solutions}

Experience Cloud 솔루션용 Android SDK 4.x를 사용하면 기본 Android 애플리케이션을 측정하고, 앱에 타겟 콘텐츠를 제공하고, 대상 관리를 통해 대상 데이터를 활용하고 수집할 수 있습니다.

## 새로운 Adobe Experience Platform Mobile SDK 릴리스

Adobe Experience Platform Mobile SDK와 관련된 정보 및 설명서를 찾고 계십니까? [여기](https://aep-sdks.gitbook.io/docs/)를 클릭하여 최신 설명서를 확인하십시오.

2018년 9월 일자로 SDK의 새로운 주요 버전을 릴리스하였습니다. 이러한 새로운 Adobe Experience Platform Mobile SDK는 [Experience Platform Launch](https://www.adobe.com/kr/experience-platform/launch.html)를 통해 구성할 수 있습니다.

* 시작하려면 Adobe Experience Platform Launch로 이동합니다.
* Experience Platform SDK 리포지토리의 항목을 보려면 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)로 이동하십시오.

>[!IMPORTANT]
>
>Adobe Analytics Mobile Marketing 추가 기능 SKU는 Mobile Services를 사용하여 모바일 획득, 딥링크, 지리적 위치 및 모바일 메시징 기능에 액세스하는 데 필요합니다. 자세한 내용은 Adobe CSM에게 문의하십시오.

>[!IMPORTANT]
>
>UI에서 기능을 구성할 수 있지만, 이러한 기능은 생성된 구성 파일을 다운로드하고 이 파일을 SDK에 추가할 때까지 작동하지 않습니다. SDK 다운로드 및 구성에 대한 자세한 내용은 [핵심 구현 및 라이프사이클](/help/android/getting-started/dev-qs.md)을 참조하십시오.

SDK는 다음 버전의 Android를 지원합니다.

* 버전 4.6.0 또는 이전 버전은 Android 2.2(API 8) - Android 5.1.1(API 22)을 지원합니다.
* 버전 4.6.1 이상 버전은 Android 2.3(API 9) 이상을 지원합니다.

기억해야 할 정보:

* 4.2 버전 이상에서는 모든 히트를 HTTP POST를 사용하여 전송합니다.

   이 작업은 수집 및 보고된 데이터에는 영향을 미치지 않지만 히트를 보려면 POST 데이터 검사를 지원하는 패킷 분석기를 사용해야 합니다.

* 이전 버전에서 업그레이드하는 경우 [4.x 마이그레이션 안내서](/help/android/getting-started/migration-v3.md)를 참조하십시오.

## Adobe Mobile 사용자 설명서 {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services는 Adobe Experience Cloud에서 모바일 애플리케이션에 대한 모바일 마케팅 기능을 종합하여 제공하는 UI를 제공합니다.  UI에 대한 자세한 정보를 확인하고 사용자 설명서를 읽어 보려면 [Adobe Mobile Services](https://docs.adobe.com/content/help/ko-KR/mobile-services/using/home.html)를 참조하십시오.

## 릴리스 노트 {#section_F8181DC052D44DD2A99AB40A41F6792C}

Experience Cloud 릴리스에 대한 최신 정보는 [Experience Cloud 릴리스 노트](https://docs.adobe.com/content/help/ko-KR/release-notes/experience-cloud/current.html)를 참조하십시오.

## Bloodhound 사용

>[!IMPORTANT]
>
>**2017년 4월 30일** 현재 Adobe Bloodhound는 종료되었습니다. 2017년 5월 1일부터 추가적인 개선이나 추가 엔지니어링 또는 Adobe Expert Care 지원이 제공되지 않습니다.
