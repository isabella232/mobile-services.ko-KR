---
title: Adobe Mobile Services end-of-life FAQ
description: Adobe Mobile 서비스에 대한 수명 종료 안내와 관련하여 자주 묻는 질문에 대한 답변을 얻을 수 있습니다.
source-git-commit: a0f834247c328b40d0f47fdf515c239cf66b7566
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 2%

---

# Adobe Mobile 서비스 사용 종료 FAQ

Adobe Mobile Service&#39;s end-of-life date is **December 31, 2022**.

## 무슨 일이야?

Mobile Services reaches end-of-life on December 31, 2022. Mobile Services, which supports a mobile-centric UI, acquisition, deep linking, in-app messaging, push notification, and geo-location is no longer supported after this date.

## 포함된 내용 및 포함되지 않은 항목

이 수명 종료에는 Adobe Mobile 서비스만 포함되어 있으며, 이 서비스에는 [mobilemarketing.adobe.com](https://mobilemarketing.adobe.com). The Mobile version 4 SDKs that rely on this interface were sunset on August 31, 2021.

이 수명 종료에는 Adobe Experience Platform Mobile SDK의 일부인 모바일 앱용 Adobe Analytics이 포함되지 않습니다. 인앱 행동, 라이프사이클 분석, 메시징 상호 작용 추적 및 대상 프로필을 포함한 이러한 기능은 Adobe의 지원을 계속 받습니다.

## Why is the capability being retired?

Adobe이 모바일 마케팅 기능을 계속 확장함에 따라 Mobile Services에서 이전에 사용할 수 있었던 기능은 Adobe Experience Cloud 솔루션에서 출시되거나 Adobe Exchange 프리미어 파트너를 통해 제공됩니다. This transition provides you with more powerful and flexible mobile marketing capabilities.

## Mobile Services에서 만든 기존 처리 규칙은 어떻게 됩니까?

[처리 규칙](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) Mobile Services UI에서 생성되거나 생성된 는 Mobile 서비스 수명 종료 날짜 이전에 2022년 2월에 Adobe Analytics으로 자동으로 마이그레이션됩니다. Migrated processing rules behave similarly to other processing rules in Adobe Analytics, where you can freely view or edit them. No user action is required for this migration.

Mobile 서비스가 종료되면 일반적으로 다음을 포함하여 모든 처리 규칙 로직은 Adobe Analytics 내에서만 처리됩니다 [컨텍스트 데이터 변수](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/contextdata.html?lang=ko-KR).

## What transition options are available?

Adobe offers three transition paths depending on your organization&#39;s use case.

1. **인앱 메시지 및 푸시 알림**: Adobe은 메시징 워크플로우를 Adobe Journey Optimizer으로 전환할 수 있습니다. This product helps organizations optimize and personalize experiences across the entire customer journey, including mobile messaging.
1. **획득 및 심층 연결**: 고객 확보 및 심층 연결은 Adobe Exchange 프리미어 파트너 프로그램을 통해 제공됩니다. These partners include Adjust, AppsFlyer, and Branch, who offer extensive acquisition capabilities. Adobe의 파트너십 팀은 귀하의 요구 사항에 가장 적합한 솔루션을 찾을 수 있도록 적절한 소개를 제공할 수 있습니다.
1. **Places Service**: 위치 서비스는 지리적 위치 기능을 무료로 제공합니다. 자세한 내용은 [Places Service 설명서](https://experienceleague.adobe.com/docs/places/using/home.html).

## 질문이 있으면 어디로 가야 하나요?

See the [Adobe Mobile Services end-of-life Spark page](https://spark.adobe.com/page/C6D30y09zaRpD/) for more information. Contact your Adobe representative with any additional questions.
