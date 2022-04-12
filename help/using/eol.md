---
title: Adobe Mobile 서비스 사용 종료 FAQ
description: Adobe Mobile Services에 대한 수명 종료 안내와 관련하여 자주 묻는 질문에 대한 답변을 얻습니다.
exl-id: c5f44341-7b87-4530-b86e-17e2911a7959
source-git-commit: a6dd74b8df771249e3c50de93f44639cfbfe7e13
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 2%

---

# Adobe Mobile Services 사용 종료 FAQ

Adobe 모바일 서비스의 수명 종료 날짜는 다음과 같습니다 **2022년 12월 31일**.

## 무슨 일이야?

Mobile Services는 2022년 12월 31일에 사용이 종료됩니다. 모바일 중심의 UI, 획득, 딥 링크, 인앱 메시지, 푸시 알림 및 지리적 위치를 지원하는 Mobile 서비스는 이 날짜 이후로 더 이상 지원되지 않습니다.

## 포함된 내용 및 포함되지 않은 항목

이 수명 종료에는 Adobe Mobile Services, 즉, [mobilemarketing.adobe.com](https://mobilemarketing.adobe.com). 이 인터페이스를 사용하는 모바일 버전 4 SDK는 2021년 8월 31일에 종료되었습니다.

이 수명 종료에는 Adobe Experience Platform Mobile SDK의 일부인 모바일 앱용 Adobe Analytics이 포함되지 않습니다. 인앱 행동, 라이프사이클 분석, 메시징 상호 작용 추적 및 대상 프로필을 포함한 이러한 기능은 Adobe의 지원을 계속 받습니다.

## 이 기능이 사용되지 않는 이유는 무엇입니까?

Adobe이 모바일 마케팅 기능을 계속 확장함에 따라 Mobile Services에서 이전에 사용할 수 있었던 기능은 Adobe Experience Cloud 솔루션에서 출시되거나 Adobe Exchange 프리미어 파트너를 통해 제공됩니다. 이 전환에서는 보다 강력하고 유연한 모바일 마케팅 기능을 제공합니다.

## Mobile Services에서 만든 기존 처리 규칙은 어떻게 됩니까?

[처리 규칙](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) mobile Services UI에서 생성 또는 생성된 는 Mobile Services 수명 종료 날짜 이전에 자동으로 Adobe Analytics으로 마이그레이션됩니다. 마이그레이션된 처리 규칙은 Adobe Analytics의 다른 처리 규칙과 유사하게 작동하며 자유롭게 보거나 편집할 수 있습니다. 이 마이그레이션에 대한 사용자 작업은 필요하지 않습니다.

Mobile 서비스가 종료되면 일반적으로 다음을 포함하여 모든 처리 규칙 로직은 Adobe Analytics 내에서만 처리됩니다 [컨텍스트 데이터 변수](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/contextdata.html?lang=ko-KR).

## 어떤 전환 옵션을 사용할 수 있습니까?

Adobe은 조직의 사용 사례에 따라 세 가지 전환 경로를 제공합니다.

1. **인앱 메시지 및 푸시 알림**: Adobe은 메시징 워크플로우를 Adobe Journey Optimizer으로 전환할 수 있습니다. 이 제품을 사용하면 모바일 메시지를 포함하여 전체 고객 여정에서 경험을 최적화하고 개인화할 수 있습니다.
1. **획득 및 심층 연결**: 고객 확보 및 심층 연결은 Adobe Exchange 프리미어 파트너 프로그램을 통해 제공됩니다. Adjust, AppsFlyer, Branch 등의 파트너에는 광범위한 획득 기능이 포함되어 있습니다. Adobe의 파트너십 팀은 귀하의 요구 사항에 가장 적합한 솔루션을 찾을 수 있도록 적절한 소개를 제공할 수 있습니다.
1. **Places Service**: 위치 서비스는 지리적 위치 기능을 무료로 제공합니다. 자세한 내용은 [Places Service 설명서](https://experienceleague.adobe.com/docs/places/using/home.html).

## 질문이 있으면 어디로 가야 하나요?

자세한 내용은 [Adobe Mobile Services 사용 종료 스파크 페이지](https://spark.adobe.com/page/C6D30y09zaRpD/) 추가 정보. 추가 질문 사항은 Adobe 담당자에게 문의하십시오.
