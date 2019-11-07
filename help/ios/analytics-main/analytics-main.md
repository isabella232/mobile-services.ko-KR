---
description: 다음은 Adobe Analytics에서 iOS SDK를 사용하는 데 유용한 정보입니다.
seo-description: 다음은 Adobe Analytics에서 iOS SDK를 사용하는 데 유용한 정보입니다.
seo-title: Analytics 개요
solution: Marketing Cloud,Analytics
title: Analytics 개요
topic: 개발자 및 구현
uuid: 8c7fb76a-be0b-4465-8151-ece7bad11b55
translation-type: ht
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Analytics 개요 {#analytics}

이 섹션의 정보는 Adobe Analytics에서 iOS SDK를 사용하는 데 유용합니다.

## 새로운 Adobe Experience Platform Mobile SDK 릴리스

Adobe Experience Platform Mobile SDK와 관련된 정보 및 문서 찾기 최신 문서를 보려면 [여기](https://aep-sdks.gitbook.io/docs/)를 클릭하십시오.

2018년 9월 일자로 SDK의 새로운 주요 버전을 릴리스하였습니다. 이러한 새로운 Adobe Experience Platform Mobile SDK는 [Experience Platform Launch](https://www.adobe.com/kr/experience-platform/launch.html)를 통해 구성할 수 있습니다.

* 시작하려면 Adobe Experience Platform Launch로 이동합니다.
* Experience Platform SDK 리포지토리의 항목을 보려면 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)로 이동하십시오.

## Analytics Tracking Identifier 생성

SDK에서 식별자는 사용자를 추적하는 데 사용되며 여기에서는 식별자의 계층 구조입니다.

1. VID(Custom Visitor Identifier)
2. AID(Analytics Tracking Identifier)
3. MID(Experience Cloud Identifier)

>[!TIP]
>
>Experience Cloud Identifier의 올바른 약어는 ECID입니다. SDK에서 계속 MID를 사용할 수 있지만 이는 이전 이름입니다.
Tracking Identifier라고도 하는 AID는 앱이 MID를 사용하도록 구성되지 않은 경우 SDK에서 생성합니다. 값은 `NSUserDefaults`에서 실행 및 앱 업그레이드 사이에서 지속됩니다. 사용자가 장치에서 앱을 삭제한 다음 앱을 다시 설치하거나 앱 개발자가 `NSUserDefaults`를 삭제하는 경우 SDK가 새 식별자를 생성합니다. 이 프로세스로 인해 분석 보고에 새로운 사용자가 생깁니다.

Identity 서비스 지원(MID)을 도입하는 앱에 있는 사용자의 경우 기존 AID 값이 분석 히트로 전송되며 분석 히트에는 AID 및 MID가 포함됩니다. Identity 서비스 지원을 사용하는 앱에 있는 새 사용자의 경우 분석 요청에 MID만 포함됩니다. 방문자 식별에 대한 자세한 내용은 [방문자 식별](https://docs.adobe.com/content/help/ko-KR/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html)을 참조하십시오.
