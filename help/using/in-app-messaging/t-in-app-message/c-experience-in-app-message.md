---
description: 표시 유형(전체 화면, 경고 또는 알림), 텍스트 및 단추 옵션 등 인앱 메시지의 환경 옵션을 구성합니다.
keywords: mobile
seo-description: 표시 유형(전체 화면, 경고 또는 알림), 텍스트 및 단추 옵션 등 인앱 메시지의 환경 옵션을 구성합니다.
seo-title: 앱 내 메시지 사용
solution: Marketing Cloud, Analytics
title: 앱 내 메시지 사용
topic: 지표
uuid: 4 C 6 D 6756-47 FB -4 F 1 B -8338-0 B 0 C 9 B 0 FCEB 0
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Experience: in-app message {#experience-in-app-message}

표시 유형(전체 화면, 경고 또는 알림), 텍스트 및 단추 옵션 등 인앱 메시지의 환경 옵션을 구성합니다.

1. In your app, click **[!UICONTROL Messaging]** &gt; **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]** &gt; **[!UICONTROL Create In-App]**.
1. 환경 페이지에서 메시지 이름을 입력합니다.
1. **[!UICONTROL 유형]섹션의 필드를 작성합니다.**

   * **[!UICONTROL 입력]**
인앱 메시지 캠페인에 대한 메시지 유형을 선택합니다.

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

      **[!UICONTROL 클릭스루]단추에 대한 레이블입니다.** 이 단추를 누르면 성공한 클릭스루로 계산됩니다. 사용자가 대상으로 리디렉션됩니다.

   * **[!UICONTROL 대상]**

      사용자가 메시지를 클릭스루한 경우 보낼 특정 대상(예: 웹 링크, 딥링크 또는 하이브리드 링크)을 선택합니다. 성공적인 클릭스루에 대한 리디렉션 URL.

      이 URL에는 다음 정보가 포함될 수 있습니다.

      * `{userId}`를 사용자 식별자로 바꾸거나 사용자 ID가 설정되지 않은 경우 비어 있습니다.
      * `{trackingId}`로 대체됩니다 *(s_ vi* 쿠키와 상관 관계).
      * `{messageId}`을 입력합니다.
      * `{lifetimeValue}`의 값은 라이프타임 값이 없는 경우 라이프타임 값이나 0로 대체됩니다.
      Here is an example of tracking the user ID: `https://www.mysite.com?uid={userId}`.

      If the click-through URL uses `https://` or `https://`, the URL opens in the device browser outside the app. 그렇지 않으면 각 플랫폼에서는 앱이 사용자 지정 구성표를 지원하도록 개발된 경우 앱을 열거나 참조할 수 있게 해주는 구성표를 지원합니다.

      >[!TIP]
      >
      >**[!UICONTROL 웹 링크]** 또는 **[!UICONTROL 사용자 지정 링크]** 대상 유형을 사용할 때 대상 유형은 추적되지 않습니다. **[!UICONTROL 딥링크]만 추적됩니다.** 자세한 내용은 [대상을](/help/using/acquisition-main/c-create-destinations.md)참조하십시오.


1. (선택 사항) 다음 아이콘을 클릭하여 메시지 레이아웃을 미리 보기합니다.

   * **[!UICONTROL 요약은]** 미리 보기 창을 숨깁니다.

      Click ![preview](assets/icon_preview.png) to redisplay the preview pane.

   * **[!UICONTROL 방향 변경]**

      To change the orientation of the preview from portrait to landscape mode, click ![orientation](assets/icon_orientation.png). 시계의 경우 방향이 원형에서 정사각형으로 바뀝니다.

   * **[!UICONTROL 사용자 보기 미리 보기]**

      메시지가 사용자의 감시 화면에 나타날 때 미리 보려면 ![[감시 아이콘](assets/icon_watch.png)] 를 클릭합니다.

   * **[!UICONTROL 사용자의 휴대폰에서 미리 보기]**

      메시지가 사용자의 휴대폰에 나타날 때 메시지를 미리 보려면 ![전화 아이콘을 클릭합니다](assets/icon_phone.png).

   * **[!UICONTROL 사용자의 태블릿에서 미리 보기]**

      사용자의 태블릿에서 메시지를 미리 보려면 ![태블릿 아이콘을](assets/icon_tablet.png)클릭합니다.

      미리 보기 패널의 맨 아래에서, 이전 단계에서 선택한 대상에 대한 설명을 볼 수 있습니다. 미리 보기 창의 하단에서 이전 단계에서 선택한 대상에 대한 설명을 볼 수도 있습니다.

1. 예약 옵션 구성을 [](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md)참조하십시오.
