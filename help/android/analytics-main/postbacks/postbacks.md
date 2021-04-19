---
description: 포스트백을 이용하면 SDK에서 수집한 데이터를 타사 서버에 보낼 수 있습니다. 인앱 메시지를 표시하는 데 사용하는 것과 동일한 트리거와 트레이트를 이용하면 사용자 지정된 데이터를 타사 대상에 보내도록 SDK를 구성할 수 있습니다.
keywords: android;라이브러리;모바일;sdk
seo-description: 포스트백을 이용하면 SDK에서 수집한 데이터를 타사 서버에 보낼 수 있습니다. 인앱 메시지를 표시하는 데 사용하는 것과 동일한 트리거와 트레이트를 이용하면 사용자 지정된 데이터를 타사 대상에 보내도록 SDK를 구성할 수 있습니다.
seo-title: 포스트백
solution: Experience Cloud,Analytics
title: 포스트백 개요
topic-fix: Developer and implementation
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
exl-id: 318f6eab-ff71-4bfe-8eb7-51a35380b992
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 100%

---

# 포스트백 {#postbacks}

포스트백을 이용하면 SDK에서 수집한 데이터를 타사 서버에 보낼 수 있습니다. 인앱 메시지를 표시하는 데 사용하는 것과 동일한 트리거와 트레이트를 이용하면 사용자 지정된 데이터를 타사 대상에 보내도록 SDK를 구성할 수 있습니다.

>[!IMPORTANT]
>
>이 기능을 사용하려면 SDK 버전 4.6.0 이상이 필요합니다.

포스트백 메시지는 큐에 올라가 분석 데이터 수집을 제어하는 기존의 모든 온라인/오프라인 규칙을 따릅니다. 메시지가 일치할 때(표시된 메시지처럼) 포스트백 메시지는 나머지 메시지를 취소하지 않습니다. 따라서 동일한 분석 히트에서 여러 포스트백이 발생할 수 있습니다. 정의는 [ADBMobile JSON 구성](/help/android/configuration/json-config/json-config.md)의 *포스트백* 행을 참조하십시오.

## 템플릿 확장 {#section_6758AD05A24C4E9E965F5253294C164A}

템플릿 확장은 `templateurl` 및 `templatebody`속성에서 사용할 수 있습니다. 템플릿 항목은 `{key}`의 형태로 가져옵니다. 여기서 `key`는 컨텍스트 데이터 키 또는 기존 데이터 키입니다. 템플릿 확장에 사용할 수 있는 값은 메시지를 트리거하는 히트에 첨부된 모든 사용자 지정 데이터와 [라이프사이클 지표](/help/android/metrics.md)로 제한됩니다. 현재 사용 가능한 내역 또는 세그먼트 기반 데이터가 없습니다.

또한 SDK가 SDK에 알려진 내부 데이터로 자동으로 대체되는 특정 예약 템플릿이 있습니다.

이 목록에는 다음 사항이 포함됩니다.

| 토큰 이름 | 토큰 설명 |
|--- |--- |
| {%sdkver%} | SDK 버전을 반환합니다. |
| {%cachebust%} | 1에서 100000000 사이의 임의의 숫자로 확인됩니다. |
| {%adid%} | Android용 광고주 ID를 반환합니다. 참고: 이 템플릿은 `submitAdvertisingIdentifierTask`를 사용한 경우에만 작동합니다. |
| {%pushid%} | 푸시 식별자 토큰을 반환합니다. 참고: 이 템플릿은 `setPushIdentifier`를 사용한 경우에만 작동합니다. |
| {%timestampu%} | epoch 시간의 현재 타임스탬프를 반환합니다. |
| {%timestampz%} | 현재 타임스탬프를 JavaScript(ISO 8601) 형식으로 반환합니다. |
