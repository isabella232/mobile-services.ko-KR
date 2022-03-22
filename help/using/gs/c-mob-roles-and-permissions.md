---
description: Adobe Analytics에서는 관리 도구 홈 페이지에서 역할을 관리할 수 있습니다.
title: 역할 및 권한
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
exl-id: 70f0b427-60d5-4a79-a8d3-e03274edd917
source-git-commit: 7b26c852dd9dba67a8b5e3228c1fecadfb465dca
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 49%

---

# 역할 및 권한{#roles-and-permissions}

Adobe Analytics에서는 관리 도구 홈 페이지에서 역할을 관리할 수 있습니다.

## 개요 {#section_91B8192891E14E5285718C8118912500}

다음 역할은 Mobile Services UI에서 권한을 관리합니다.

### Analytics 관리

Analytics 관리자는 사용자 그룹을 관리하고 사용 권한을 할당하며, 이 중 하나가 모바일 앱 관리자입니다. The Experience Cloud Admin links your Adobe ID to your Adobe Analytics account, which allows you to log in to the Mobile Services UI by using your Adobe ID. [](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=ko-KR)

>[!TIP]
>
>기존 Analytics 관리자는 사용자에게 Analytics 관리자 역할을 지정할 수 있습니다.

### 모바일 앱 관리

이 역할은 Mobile Services UI에 대한 관리자 역할입니다.

>[!IMPORTANT]
>
>Analytics 관리자는 푸시 메시지와 같은 일부 기능에 대해 사용자 관리에서 **[!UICONTROL 세그먼트 생성]** 확인란을 선택해야 합니다.

## 액세스 관리 {#section_E6939C2695AA4A0DBF432D50B2670920}

다음은 Mobile Services UI의 옵션에 액세스하는 방법에 대한 몇 가지 추가 정보입니다.

### 앱 및 보고서 세트

All Mobile Service apps are tied to report suites. If users do not have access to a report suite, they will not have access to that report suite&#39;s associated app.

### Mobile Services 및 Analytics 기능

사용자의 회사에 푸시 메시지와 같은 UI의 기능에 액세스에 대한 Analytics 계약이 없는 경우, 회사 사용자는 권한 수준에 관계없이 해당 기능에 액세스할 수 없습니다.

## 역할 및 권한 {#section_20AA029D5B8C413C8659777E79B11620}

다음은 Mobile Services UI에서 관련 권한이 있는 역할입니다.

### Analytics 관리 permissions

* 모든 사용자 및 모바일 앱 관리자 권한
* Create App with new report suite
* Delete App from Mobile Services

   >[!IMPORTANT]
   >
   >앱이 Mobile Services UI에서 삭제되었지만 보고서 세트가 여전히 Analytics에 있습니다.

* 앱 설정 관리

   * Enable Lifecycle Reporting
   * Enable Location Reporting
   * Create/Update/Delete Variables and Metrics

### 모바일 앱 관리 permissions

* All User Permissions
* Create App with existing report suite
* 앱 설정 관리

   * Configure App&#39;s Mobile SDK options
   * Configure App&#39;s UI settings
   * Configure linked App Store apps
   * Configure App&#39;s Universal Link options
   * Configure Push Services certs and API keys
   * Create/Update/Activate/Deactivate/Duplicate/Archive/Delete Postbacks
   * Create/Update/Archive/Delete Link Destinations

* Create/Update/Archive Marketing Links
* Create/Import/Update/Delete Legacy Acquisition Links
* Create/Import/Update/Delete Places (Points of Interest) configuration
* Create/Update/Send/Schedule/Cancel/Duplicate/Archive/Delete Push Messages
* Create/Update/Activate/Deactivate/Duplicate/Archive/Delete In-App Messages

For more information about groups and users, see the following content in the Adobe Analytics documentation:

* [](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html?lang=ko-KR)
* [사용자를 그룹에 추가](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)

### Mobile Services 사용자

This role has view-only permissions and can provide feedback in the Mobile Services UI.

* Provide Feedback on Mobile Services UI
* View Apps

   >[!IMPORTANT]
   >
   >사용자는 Adobe Analytics에서 액세스할 수 있는 보고서 세트만 볼 수 있습니다.

* View App Settings

   * Download App SDK configuration
   * View all UI and SDK settings
   * View Variables and Metrics configuration
   * View Postbacks
   * View Link Destinations

* 보고서 보기 및 실행
* 마케팅 링크 보기
* View and Export Legacy Acquisition Links
* View and Export Places (Points of Interest) configuration
* View Push Messages
* View In-App Messages
