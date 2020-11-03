---
description: Adobe SDK는 Apple의 Search Ads App Attribution API를 활용하여 개발자와 마케팅 담당자가 Apple App Store의 검색 광고 캠페인에서 발생한 앱 다운로드를 추적하고 그 속성을 파악할 수 있도록 합니다.
seo-description: Adobe SDK는 Apple의 Search Ads App Attribution API를 활용하여 개발자와 마케팅 담당자가 Apple App Store의 검색 광고 캠페인에서 발생한 앱 다운로드를 추적하고 그 속성을 파악할 수 있도록 합니다.
seo-title: Apple 검색 광고
solution: Experience Cloud,Analytics
title: Apple 검색 광고
topic: Developer and implementation
uuid: 790080e8-067e-4bfd-a169-0027db4fdff3
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '280'
ht-degree: 100%

---


# Apple 검색 광고 {#apple-search-ads}

Adobe SDK는 Apple의 Search Ads App Attribution API를 활용하여 개발자와 마케팅 담당자가 Apple App Store의 검색 광고 캠페인에서 발생한 앱 다운로드를 추적하고 그 속성을 파악할 수 있도록 합니다. 검색 광고 캠페인에 대한 자세한 내용은 [Apple Search Ads](https://searchads.apple.com)/kr/를 참조하십시오.

## 이점 {#section_CEA30C652AC8470784B8054E299B80FA}

Apple 광고를 사용할 경우 다음과 같은 이점이 있습니다.

* 앱에 코드 줄 몇 개를 추가하여 검색 광고 앱 다운로드 캠페인의 효과를 쉽게 측정할 수 있습니다.
* 개발자는 다운로드 날짜/시간 및 전환을 유도한 입찰 키워드에 액세스할 수 있습니다.

## Apple 광고 구현 {#section_F1094676793540CFA1DBB540174EEB6A}

>[!TIP]
>
>Apple 광고를 구현하려면 iOS SDK 버전 4.13.2 이상이 있어야 합니다.

앱에서 검색 광고 속성을 사용하려면

1. Adobe SDK 버전 4.13.2 이상을 구현합니다.

   자세한 내용은 [핵심 구현 및 라이프사이클](/help/ios/getting-started/dev-qs.md)을 참조하십시오.

1. 앱의 Xcode 프로젝트 파일에 iAd 프레임워크를 추가합니다.

## 검색 광고 속성 보고 {#section_1AF4E0B4F8E94F36B38CA3D3E384D0A4}

1. Apple 검색 광고 속성 데이터는 획득 이름, 소스 및 용어 값으로 제공됩니다.

   속성이 `true`이면 라이프사이클 히트에 모든 `iad-*` 필드가 포함됩니다.

   또한 다음 값이 `"iad"` 사전에서 Adobe의 일반적인 획득 컨텍스트 데이터 필드에 매핑됩니다.

   * `"iad-campaign-id"` --> `"a.referrer.campaign.trackingcode"`
   * `"iad-campaign-name"` --> `"a.referrer.campaign.name"`
   * `"iad-adgroup-id"` --> `"a.referrer.campaign.content"`
   * `"iad-keyword"` --> `"a.referrer.campaign.term"`
   이렇게 매핑되면 해당 값을 Adobe의 표준 보고에 사용할 수 있습니다.
