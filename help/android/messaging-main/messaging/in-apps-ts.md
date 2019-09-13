---
description: 다음은 인앱 메시지 문제를 해결하는 데 유용한 정보입니다.
keywords: mobile
seo-description: 다음은 인앱 메시지 문제를 해결하는 데 유용한 정보입니다.
seo-title: 인앱 메시징 문제 해결
solution: Marketing Cloud, Analytics
title: 인앱 메시징 문제 해결
topic: 지표
uuid: 39 C 3 A 21 D -92 C 2-4004-B 00 F -99 B 6 F 91 D 3696
translation-type: tm+mt
source-git-commit: 12e01e112debffd877dd62f1fd2505724b2aae7d

---


# 인앱 메시징 문제 해결{#troubleshooting-in-app-messaging}

다음은 인앱 메시지 문제를 해결하는 데 유용한 정보입니다.

인앱 메시지에 대한 모든 요구 사항을 충족해도 메시지가 표시되지 않으면 다음 항목을 확인하십시오.

## 앱에 새 구성 및 새 SDK를 적용하고 있습니까?

Ensure that you have an [In-App Messaging](/help/android/messaging-main/messaging/messaging.md) section in your configuration (downloaded JSON file) or have a Messages remote endpoint, so that it can be retrieved from dynamic tag management.

## Android에서 내 전체 화면 메시지가 표시되지 않습니다. 올바른 SDK, 구성을 사용하고 있으며 내 트리거가 충족됩니다.

매니페스트 파일을 업데이트하여 전체 화면 활동을 정의했습니까?

## Android에서 내 로컬 알림 메시지가 작동하지 않습니다.

로컬 알림 브로드캐스트 수신기가 매니페스트에 선언되어 있는지 확인하십시오. For more information, see step 2 in *Enabling In-App Messaging* in [In-App Messaging](/help/android/messaging-main/messaging/messaging.md).

## 메시지가 라이브입니까?

메시지가 라이브인지 여부를 확인하려면 In-App 메시지 관리 페이지의 **상태** 열에서 메시지 목록을 확인하십시오.

## *한 번 표시*, *항상 표시*, *오프라인으로 표시* 설정을 대상 페이지에서 확인합니다.

이 설정들이 원하는 방법으로 설정되어 있는지 확인하십시오. **[!UICONTROL 대상]** 탭에서 메시지 표시 빈도를 지정할 수 있는 **트리거[!UICONTROL 옵션을 검토하십시오.]**

## 론치 이벤트를 트리거로 사용하는 경우...

시작은 새 세션에서만 실행됩니다. 세션이 시작되는 경우에 대한 자세한 내용은 `lifecycleTimeout`JSON 구성[에서 ](/help/android/configuration/json-config/json-config.md) 행을 참조하십시오.

## 내 메시지를 원격으로 업데이트했지만 아직 이전 메시지가 표시됩니다.

다음 정보를 숙지하십시오.

* 다이내믹 태그 관리가 새 정의로 종단점을 업데이트하는 데에 수 분이 걸릴 수 있습니다. 잠시 기다렸다가 다시 시도하십시오.
* 구성은 새로운 시작 시에만 업데이트됩니다. 앱이 라이프사이클 세션 제한 시간 내에 다시 시작되었다면 새 구성이 다운로드되지 않았을 수 있습니다.

자세한 내용은 [라이프사이클 지표](/help/android/metrics.md)를 참조하십시오.

## 내 이미지가 템플릿에서 제공한 공간에 정확히 맞지는 않습니다.

인앱 메시지 전체 화면 템플릿에서는 원격 서버(이미지 URL)나 앱 번들(번들 이미지)의 이미지를 표시하는 기능을 지원합니다. 이미지는 JPG, GIF 또는 PNG와 같은 표준 이미지 형식이어야 합니다. 장치 화면의 크기는 매우 다양하므로, 이미지는 템플릿에서 제공한 공간에 정확히 맞지는 않을 수 있습니다. 템플릿은 이미지의 중심을 표시하는 데 중점을 둡니다. 이미지가 맞지 않으면 측면을 자르거나(세로) 측면을 페이드(가로)합니다.

다음은 각 방향에 대한 정확한 배치 및 크기 조정 규칙입니다.

* **세로**
   * 휴대폰의 경우 높이 195px.
   * 태블릿의 경우 높이 529px.
   * 이미지 너비가 장치 너비보다 작은 경우 중앙에 배치됩니다.
   * 이미지 너비가 장치 너비보다 크면 잘립니다.

* **가로**
   * 이미지가 장치 높이의 100%로 조정됩니다.
   * 너비는 장치의 75%이며, 오른쪽에서 페이드 아웃됩니다.
   전체 화면 템플릿에 문제가 있는 경우 사용자 지정 HTML 템플릿을 다운로드하여 사용할 수 있습니다. 이 템플릿을 사용하면 이미지를 더 유연하게 처리할 수 있으며 템플릿을 원하는 대로 조정할 수 있습니다.

