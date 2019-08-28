---
description: 이 정보를 통해 인앱 메시지 문제를 해결할 수 있습니다.
keywords: mobile
seo-description: 이 정보를 통해 인앱 메시지 문제를 해결할 수 있습니다.
seo-title: 인앱 메시징 문제 해결
solution: Marketing Cloud, Analytics
title: 인앱 메시징 문제 해결
topic: 지표
uuid: 8813 E 8 D 8-BB 1 E -46 AD -83 CD -98 AE 68 F 73 CE 6
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Troubleshooting in-app messaging{#troubleshooting-in-app-messaging}

이 정보를 통해 인앱 메시지 문제를 해결할 수 있습니다.

인앱 메시지에 대한 모든 요구 사항을 완료해도 메시지가 표시되지 않는 경우 다음 항목을 확인하십시오.

## 앱에 새 구성 및 새 SDK를 적용하고 있습니까?

* SDK 버전이 4.2 이상이고 SDK가 올바르게 구성되어 있는지 확인하십시오.

* Ensure that you have a [Messaging](/help/using/in-app-messaging/in-app-messaging.md) section in your configuration (the downloaded JSON file) or have a Messages remote endpoint, so that it can be retrieved from dynamic tag management.

## Android에서 내 전체 화면 메시지가 표시되지 않습니다. 올바른 SDK, 구성을 사용하고 있으며 내 트리거가 충족됩니다.

매니페스트 파일을 업데이트하여 전체 화면 활동을 정의했습니까?

## Android에서 내 로컬 알림 메시지가 작동하지 않습니다.

로컬 알림 브로드캐스트 수신기가 매니페스트에 선언되어 있는지 확인하십시오. For more information, see step #1 in [In-app messaging](/help/android/messaging-main/messaging/messaging.md).

## 메시지가 라이브입니까?

**인앱 메시지 관리 페이지의상태** 열에서 목록 보기를 확인하고, 메시지가 라이브 상태인지 확인합니다.

## [한 번 *보기*], [항상 *표시*], *[대상 페이지에서 오프라인* 설정 표시] 를 선택합니다.

이러한 설정이 올바른지 확인합니다. 대상 페이지에서 메시지 표시 빈도를 지정할 수 있는 **트리거** 탭의 옵션을 검토하십시오.

## 시작 이벤트를 트리거로 사용하는 경우...

시작은 새 세션에서만 실행됩니다. 세션이 시작되는 시간에 대한 정보는 `lifecycleTimeout`[로 변경되었습니다.](/help/ios/configuration/json-config/json-config.md)

## 내 메시지를 원격으로 업데이트했지만 아직 이전 메시지가 표시됩니다.

다음 작업 중 하나를 완료하십시오.

* Dynamic Tag Management가 새 정의로 종단점을 업데이트하는 데에 몇 분 정도 걸릴 수 있습니다.

   잠시 후에 다시 시도하십시오.

* 구성은 새로운 시작 시에만 업데이트됩니다.

   앱이 라이프사이클 세션 제한 시간 내에 다시 시작되었다면 새 구성이 다운로드되지 않았을 수 있습니다.

## 내 이미지가 템플릿에서 제공한 공간에 정확히 맞지는 않습니다.

인앱 메시지 전체 화면 템플릿에서는 원격 서버(이미지 URL)나 앱 번들(번들 이미지)에서 이미지를 보여주는 기능을 지원합니다. 이미지는 JPG, GIF 또는 PNG와 같은 표준 이미지 형식이어야 합니다.

장치 화면의 크기는 매우 다양하므로, 이미지가 템플릿에서 제공한 공간에 정확히 맞지는 않을 수 있습니다. 템플릿은 항상 이미지의 중앙을 보여주도록 초점이 맞춰지며, 이미지가 맞지 않을 경우 측면을 자르거나(세로) 측면에 페이드를 적용(가로)합니다.

다음은 각 방향에 대한 정확한 배치 및 크기 조정 규칙입니다.

* **세로**: 이미지 높이가 휴대폰의 경우 195px, 태블릿의 경우 529px로 조정되고, 이미지 너비가 장치 너비보다 작으면 중앙에 배치되고, 이미지 너비가 장치 너비보다 크면 잘립니다.

* **가로**: 이미지는 장치 높이의 100%으로 조정되고 오른쪽에서 페이드 아웃으로 페이드됩니다.

   전체 화면 템플릿에 문제가 있는 경우 사용자 지정 HTML 템플릿을 다운로드하여 사용할 수 있습니다. 사용자 지정 HTML 템플릿을 사용하면 이미지에 대해 더 유연하게 대처할 수 있으며, 템플릿을 원하는 대로 조정할 수 있습니다.

## 메시지에 UI에서 실행한 변경/업데이트가 반영되지 않습니다.

SDK는 라이프사이클이 시작될 때 새/업데이트된 메시지를 가져옵니다. 라이프사이클 시간 제한 값보다 오래 애플리케이션을 닫았거나/백그라운드로 실행된 다음 다시 열 때에만 메시지를 가져옵니다.

다음 단계를 완료합니다.

1. 구성 파일에서 메시지 URL를 말아 원격 메시지가 업데이트되었는지 확인합니다 (예: `curl "https://assets.adobedtm.com/b213090c5204bf94318f4ef0539a38b487d10368/scripts/satellite-542c62859662383b1a0008f4.json"`).
1. 애플리케이션을 닫습니다.
1. Wait for a time period that is longer than the `lifecycleTimeout` in the config file.
1. 앱을 열고 메시지가 표시되어야 하는 위치로 이동하여 메시지가 업데이트되었는지 확인합니다.