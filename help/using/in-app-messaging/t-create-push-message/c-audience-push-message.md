---
description: 푸시 메시지에 대해 날짜 범위 옵션, Analytics 세그먼트 및 사용자 지정 세그먼트 등의 대상 옵션을 정의하고 구성할 수 있습니다.
keywords: mobile
seo-description: 푸시 메시지에 대해 날짜 범위 옵션, Analytics 세그먼트 및 사용자 지정 세그먼트 등의 대상 옵션을 정의하고 구성할 수 있습니다.
seo-title: 대상 푸시 메시지에 대한 대상 세그먼트 정의 및 구성
solution: Marketing Cloud,Analytics
title: 대상 푸시 메시지에 대한 대상 세그먼트 정의 및 구성
topic: 지표
uuid: efd410e7-3b6c-4cf4-a26f-b11688adc491
translation-type: tm+mt
source-git-commit: f28ea0db13b8d8f209d7521d1f61f1c290e688aa

---


# 대상:푸시 메시지{#audience-define-and-configure-audience-segments-for-push-messages}

푸시 메시지에 대해 날짜 범위 옵션, Analytics 세그먼트 및 사용자 지정 세그먼트 등의 대상 옵션을 정의하고 구성할 수 있습니다.

## Define audience segments {#section_7C4D2393CF7441959FE2381A02867CAC}

푸시 메시지에 대한 대상 세그먼트가 생성될 때 세그먼트에는 하나 이상의 앱 사용자가 포함될 수도 있습니다. 보고서 세트 또는 가상 보고서 세트에 하나 이상의 앱 데이터가 있을 수 있기 때문입니다. 가상 보고서 세트에 대한 자세한 내용은 [Virtual report suites](/help/using/manage-apps/c-mob-vrs.md).

