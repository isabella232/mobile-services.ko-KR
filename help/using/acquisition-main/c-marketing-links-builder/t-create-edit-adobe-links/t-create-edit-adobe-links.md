---
description: 마케팅 링크를 만들거나 편집하여 모바일 앱이나 웹 사이트로 딥링크를 제공할 수 있습니다.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: 마케팅 링크 만들기 또는 편집
topic-fix: Metrics
uuid: 305a8265-38de-4d19-8c79-b3912f5aae7c
exl-id: a9b5c98d-77c1-4a40-96e5-f9e234d55ec5
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 98%

---

# 마케팅 링크 만들기 또는 편집{#create-or-edit-marketing-links}

{#eol}

마케팅 링크를 만들거나 편집하여 모바일 앱이나 웹 사이트로 딥링크를 제공할 수 있습니다. 자세한 내용은 [Apple 범용 링크 및 Android 앱 링크](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)를 참조하십시오.

1. 앱의 왼쪽 탐색 창에서 **[!UICONTROL 획득]**&#x200B;을 확장하고 **[!UICONTROL 마케팅 링크 빌더]**&#x200B;를 클릭합니다.
1. 다음 작업 중 하나를 완료하십시오.

   * 마케팅 링크를 만들려면 **[!UICONTROL 새로 만들기]**&#x200B;를 클릭합니다.
   * 링크를 편집하려면 **[!UICONTROL 제목]** 열에서 링크 이름을 클릭합니다.

1. 다음 필드에 정보를 입력하십시오.

   * **[!UICONTROL 마케팅 링크 이름]**:

      (**필수**) 마케팅 링크를 설명하는 이름을 지정합니다. 이 이름은 Adobe Mobile Services UI의 마케팅 링크 페이지에만 표시됩니다. 수사적 이름은 작성자나 조직의 다른 직원이 특정 링크를 신속하게 찾을 수 있게 하고 링크를 만든 목적에 대한 자세한 설명을 제공합니다.

   * **[!UICONTROL 고유한 추적 코드]**:

      (**필수**) 원하는 추적 코드를 지정하거나 (![생성 아이콘](assets/icon_generate.png))을 클릭하여 새 추적 코드를 만듭니다. 추적 코드 사용에 관한 자세한 내용이 담긴 보고서를 볼 수 있습니다.

   * **[!UICONTROL 추적 컨텍스트 데이터 추가]**:

      **선택사항** - ****+ 아이콘을 클릭하고 관련 정보를 입력하여 컨텍스트 데이터로 캠페인을 추적합니다. **[!UICONTROL 사용자 지정 컨텍스트 데이터]** 드롭다운 목록에서 사전 설정된 태그 또는 고유한 태그 중 하나를 선택합니다. 마케팅 링크가 배포될 때 보고 목적으로 컨텍스트 데이터가 사용됩니다.

      다음 사전 설정 태그를 사용할 수 있습니다.

      * **사용자 지정 컨텍스트 데이터**
키와 값을 지정합니다. 사용자 지정 컨텍스트 데이터를 추가할 경우 처리 규칙을 작성해야 합니다. 자세한 내용은 [처리 규칙 개요](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) Adobe Analytics 설명서에서 확인할 수 있습니다.

      * **소스**
&quot;뉴스레터&quot; 또는 &quot;홈 페이지&quot;와 같은 원본 레퍼러를 지정합니다.

      * **매체**
&quot;배너&quot; 또는 &quot;이메일&quot;과 같은 마케팅 매체를 지정합니다.

      * **콘텐츠**
링크가 있는 광고의 이름이나 ID를 지정합니다.

      * **용어**
광고의 유료 용어나 기타 검색어를 지정합니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
1. 다음 필드에 정보를 입력하십시오.

   * **(필수)** **[!UICONTROL 대체 URL]**&#x200B;에 일치하는 대상을 찾을 수 없는 경우 사용자에게 안내되는 URL을 지정합니다(예: 사용자가 대상 규칙과 일치하지 않는 데스크탑이나 다른 플랫폼에서 작업하는 경우).
   * **[!UICONTROL 마케팅 링크 옵션]**&#x200B;에서 **[!UICONTROL 삽입 광고]** 또는 **[!UICONTROL 범용 및 앱 링크를 선택합니다]**.

      자세한 내용은 [삽입 광고](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md) 또는 [Apple 범용 링크 및 Android 앱 링크](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)를 참조하십시오.

   * **(조건)** **[!UICONTROL 사용자 지정 경로]**&#x200B;에서 **[!UICONTROL 범용 또는 앱 링크]**&#x200B;가 선택되어 있으면 사용자가 모든 쿼리 매개 변수를 사용하여 도메인 뒤에 URL 경로를 정의할 수 있습니다. 자세한 내용은 [Apple 범용 링크 및 Android 앱 링크](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)를 참조하십시오.

1. **[!UICONTROL 딥링크 삽입 광고 편집]**&#x200B;을 클릭하고 링크를 구성합니다.

   (**선택사항**) 여러 대상이 있는 경우 모바일 앱 설치 여부에 따라 사용자를 안내할 수 있습니다. 앱이 설치되면 삽입 광고 랜딩 페이지가 표시됩니다.

   자세한 내용은 [삽입 광고](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md)를 참조하십시오.

1. **[!UICONTROL 저장]**&#x200B;을 클릭하고 **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. 대상 페이지에서 링크를 구성합니다.

   1. **[!UICONTROL 결정]** 아이콘(![결정 아이콘](assets/icon_decision.png))을 클릭하고 다음 결정 위치 중 하나를 선택합니다. 

      * **[!UICONTROL 결정 추가]**
      * **[!UICONTROL 경로 추가]**
   1. **[!UICONTROL 결정 추가]**&#x200B;를 선택한 경우 다음 결정 유형 중 하나를 선택합니다.

      * **[!UICONTROL 운영 결정]**

         지원되는 운영 체제는 iOS, Android, AMX 등입니다.

      * **[!UICONTROL 장치 유형]**

         장치 유형에는 데스크톱, eReader, 게임 콘솔, 휴대 전화, 셋톱 박스 등과 같은 장치가 있습니다.
   1. **[!UICONTROL 대상]** 아이콘(![사각형 아이콘](assets/icon_square.png))을 클릭하고 다음 대상 유형 중 하나를 선택합니다. 

      * **[!UICONTROL 앱스토어]**
      * **[!UICONTROL 웹 링크]**
      * **[!UICONTROL 앱 딥링크]**
      * **[!UICONTROL 하이브리드 링크]**

      >[!TIP]
      >
      >앱스토어에 대한 링크에서 **[!UICONTROL 웹 링크]** 대상 유형을 사용할 경우 획득이 추적되지 않습니다. 획득을 추적하려면 **[!UICONTROL 앱스토어]** 대상 유형을 사용합니다.

      자세한 내용은 [새 링크 대상 만들기](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md)를 참조하십시오.




1. 마케팅 링크를 저장하려면 가져오기를 클릭한 ![줄임표](assets/icon_elipses.png)를 클릭한 다음 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
