---
description: Experience Cloud Mobile SDK는 사용자가 로컬로 저장된 ID를 검색하고 데이터 수집 및 전송에 대한 선택 상태 플래그를 설정할 수 있는 컨트롤러에 일반 데이터 보호 규정(GDPR) 지원 API를 제공합니다.
title: 개인 정보 및 일반 데이터 보호 규정
uuid: 69bb82de-1993-440c-a1b0-8d37919b48b6
exl-id: 8549310d-31b8-49a3-9276-f8e9ab980a10
source-git-commit: bd55e3525488f24bc9845220f0df62706ec28f31
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 74%

---

# 개인 정보 및 일반 데이터 보호 규정 {#privacy-and-general-data-protection-regulation}

Experience Cloud Mobile SDK는 사용자가 로컬로 저장된 ID를 검색하고 데이터 수집 및 전송에 대한 선택 상태 플래그를 설정할 수 있는 컨트롤러에 일반 데이터 보호 규정(GDPR) 지원 API를 제공합니다.

>[!IMPORTANT]
>
>GDPR은 Mobile SDK 버전 4.16.0 이상에서&#x200B;**만** 지원됩니다.

## 새로운 Adobe Experience Platform Mobile SDK 릴리스

Adobe Experience Platform Mobile SDK와 관련된 정보 및 설명서를 찾고 계십니까? [여기](https://aep-sdks.gitbook.io/docs/)를 클릭하여 최신 설명서를 확인하십시오.

2018년 9월 일자로 SDK의 새로운 주요 버전을 릴리스하였습니다. 이러한 새로운 Adobe Experience Platform Mobile SDK는 [Experience Platform Launch](https://www.adobe.com/kr/experience-platform/launch.html)를 통해 구성할 수 있습니다.

* 시작하려면 Adobe Experience Platform Launch로 이동합니다.
* Experience Platform SDK 리포지토리의 항목을 보려면 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)로 이동하십시오.

## 개요

Adobe이 기업에 소프트웨어 및 서비스를 제공할 때 Adobe은 이러한 서비스를 제공하는 과정에서 처리하고 저장하는 개인 데이터에 대한 데이터 처리자 역할을 합니다. Adobe은 데이터 처리자로서 귀사의 허가 및 지침(예: Adobe와의 계약에 명시된 내용)에 따라 개인 데이터를 처리합니다.

데이터 제어자는 Mobile Services SDK Adobe을 사용하여 모바일 앱에서 GDPR 검색 및 삭제 요청을 지원할 수 있습니다.

모바일 앱의 Adobe Mobile SDK 부분에 대해 다음 설정 및 메서드를 사용할 수 있습니다.

* SDK에서 데이터를 검색하고 이 데이터를 서버에 전송하려면 `getAllIdentifiersAsync` 메서드를 사용합니다.

   자세한 내용은 [저장된 식별자 검색](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)을 참조하십시오.

* 선택 상태를 설정하고 GDPR 데이터 삭제 요청을 지원하려면 다음 설정을 사용합니다.

   * `privacyDefault`
   * `setPrivacyStatus`

   자세한 내용은 [사용자의 옵트 상태 설정](/help/ios/c-mob-privacy-gdpr-ios/privacy.md)을 참조하십시오.

## 추가 정보 {#section_7C7124C50D85469C8C8714533FB1A37D}

* GDPR에 대한 자세한 내용은 [GDPR 및 비즈니스](https://www.adobe.com/kr/privacy/general-data-protection-regulation.html).
