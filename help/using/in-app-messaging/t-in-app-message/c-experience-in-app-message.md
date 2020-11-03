---
description: 표시 유형(전체 화면, 경고 또는 알림), 텍스트 및 단추 옵션 등 인앱 메시지의 환경 옵션을 구성합니다.
keywords: mobile
seo-description: 표시 유형(전체 화면, 경고 또는 알림), 텍스트 및 단추 옵션 등 인앱 메시지의 환경 옵션을 구성합니다.
seo-title: '환경: 인앱 메시지'
solution: Experience Cloud,Analytics
title: '환경: 인앱 메시지'
topic: Metrics
uuid: 4c6d6756-47fb-4f1b-8338-0b0c9b0fceb0
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '686'
ht-degree: 100%

---


# 환경: 인앱 메시지 {#experience-in-app-message}

표시 유형(전체 화면, 경고 또는 알림), 텍스트 및 단추 옵션 등 인앱 메시지의 환경 옵션을 구성합니다.

1. 앱에서 **[!UICONTROL 메시징]** > **[!UICONTROL 메시지 관리]** > **[!UICONTROL 메시지 작성]** > **[!UICONTROL 앱 내 메시지 만들기]**&#x200B;를 클릭합니다.
1. 환경 페이지에서 메시지 이름을 입력합니다.
1. **[!UICONTROL 유형]** 섹션의 필드를 작성합니다.

   * **[!UICONTROL 유형]**
인앱 메시지 캠페인에 대한 메시지 유형을 선택합니다.

      * **[!UICONTROL 전체 화면]**
      * **[!UICONTROL 경고]**
      * **[!UICONTROL 로컬 알림]**
   * **[!UICONTROL 템플릿]**

      컨텐츠에 대한 테마 응답 메시지 템플릿을 사용자 지정합니다.

      >[!TIP]
      >
      >이 옵션은 **[!UICONTROL 전체 화면]** 메시지 유형을 선택한 경우에만 표시됩니다.

   * **[!UICONTROL 사용자 지정]**

      사용자 지정 HTML 컨텐츠를 로드합니다(전체 화면만). 클릭스루 링크와 취소 링크를 제공해야 합니다.

      1. **[!UICONTROL 찾아보기]**&#x200B;를 클릭하고 HTML 파일을 다운로드하거나 HTML 문서를 창으로 드래그합니다.
      1. 샘플 사용자 지정 HTML 컨텐츠를 보려면 **[!UICONTROL 예제 다운로드]**&#x200B;를 클릭하십시오.

      >[!TIP]
      >
      >이 옵션은 **[!F전체 화면]** 메시지 유형을 선택한 경우에만 표시됩니다.



1. **[!UICONTROL 표시]** 섹션의 필드를 작성합니다.

   * **[!UICONTROL 테마]**

   메시지의 테마를 선택합니다.

   * **[!UICONTROL 레이아웃]**

      장치 화면에서 앱 레이아웃을 선택합니다.

   * **[!UICONTROL 이미지 URL]**

      이미지의 URL. 전체 화면 템플릿을 사용할 때 크기 조절 문제가 발생하면 [인앱 메시징 문제 해결](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md)에서 *내 이미지가 템플릿에서 제공한 공간에 정확히 맞지는 않습니다*&#x200B;를 참조하십시오.

   * **[!UICONTROL 번들 이미지]**

      앱 코드 번들에 있는 이미지에 대한 경로입니다. 이 옵션은 이미지가 없을 때 사용됩니다. 또는 이미지를 사용할 수 없을 때 사용됩니다. 예를 들어, 장치가 오프라인 상태인 경우 이미지를 사용하지 못할 수도 있습니다. 전체 화면 템플릿을 사용할 때 크기 조절 문제가 발생하면 [인앱 메시징 문제 해결](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md)에서 *내 이미지가 템플릿에서 제공한 공간에 정확히 맞지는 않습니다*&#x200B;를 참조하십시오.


