---
description: 인앱 및 푸시 메시지를 만들고, 관리하고 이 메시지에 대해 보고합니다.
keywords: mobile
seo-description: 인앱 및 푸시 메시지를 만들고, 관리하고 이 메시지에 대해 보고합니다.
seo-title: 메시징
solution: Experience Cloud,Analytics
title: 메시징
topic: Metrics
uuid: e32d3e35-2d09-4ddf-8919-75dc895abcb3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 82%

---


# 메시징 {#messaging}

인앱 및 푸시 메시지를 만들고, 관리하고 이에 대해 보고할 수 있습니다.

## 새로운 Adobe Experience Cloud SDK 릴리스

Adobe Experience Platform Mobile SDK와 관련된 정보 및 설명서를 찾고 계십니까? [여기](https://aep-sdks.gitbook.io/docs/)를 클릭하여 최신 설명서를 확인하십시오.

2018년 9월 일자로 SDK의 새로운 주요 버전을 릴리스하였습니다. 이러한 새로운 Adobe Experience Platform Mobile SDK는 [Experience Platform Launch](https://www.adobe.com/kr/experience-platform/launch.html)를 통해 구성할 수 있습니다.

* To get started, go to [Launch](https://launch.adobe.com/).
* Experience Platform SDK 리포지토리의 항목을 보려면 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)로 이동하십시오.

>[!IMPORTANT]
>
> Adobe Experience Platform Mobile SDK와 Adobe Launch를 함께 사용 중인 경우, Adobe Analytics Mobile Services 확장 프로그램을 설치&#x200B;**해야** 획득 링크와 같은 Adobe Mobile Services 기능을 사용할 수 있습니다. 자세한 내용은 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)를 참조하십시오. Experience Platform SDK를 통해 푸시 메시지 및 인앱 메시지를 사용하는 방법에 관한 정보는 [푸시 메시지 설정](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) 및 [인앱 메시지 설정](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging)을 참조하십시오.

## 인앱 메시지 {#section_8984F4568BC24D32A87429FFCB5184A6}

인앱 메시지는 사용자의 동작 및 트레이트에 따라 실시간으로 사용자에게 전달됩니다. 메시지는 SDK에서 이미 추적한 Analytics 데이터에서 트리거됩니다.

지원되는 메시지 유형은 다음과 같습니다.

* 사용자 정의 및 테마
* 전체 화면
* 기본 경고
* 로컬 알림

인앱 메시지 작동 방식을 이해하는 데 도움이 되도록 다음 몇 가지 추가 정보를 제공합니다.

* 인앱 메시지를 사용하려면 SDK 버전 4.2 이상이 필요합니다.
* 모바일 앱 관리자 권한이 있는 사용자를 지정해야 합니다.

   이러한 권한을 통해 획득 링크 및 인앱 메시지에 액세스할 수 있습니다. 자세한 내용은 [역할 및 권한](/help/using/gs/c-mob-roles-and-permissions.md)을 참조하십시오.
* 메시지가 승인되면 응용 프로그램에 자동으로 게시됩니다.
* SDK는 트레이트, 트리거 및 일정과 같은 메시지 매개 변수가 충족되면 사용자에게 메시지를 제공합니다.
* 메시지는 온라인 URL을 사용하여 사용자 지정 HTML 또는 이미지를 포함할 수 있습니다.

   오프라인 상태에서 트리거되는 메시지에 대해서도 앱 번들의 백업 또는 대체 이미지를 지정할 수 있습니다.
* 활성 상태의 완료된 메시지는 총 뷰, 클릭스루 비율 등에 대한 보고서를 제공합니다.
* 사용자 지정 메시지에 템플릿을 사용할 수 있으며, 이 경우 고유한 인앱 메시지를 쉽게 작성할 수 있습니다.

## 푸시 메시지 {#section_90555A55BCE7427A90B1577E14BEF51B}

푸시 메시지는 알림을 받도록 선택한 사용자에게 전송됩니다. Analytics 세그먼트나 사용자 지정 세그먼트에서 이러한 푸시 메시지를 사용자에게 타깃팅할 수 있습니다. 푸시 메시지는 앱 외부에 표시되므로 수동적인 사용자를 다시 참여시키거나 시간 및 위치와 관련된 정보를 전달하는 데 사용할 수 있습니다.

푸시 메시지를 구성하기 전에 [푸시 메시지를 활성화하기 위한 전제 조건](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)을 참조하십시오. 이러한 작업을 수행했으면 앱의 설정에서 푸시 메시지를 구성해야 합니다. 자세한 내용은 [푸시 메시지 구성](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-push-messaging.md)을 참조하십시오.
