---
description: Adobe Mobile Services UI에서 즉시 전달할 푸시 메시지, 나중에 전달할 푸시 메시지 및 반복 이벤트로 전달할 푸시 메시지를 예약할 수 있습니다. 이러한 이벤트는 매일, 매주 또는 매월 예약할 수 있습니다.
keywords: mobile
seo-description: Adobe Mobile Services UI에서 즉시 전달할 푸시 메시지, 나중에 전달할 푸시 메시지 및 반복 이벤트로 전달할 푸시 메시지를 예약할 수 있습니다. 이러한 이벤트는 매일, 매주 또는 매월 예약할 수 있습니다.
seo-title: Schedule  Push Message
solution: Marketing Cloud,Analytics
title: 푸시 메시지 예약
topic: 지표
uuid: 6810e27a-016f-4286-8fe2-9972d85fa326
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# 일정:푸시 메시지{#schedule-push-message}

Adobe Mobile Services UI에서 즉시 전달할 푸시 메시지, 나중에 전달할 푸시 메시지 및 반복 이벤트로 전달할 푸시 메시지를 예약할 수 있습니다. 이러한 이벤트는 매일, 매주 또는 매월 예약할 수 있습니다.

>[!TIP]
>
>사용자는 언제든지 푸시 메시지 작업에 대한 예약 설정을 수정할 수 있습니다. 반복 예약된 메시지를 보낼 수 있는 해당 날짜가 없는 경우(예: 매월 31일마다, 2월 31일 또는 매월 5번째 화요일) 메시지가 전송되지 않습니다.

다음 정보를 숙지하십시오.

* The correct date and time format is `hh:mm` and `mm/dd/yyyy`.

* 예약된 메시지는 다음 방법으로 편집할 수 있습니다.

   * 날짜를 나중 날짜로 변경합니다.
   * 반복 간격을 다른 간격으로 변경합니다.

      예를 들어, 원래 매일 전송된 메시지가 있던 경우 반복을 매주로 전환할 수 있습니다.

## 반복 푸시 메시지 예약 전

반복 푸시 메시지를 예약하기 전에 다음 정보를 이해&#x200B;**해야** 합니다.

* **[!UICONTROL 반복]드롭다운 목록에 표시되는 옵션은 입력하거나 선택한 날짜에 따라 다릅니다.**

   예를 들어 입력한 경우 `Saturday, October 7`다음 옵션이 표시됩니다.

   * **[!UICONTROL 절대 안 함]**
   * **[!UICONTROL 매일]**
   * **[!UICONTROL 매주 토요일]**
   * **[!UICONTROL 매월 7일]**
   * **[!UICONTROL 매월 첫 번째 주 토요일]**

* 푸시 메시지는 GMT(그리니치 표준시)를 기준으로 예약되고 전송됩니다.

   예를 들어, **PST**&#x200B;를 기준으로 매주 토요일 오후 12시(정오)에 반복 메시지를 전송하도록 예약한 경우, **GMT**&#x200B;로 토요일 오후 7시에 메시지가 실제로 전송됩니다.
* 메시지는 현재 위치가 미국, 유럽 또는 아시아인지에 따라 다르게 전송됩니다.

   예를 들어 캘리포니아 산호세에서 **PST**&#x200B;로 ***10월 31일*** 오후 5시 30분에 메시지를 전송하도록 예약한 경우 메시지는 실제로 **GMT**&#x200B;로 ***11월 1일*** 오전 12시 30분에 전송됩니다. 도쿄에서 ***1월 1일*** 오전 5시 30분에 메시지를 전송하도록 예약하는 경우 **GMT**&#x200B;로 ***12월 31일*** 오후 8시 30분에 전송됩니다.
* 일광 절약 시간제가 적용되는지에 따라 푸시 메시지는 1시간 빠르게 또는 늦게 전송됩니다.
* 푸시 메시지 보고서를 보면 메시지가 시스템의 현지 시간대로 표시됩니다.

   예를 들어, 시작 시간이 **PST**&#x200B;로 오후 12시인 경우 메시지를 **GMT**&#x200B;로 오후 7시에 전송해도 메시지 보고서에는 **PST**&#x200B;로 오후 12시에 전송된 것으로 시간이 표시됩니다.

## Schedule a recurring push message {#section_675BD754E5A04423A1751193698A978F}

1. 새 푸시 메시지의 예약 페이지에서 예약됨 또는 **[!UICONTROL 지금]** 을 **[!UICONTROL 선택합니다]**.

   For more information, see [Create a push message](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md).

   If you selected **[!UICONTROL Now]**, the message is pushed immediately. 메시지가 즉시 예약되지 않도록 하려면 **[!UICONTROL 초안으로 저장을 클릭합니다]**.

   ![](assets/schedule-push-message.png)

1. If you selected **[!UICONTROL Scheduled]**, click the calendar icon and select or type a start date.
1. 시간을 입력합니다. 
1. Under **[!UICONTROL Repeat]**, select one of the following options:

   * **[!UICONTROL 절대 안 함]**
   * **[!UICONTROL 매일]**
   * **[!UICONTROL 매주 화요일]**
   * **`<Day x>`월**

      표시된 옵션은 시작일로 선택하거나 입력한 날에 따라 변경됩니다.
   * **`<nth day>`of Every Month**

      표시된 값은 시작 날짜로 선택하거나 입력한 날짜에 따라 변경됩니다.

1. In **[!UICONTROL End Repeat]**, type an end date and time.
1. 다음 옵션 중 하나를 클릭합니다.

   * **[!UICONTROL 초안으로 저장]**

      이 옵션은 메시지를 초안 형식으로 저장합니다. 완료되지 않은 메시지를 저장하거나, 활성화 전에 다른 사람이 해당 메시지를 편집하고 승인할 수 있게 하려면 이 옵션을 선택할 수 있습니다.

      If you selected **[!UICONTROL Now]** in the previous step, the draft message is sent immediately on activation. If you selected a date and time to push the message, the message is pushed according to this schedule.

   * **[!UICONTROL 저장 및 예약]**

      이 옵션은 예약된 날짜 및 시간에 메시지를 전송합니다.

초안 메시지를 나중에 푸시하려면 다음 작업 중 하나를 완료하십시오.

* Click **[!UICONTROL Manage Messages]**, select the check box next to the message, and click **[!UICONTROL Activate Selected]**.
* 메시지를 저장 및 발송하려면 **[!UICONTROL 저장 및 보내기]를 클릭하십시오.**