1. **[!UICONTROL 텍스트]** 섹션의 필드를 작성합니다.

   * **[!UICONTROL Header]**

      메시지 머리글에 대한 텍스트를 입력합니다.

   * **[!UICONTROL 컨텐츠]**

      메시지 컨텐츠에 대한 텍스트를 입력합니다.

1. **[!UICONTROL 단추]** 섹션의 필드를 작성합니다.

   * **[!UICONTROL 클릭스루 단추]**

      **[!UICONTROL 클릭스루]** 단추에 대한 레이블입니다. 이 단추를 탭하면 성공한 클릭스루로 계산됩니다. 사용자가 대상으로 리디렉션됩니다.

   * **[!UICONTROL 대상]**

      사용자가 메시지를 클릭스루한 경우 보낼 특정 대상(예: 웹 링크, 딥링크 또는 하이브리드 링크)을 선택합니다. 성공적인 클릭스루에 대한 리디렉션 URL.

      이 URL에는 다음 정보가 포함될 수 있습니다.

      * `{userId}`: 사용자 ID로 교체되거나, 사용자 ID가 설정되지 않은 경우 비어 있습니다.
      * `{trackingId}`: aid(*s_vi* 쿠키와 상관 관계가 있음)로 대체됩니다.
      * `{messageId}`: 인앱 메시지에 대한 고유한 ID로 대체됩니다.
      * `{lifetimeValue}`: 라이프타임 값으로 대체되거나, 라이프타임 값이 없는 경우 0으로 대체됩니다.

      다음은 사용자 ID 추적의 예입니다. `https://www.mysite.com?uid={userId}`

      클릭스루 URL에서 `https://` 또는 `https://`를 사용하는 경우 URL이 앱 외부의 장치 브라우저에서 열립니다. 그렇지 않으면 각 플랫폼에서는 앱이 사용자 지정 구성표를 지원하도록 개발된 경우 앱을 열거나 참조할 수 있게 해주는 구성표를 지원합니다.

      >[!TIP]
      >
      >**[!UICONTROL 웹 링크]** 또는 **[!UICONTROL 사용자 지정 링크]** 대상 유형을 사용하는 경우 대상 유형이 추적되지 않습니다. **[!UICONTROL 딥링크]**&#x200B;만 추적됩니다. 자세한 내용은 [대상](/help/using/acquisition-main/c-create-destinations.md)을 참조하십시오.


1. (선택 사항) 다음 아이콘을 클릭하여 메시지 레이아웃을 미리 보기합니다.

   * **[!UICONTROL 요약]**&#x200B;은 미리 보기 창을 숨깁니다.

      미리 보기 창을 다시 표시하려면 ![미리 보기](assets/icon_preview.png)를 클릭합니다.

   * **[!UICONTROL 방향 변경]**

      미리 보기 방향을 세로에서 가로 모드로 변경하려면 ![방향](assets/icon_orientation.png)을 클릭합니다. 시계의 경우, 방향이 둥근 시계 면에서 사각 시계 면으로 바뀝니다.

   * **[!UICONTROL 사용자의 시계에서 미리 보기]**

      사용자의 시계에 표시되는 메시지를 미리 보려면 ![시계 아이콘](assets/icon_watch.png)을 클릭합니다.

   * **[!UICONTROL 사용자의 휴대폰에서 미리 보기]**

      사용자의 휴대폰에 표시되는 메시지를 미리 보려면 ![전화 아이콘](assets/icon_phone.png)을 클릭합니다.

   * **[!UICONTROL 사용자의 태블릿에서 미리 보기]**

      사용자의 태블릿에서 메시지를 미리 보려면 ![태블릿 아이콘](assets/icon_tablet.png)을 클릭합니다.

      미리 보기 패널의 맨 아래에서, 이전 단계에서 선택한 대상에 대한 설명을 볼 수 있습니다. 미리 보기 창의 하단에서 이전 단계에서 선택한 대상에 대한 설명을 볼 수도 있습니다.

1. [예약 옵션](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md)을 구성합니다.
