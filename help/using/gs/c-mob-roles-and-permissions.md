---
description: Adobe Analytics에서는 관리 도구 홈 페이지에서 역할을 관리할 수 있습니다.
seo-description: Adobe Analytics에서는 관리 도구 홈 페이지에서 역할을 관리할 수 있습니다.
seo-title: 역할 및 권한
title: 역할 및 권한
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
translation-type: tm+mt
source-git-commit: c7cac006340e01d0fd1f6afe3419e6fd17294a98
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 59%

---


# 역할 및 권한{#roles-and-permissions}

Adobe Analytics에서는 관리 도구 홈 페이지에서 역할을 관리할 수 있습니다.

## 개요 {#section_91B8192891E14E5285718C8118912500}

다음 역할은 Mobile Services UI에서 권한을 관리합니다.

### Analytics 관리

Analytics 관리자는 사용자 그룹을 관리하고 사용 권한을 할당하며, 이 중 하나가 모바일 앱 관리자입니다. Experience Cloud 관리자는 Adobe ID을 사용하여 Mobile Services UI에 로그인할 수 있는 Adobe ID을 Adobe Analytics 계정에 연결합니다. Experience Cloud 관리자에 대한 자세한 내용은 [관리 - 사용자 관리 및 FAQ](https://docs.adobe.com/content/help/ko-KR/core-services/interface/manage-users-and-products/admin-getting-started.html)를 참조하십시오.

>[!TIP]
>
>기존 Analytics 관리자는 사용자에게 Analytics 관리자 역할을 지정할 수 있습니다.

이 역할에 대한 자세한 내용은 다음 컨텐츠를 참조하십시오.

* [사용자 관리 개요](https://docs.adobe.com/content/help/ko-KR/analytics/admin/user-product-management/user-management/users.html)

* [사용자 및 그룹 권한 변경 사항](https://docs.adobe.com/content/help/ko-KR/analytics/admin/user-product-management/user-management/permissions-changes.html)

### 모바일 앱 관리

이 역할은 Mobile Services UI에 대한 관리자 역할입니다.

>[!IMPORTANT]
>
>Analytics 관리자는 푸시 메시지와 같은 일부 기능에 대해 사용자 관리에서 **[!UICONTROL 세그먼트 생성]** 확인란을 선택해야 합니다.

## 액세스 관리 {#section_E6939C2695AA4A0DBF432D50B2670920}

다음은 Mobile Services UI의 옵션에 액세스하는 방법에 대한 몇 가지 추가 정보입니다.

### 앱 및 보고서 세트

모든 모바일 서비스 앱은 보고서 세트에 연결되어 있습니다. 사용자에게 보고서 세트에 대한 액세스 권한이 없는 경우 해당 보고서 세트의 관련 앱에 액세스할 수 없습니다.

### Mobile Services 및 Analytics 기능

사용자의 회사에 푸시 메시지와 같은 UI의 기능에 액세스에 대한 Analytics 계약이 없는 경우, 회사 사용자는 권한 수준에 관계없이 해당 기능에 액세스할 수 없습니다.

## 역할 및 권한 {#section_20AA029D5B8C413C8659777E79B11620}

다음은 Mobile Services UI에서 관련 권한이 있는 역할입니다.

### Analytics 관리

* 모든 사용자 및 모바일 앱 관리자 권한
* 새 보고서 세트로 앱 만들기
* Mobile Services에서 앱 삭제

   >[!IMPORTANT]
   >
   >앱이 Mobile Services UI에서 삭제되었지만 보고서 세트가 여전히 Analytics에 있습니다.

* 앱 설정 관리

   * 라이프사이클 보고 활성화
   * 위치 보고 사용
   * 변수 및 지표 만들기/업데이트/삭제

### 모바일 앱 관리

* 모든 사용자 권한
* 기존 보고서 세트로 앱 만들기
* 앱 설정 관리

   * 앱의 모바일 SDK 옵션 구성
   * 앱의 UI 설정 구성
   * 연결된 앱스토어 앱 구성
   * 앱의 범용 링크 옵션 구성
   * 푸시 서비스 인증서 및 API 키 구성
   * 포스트백 만들기/업데이트/활성화/비활성화/복제/보관/삭제
   * 링크 대상 만들기/업데이트/보관/삭제

* 마케팅 링크 만들기/업데이트/보관
* 기존 획득 링크 만들기/가져오기/업데이트/삭제
* 장소 만들기/가져오기/업데이트/삭제(관심 영역) 구성
* 푸시 메시지 작성/업데이트/전송/예약/취소/복제/보관/삭제
* 인앱 메시지 만들기/업데이트/활성화/비활성화/복제/보관/삭제

그룹 및 사용자에 대한 자세한 내용은 다음을 참조하십시오.

* [사용자 그룹 설정](https://docs.adobe.com/content/help/ko-KR/analytics/admin/user-product-management/user-groups/groups.html)
* [사용자를 그룹에 추가](https://docs.adobe.com/content/help/ko-KR/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Mobile Services 사용자

이 역할에는 보기 전용 권한이 있으며 Mobile Services UI에서 피드백을 제공할 수 있습니다.

* Mobile Services UI에 대한 피드백 제공
* 앱 보기

   >[!IMPORTANT]
   >
   >사용자는 Adobe Analytics에서 액세스할 수 있는 보고서 세트만 볼 수 있습니다.

* 앱 설정 보기

   * 앱 SDK 구성 다운로드
   * 모든 UI 및 SDK 설정 보기
   * 변수 및 지표 구성 보기
   * 포스트백 보기
   * 링크 대상 보기

* 보고서 보기 및 실행
* 마케팅 링크 보기
* 기존 획득 링크 보기 및 내보내기
* 위치 보기 및 내보내기(관심 영역) 구성
* 푸시 메시지 보기
* 인앱 메시지 보기