Adobe Mobile Services에서 마케터는 플랫폼당 하나의 앱으로만 푸시할 수 있습니다. 마케터가 여러 앱의 사용자를 포함하는 세그먼트로 푸시하려고 하면 계속 진행할 경우 심각한 푸시 오류가 발생할 수 있으며 사용자가 블랙리스트에 추가될 수 있다는 경고가 표시됩니다. 푸시가 실패하는 경우 *푸시 문제 해결*( [Troubleshooting push messaging](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md).

세그먼트 정의에 Audience Manager 데이터를 사용하려면 [Audience Analytics](https://docs-author-stg.corp.adobe.com/content/help/en/analytics/integration/audience-analytics/mc-audiences-aam.html)를 참조하십시오.

>[!IMPORTANT]
>
>If app users are blacklisted, marketers can **never** send push messages to those affected users again.

여러 앱에서 사용자가 포함된 대상 세그먼트를 선택하면 다음 경고가 표시될 수 있습니다.

![다중 앱 이름](assets/multiple_appname.png)

The app name is based on the pared down version of the appId, which is automatically sent to Adobe Analytics by the Mobile Services SDK in the `<app name> <version number> (<bundle id>)` format.

>[!TIP]
>
>버전 번호는 선택 사항입니다.

버전의 경우 최대 6개의 숫자 세트가 제거되고, 번들 ID의 경우 최대 5개의 숫자 세트가 제거됩니다.

예:

* `Bea[rd]cons 1.0 (123)` 가 `Bea[rd]cons`
* `Bea[rd]cons 1.2 (1.2)` 가 `Bea[rd]cons`
* `Bea[rd]cons 1.2.3.4.5.6.7 (1111)` 가 `Bea[rd]cons .7`
* `Bea[rd]cons 1.2.3. (1.2.3.4.5.6)` 가 `Bea[rd]cons (.6)`

표시된 앱으로 푸시 메시지를 계속 보내려면 **예, 진행하겠습니다.** check box and click **[!UICONTROL Send]**.

## 우수 사례

다음은 기억해야 할 몇 가지 우수 사례입니다.

* 혼동을 줄이기 위해 여러 앱의 데이터를 포함하는 모바일 앱 가상 보고서 세트를 정의하지 **마십시오**.
* 푸시 메시지를 전송할 때&#x200B;**마다** 고유한 앱 ID를 대상 세그먼트의 일부로 사용합니다.
이렇게 하면 한 앱**에만** 속하는 대상 세그먼트로 푸시 알림이 전송됩니다.

### 예

다음은 세그먼트를 올바르게 정의하는 방법을 이해하는 데 도움이 되는 몇 가지 예입니다.

**수행할 작업**: 마케터는 Adobe Photoshop 등에 iOS 및 Android의 한 앱 버전에 대한 푸시 인증을 제공합니다. 마케터가 두 플랫폼에 분할된 사용자 세그먼트로 푸시 알림을 보낼 수 있습니다.

**수행하지 않을 작업**: 마케터는 Adobe Photoshop 등에 한 개 앱의 iOS 및 Android의 버전에 대한 푸시 인증서를 제공합니다. 마케터가 *최근 30일 동안 모든 활성 사용자*&#x200B;의 세그먼트로 생성하고 푸시하면 Adobe Photoshop iOS 및 Android 앱 사용자만 해당 푸시를 받고, Adobe Illustrator iOS 및 Android 앱 사용자는 모두 블랙리스트에 추가됩니다. 자세한 예는 *푸시 메시지 오류 해결*( [푸시 메시지 문제 해결](/help/using/in-app-messaging/t-create-push-message/c-troubleshooting-push-messaging.md))을 참조하십시오.

## Configure audience segments {#section_A92C60885A30421B8150820EC1CCBF13}

1. 대상 페이지로 이동하여 새 푸시 메시지를 표시합니다.

   For more information, see [Create a push message](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md).

   As you configure the audience options, remember the following **important** information:

   * **[!UICONTROL 예상 옵트인 대상]**&#x200B;은 Adobe Analytics 세그먼트&#x200B;**와** 옵트인 장치 수가 일치하는 장치 수입니다.

      선택한 세그먼트에서 메시지를 받도록 선택했고, 푸시 메시지를 받게 되는 사용자의 수에 대한 예상치를 볼 수 있습니다. 총 앱 사용자 수는 옵트인 상태에 상관없이 예상치 아래에 표시됩니다.

   * **[!UICONTROL 합계]는 Adobe Analytics 세그먼트와 일치하는 장치 수입니다.**

   * Push messages are sent to the devices that are part of a defined Adobe Analytics segment **and** that have opted-in for push messages.

      즉, SDK가 푸시 메시지 옵트인 evar에 대해 `True` 값을 보냈습니다.

   * 장치에 유효한 장치 토큰이 있어도 Adobe Analytics에서 옵트인 플래그를 설정하지 않으면 메시지가 장치로 푸시되지 않습니다.

   * 푸시 메시지 문제 해결에 대한 자세한 내용은 다음을 참조하십시오.

      * [iOS에서 푸시 메시지](https://docs.adobe.com/content/help/en/mobile-services/ios/messaging-ios/push-messaging/push-messaging.html)

      * [Android의 푸시 메시지](https://docs.adobe.com/content/help/en/mobile-services/android/messaging-android/push-messaging/push-messaging.html)

1. 다음 필드에 정보를 입력하십시오.

   * **[!UICONTROL 다음 기간 동안]**

      예상 대상에 사용할 기간을 입력합니다. **[!UICONTROL 다음 기간 동안]드롭다운 목록에서 옵션을 선택합니다.**

   * **[!UICONTROL 마지막]**: 메시지가 푸시되도록 예약된 시간으로부터 상대적인 기간(예: 최근 7일, 최근 30일 또는 최근 60일)을 선택할 수 있습니다.

      예를 들어, 최근 30일을 선택하고 10월 31일에 메시지가 푸시되도록 예약하는 경우, 예상 대상은 10월 31일부터 30일 전에 푸시 메시지를 받도록 선택한 사용자의 수가 됩니다.

   * **[!UICONTROL 정적 범위]**: 예상 대상 범위에 대한 시작 날짜와 종료 날짜를 선택하여 정적 범위를 선택할 수 있습니다.

      앞의 예를 사용하여, 날짜 범위를 10월 1일에 시작하여 10월 15일에 끝나도록 선택하되, 10월 31일에 메시지가 푸시되도록 예약하는 경우, 예상 대상은 지정한 정적 날짜 범위(10월 1일부터 10월 15일까지)에서 푸시 메시지를 받도록 선택한 사용자의 수가 됩니다.

   * **[!UICONTROL Analytics 세그먼트]**

      드롭다운 목록에서 기존 Adobe Analytics 세그먼트를 선택합니다. For more information, see [Build segments](https://docs.adobe.com/content/help/en/analytics/components/segmentation/segmentation-workflow/seg-build.html).

   * **[!UICONTROL 사용자 지정 세그먼트]**

      Select a metric or variable from the drop-down list (for example, **[!UICONTROL Days Since Last Use]** or **[!UICONTROL Point of Interest]**) and configure the filter as desired. 예를 들어, 다음 사용자 지정 세그먼트는 iOS를 실행하는 휴대 전화를 사용하고, 캘리포니아(미국) 지역 내에 있는 사용자를 타깃팅합니다.
   >[!IMPORTANT]
   >
   >In the **[!UICONTROL Create Audience]** section, if you click **[!UICONTROL And]**, a dialog box appears that reminds you to ensure that each app that is listed **must** have a valid certificate. If you clicked **[!UICONTROL Or]**, the default dialog box appears. For more information about valid certificates and report suites, see [Virtual report suites](/help/using/manage-apps/c-mob-vrs.md).
