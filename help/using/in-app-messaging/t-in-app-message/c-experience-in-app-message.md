---
description: 표시 유형(전체 화면, 경고 또는 알림), 텍스트 및 단추 옵션 등 인앱 메시지의 환경 옵션을 구성합니다.
keywords: mobile
seo-description: 표시 유형(전체 화면, 경고 또는 알림), 텍스트 및 단추 옵션 등 인앱 메시지의 환경 옵션을 구성합니다.
seo-title: 경험 인앱 메시지
solution: Marketing Cloud,Analytics
title: 경험 인앱 메시지
topic: 지표
uuid: 4c6d6756-47fb-4f1b-8338-0b0c9b0fceb0
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Experience: in-app message {#experience-in-app-message}

표시 유형(전체 화면, 경고 또는 알림), 텍스트 및 단추 옵션 등 인앱 메시지의 환경 옵션을 구성합니다.

1. In your app, click **[!UICONTROL Messaging]** &gt; **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]** &gt; **[!UICONTROL Create In-App]**.
1. 환경 페이지에서 메시지 이름을 입력합니다.
1. **[!UICONTROL 유형]섹션의 필드를 작성합니다.**

   * **[!UICONTROL Type
Select the message type for your in-app message campaign:]**

      * **[!UICONTROL 전체 화면]**
      * **[!UICONTROL 경고]**
      * **[!UICONTROL 로컬 알림]**
   * **[!UICONTROL 템플릿]**

      컨텐츠에 대한 테마 응답 메시지 템플릿을 사용자 지정합니다.

      >[!TIP]
      >
      >This option is displayed only when you select the **[!UICONTROL Full Screen]** message type.

   * **[!UICONTROL 사용자 지정]**

      사용자 지정 HTML 컨텐츠를 로드합니다(전체 화면만). 클릭스루 링크와 취소 링크를 제공해야 합니다.

      1. **[!UICONTROL 찾아보기]를 클릭하고 HTML 파일을 다운로드하거나 HTML 문서를 창으로 드래그합니다.**
      1. 샘플 사용자 지정 HTML 컨텐츠를 보려면 **[!UICONTROL 예제 다운로드]를 클릭하십시오.**
      >[!TIP]
      >
      >This option is displayed only when you select the **[!Full Screen]** message type.



1. **[!UICONTROL 표시]섹션의 필드를 작성합니다.**

   * **[!UICONTROL 테마]**
   메시지의 테마를 선택합니다.

   * **[!UICONTROL 레이아웃]**

      장치 화면에서 앱 레이아웃을 선택합니다.

   * **[!UICONTROL 이미지 URL]**

      이미지의 URL. If you have sizing issues when using the full-screen template, see *My image does not fit exactly into the space provided by the template* in [Troubleshooting in-app messaging](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).

   * **[!UICONTROL 번들 이미지]**

      앱 코드 번들에 있는 이미지 경로. 이 옵션은 이미지가 없거나 이미지를 사용할 수 없는 경우에 사용됩니다. 예를 들어, 장치가 오프라인 상태인 경우 이미지를 사용하지 못할 수도 있습니다. If you have sizing issues when using the full-screen template, see *My image does not fit exactly into the space provided by the template* in [Troubleshooting in-app messaging](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).


1. **[!UICONTROL 텍스트]섹션의 필드를 작성합니다.**

   * **[!UICONTROL 헤더]**

      메시지 머리글에 대한 텍스트를 입력합니다.

   * **[!UICONTROL 컨텐츠]**

      메시지 컨텐츠에 대한 텍스트를 입력합니다.

1. **[!UICONTROL 단추]섹션의 필드를 작성합니다.**

   * **[!UICONTROL 클릭스루 단추]**

      **[!UICONTROL 클릭스루]단추에 대한 레이블입니다.** 이 단추를 누르면 성공적인 클릭스루로 카운트됩니다. 사용자가 대상으로 리디렉션됩니다.

   * **[!UICONTROL 대상]**

      사용자가 메시지를 클릭스루한 경우 보낼 특정 대상(예: 웹 링크, 딥링크 또는 하이브리드 링크)을 선택합니다. 성공적인 클릭스루에 대한 리디렉션 URL.

      이 URL에는 다음 정보가 포함될 수 있습니다.

      * `{userId}`으로 대체되거나 사용자 식별자가 설정되지 않은 경우 비어 있게 됩니다.
      * `{trackingId}`으로 대체됩니다. 이 값은 *s_vi 쿠키와 관련됨* )
      * `{messageId}`, which is replaced with the unique ID for the in-app message.
      * `{lifetimeValue}`, which is replaced with the lifetime value or 0 if no lifetime value exists.
      Here is an example of tracking the user ID: `https://www.mysite.com?uid={userId}`.

      If the click-through URL uses `https://` or `https://`, the URL opens in the device browser outside the app. 그렇지 않으면 각 플랫폼에서는 앱이 사용자 지정 구성표를 지원하도록 개발된 경우 앱을 열거나 참조할 수 있게 해주는 구성표를 지원합니다.

      >[!TIP]
      >
      >When you use the **[!UICONTROL Web Link]** or **[!UICONTROL Custom Link]** destination types, the destination type is not tracked. **[!UICONTROL 딥링크]만 추적됩니다.** For more information, see [Destinations](/help/using/acquisition-main/c-create-destinations.md).


1. (선택 사항) 다음 아이콘을 클릭하여 메시지 레이아웃을 미리 보기합니다.

   * **[!UICONTROL [요약]** ]은 미리 보기 창을 숨깁니다.

      Click ![preview](assets/icon_preview.png) to redisplay the preview pane.

   * **[!UICONTROL Change the orientation]**

      To change the orientation of the preview from portrait to landscape mode, click ![orientation](assets/icon_orientation.png). 시계의 경우 방향이 원면에서 정사각형 시계 면으로 변경됩니다.

   * **[!UICONTROL Preview on a user's watch]**

      To preview your message as it will appear on a user's watch, click watch icon.![](assets/icon_watch.png)

   * **[!UICONTROL Preview on a user's mobile phone]**

      To preview your message as it will appear on a users's mobile phone click phone icon.![](assets/icon_phone.png)

   * **[!UICONTROL Preview on a user's tablet]**

      To preview your message in a user's tablet, click tablet icon.![](assets/icon_tablet.png)

      미리 보기 패널의 맨 아래에서, 이전 단계에서 선택한 대상에 대한 설명을 볼 수 있습니다. 미리 보기 창의 하단에서 이전 단계에서 선택한 대상에 대한 설명을 볼 수도 있습니다.

1. Configure Schedule options.[](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md)
