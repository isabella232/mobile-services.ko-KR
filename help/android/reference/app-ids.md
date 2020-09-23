---
description: 다음 표에서는 Android SDK 및 Adobe Mobile 서비스에서 사용되는 다양한 앱 식별자를 설명합니다.
seo-description: 다음 표에서는 Android SDK 및 Adobe Mobile 서비스에서 사용되는 다양한 앱 식별자를 설명합니다.
seo-title: 앱 ID
solution: Experience Cloud,Analytics
title: 앱 ID
topic: Developer and implementation
uuid: 3ac99489-6269-439e-a814-24102ef220b1
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 72%

---


# 앱 ID{#app-ids}

다음 표에서는 Android SDK 및 Adobe Mobile 서비스에서 사용되는 다양한 앱 식별자를 설명합니다.

| ID | 설명 |
|--- |--- |
| 라이프사이클 지표와 함께 전송된 ID | 앱스토어에 전송된 번들 버전과 앱 이름이 조합된 ID입니다. 이 값은 Adobe Mobile Services의 버전 보고서에 사용되며 이 값을 사용하여 필터링함으로써 결과를 앱의 특정 출시 버전을 기준으로 세그먼트화할 수 있습니다. |
| 앱스토어 ID | 이 ID는 앱스토어에서 앱에 할당되며 획득 링크를 만들 때 Adobe Mobile Services에 제공됩니다. |
| ADBMobile JSON 구성의 AppID | 이 ID는 시스템의 모든 관련 메타데이터에 대해 Adobe Mobile Services가 앱 인스턴스에 할당한 고유 ID입니다. 이 ID는 획득 추적 또는 추적 링크에 대한 고유 URL을 만드는 데 사용됩니다. 이 ID는 UI에서 이 파일을 다운로드할 때 ADBMobile JSON 구성 파일에 자동으로 추가되며, 앱에 대한 획득 설정의 앱 설정 관리에 있습니다. |