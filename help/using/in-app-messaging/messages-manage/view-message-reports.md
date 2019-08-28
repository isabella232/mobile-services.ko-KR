---
description: 인앱 및 푸시 메시지에 대한 메시지 보고서를 볼 수 있습니다.
keywords: mobile
seo-description: 인앱 및 푸시 메시지에 대한 메시지 보고서를 볼 수 있습니다.
seo-title: 메시지 보고서 보기
solution: Marketing Cloud, Analytics
title: 메시지 보고서 보기
topic: 지표
uuid: 0 ac 73 a 81-388 f -4 dfd -84 d 5-21 b 8 db 4 b 8 c 83
translation-type: tm+mt
source-git-commit: 44f531ad140827d563255fad197811185c5337c9

---


# View message reports{#view-message-reports}

인앱 및 푸시 메시지에 대한 메시지 보고서를 볼 수 있습니다.

1. Click ![report icon](assets/icon_report.png) in the **[!UICONTROL Report]** column for a message.
1. (**Optional**) Create a sticky filter for the report or change the time period by clicking the **[!UICONTROL Calendar]** icon.

   고정 필터 만들기에 대한 자세한 내용은 고정 필터 [추가를](/help/using/usage/reports-customize/t-sticky-filter.md)참조하십시오.

>[!TIP]
>
>보고 있는 메시지의 유형에 따라 보고서가 달라질 수 있습니다.

## 인앱 메시지 {#section_90B79BA58E8141F78538C187EB1BF8C7}

인앱 메시지에 대한 보고서를 표시하는 경우 보고서는 아래 그림과 유사합니다.

![보고서 메시지](assets/report_message.png)

### 인앱 메시지 지표

다음은 인앱 메시지에 사용할 수 있는 지표 목록입니다.

* **[!UICONTROL 임프레션]**, 메시지가 트리거될 때.

* **[!UICONTROL Click through]**, when a user press the **[!UICONTROL click through]** button on an alert or full-screen message, and when a user when a local notification.

* **[!UICONTROL 취소할]**&#x200B;때 사용자가 경고 또는 전체 화면 메시지의 **[!UICONTROL 취소]** 단추를 누를 때 취소됩니다.

* **[!UICONTROL 참여 비율]**, Adobe Analytics의 계산된 지표이며 클릭 수를 노출 수로 나눈 결과입니다.

## Push messages {#section_BEAFD858CA194185B6F88903446058E9}

푸시 메시지에 대한 보고서를 표시하는 경우 보고서는 아래 그림과 유사합니다.

![푸시 메시지](assets/report_message_push.png)

맨 위의 차트에는 메시지를 연 사용자의 수가 표시됩니다.

### 푸시 메시지 지표

다음은 푸시 메시지에 사용할 수 있는 지표 목록입니다.

* **[!UICONTROL 시간]**

   메시지가 Mobile Services에서 장치에 푸시된 시간입니다.

* **[!UICONTROL 상태]**

   메시지의 상태 및 사용 가능한 상태는 다음과 같습니다.

   * **[!UICONTROL 취소됨]**
   * **[!UICONTROL 예약됨]**
   * **[!UICONTROL 실행]**
   * **[!UICONTROL executed]**

* **[!UICONTROL 게시됨]**

   사용자 장치에 메시지를 전송하기 위한 Apple 푸시 알림 서비스/Firebase 클라우드 메시지 (APNS/FCM) 로 성공적으로 전송된 장치 토큰 수입니다.

* **[!UICONTROL 실패]**

   APNS/FCM에 성공적으로 전송되지 않는 장치 토큰 수입니다. 실패 원인은 다음과 같습니다.

   * 유효하지 않은 pushID

   * 푸시할 푸시 플랫폼 (APNS, FCM 등) 이 작업 애플리케이션에 대해 존재하지 않습니다. 예를 들어 플랫폼에서 iOS 푸시 토큰을 수집할 수 있지만 APNS 서비스가 구성되어 있지 않습니다.

   * 푸시 서비스가 제대로 구성되지 않았거나 Mobile Services 시스템이 작동 중지되었기 때문에 메시지가 실패했을 수 있습니다.
   >[!IMPORTANT]
   >
   >평소와 달리 실패 횟수가 많을 경우 푸시 서비스 구성을 확인하십시오. 푸시 서비스의 구성이 올바르다면 Adobe 고객 지원에 문의하십시오.

* **[!UICONTROL 블랙 리스트에 추가됨]**

   APNS 또는 FCM에 더 이상 전송되지 않는 장치 토큰 수입니다. 이는 보통 앱이 장치에서 제거되었거나 사용자가 메시지를 수신하기 위한 옵트인 설정을 변경했다는 의미입니다. Android와 iOS는 토큰이 블랙리스트 항목으로 카운트되는 시점이 다릅니다. Android 토큰은 블랙리스트 항목으로 바로 표시됩니다. iOS 토큰은 처음에 게시됨으로 표시되지만, APNS의 피드백에 따라 후속 메시지에서 블랙리스트 항목으로 표시됩니다.
