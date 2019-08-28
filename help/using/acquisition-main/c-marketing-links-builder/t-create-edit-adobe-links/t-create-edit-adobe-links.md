---
description: 마케팅 링크를 만들거나 편집하여 모바일 앱 또는 웹 사이트에 딥 링크를 제공할 수 있습니다.
keywords: mobile
seo-description: 마케팅 링크를 만들거나 편집하여 모바일 앱 또는 웹 사이트에 딥 링크를 제공할 수 있습니다.
seo-title: 마케팅 링크 만들기 또는 편집
solution: Marketing Cloud, Analytics
title: 마케팅 링크 만들기 또는 편집
topic: 지표
uuid: 305 A 8265-38 DE -4 D 19-8 C 79-B 3912 F 5 AAE 7 C
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Create or edit marketing links{#create-or-edit-marketing-links}

마케팅 링크를 만들거나 편집하여 모바일 앱 또는 웹 사이트에 대한 딥 링크를 제공할 수 있습니다. 자세한 내용은 [Apple Universal Link 및 Android 앱 링크를 참조하십시오](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. In your app, in the left navigation pane, expand **[!UICONTROL Acquisition]** and click **[!UICONTROL Marketing Link Builder]**.
1. 다음 작업 중 하나를 완료하십시오.

   * To create a Marketing Link, click **[!UICONTROL Create New]**.
   * 링크를 편집하려면 **[!UICONTROL 제목]열에서 링크 이름을 클릭합니다.**

1. 다음 필드에 정보를 입력하십시오.

   * **[!UICONTROL 마케팅 링크 이름]**:

      (**Required**) Specify a descriptive name for your Marketing Link. 이 이름은 Adobe Mobile Services UI의 마케팅 링크 페이지에만 표시됩니다. 수사적 이름은 작성자나 조직의 다른 직원이 특정 링크를 신속하게 찾을 수 있게 하고 링크를 만든 목적에 대한 자세한 설명을 제공합니다.

   * **[!UICONTROL 고유한 추적 코드]**:

      (**Required**) Specify the desired tracking code or click (![generate icon](assets/icon_generate.png) to create a new tracking code. 추적 코드 사용에 관한 자세한 내용이 담긴 보고서를 볼 수 있습니다.

   * **[!UICONTROL 추적 컨텍스트 데이터 추가]**:

      (**Optional**) Click the **[!UICONTROL +]** icon and type the relevant information to track your campaign using context data. **[!UICONTROL 사용자 지정 컨텍스트 데이터]드롭다운 목록에서 사전 설정된 태그 또는 고유한 태그 중 하나를 선택합니다.** 컨텍스트 데이터는 마케팅 링크가 배포될 때 보고용으로 사용됩니다.

      다음 사전 설정 태그를 사용할 수 있습니다.

      * **사용자 지정 컨텍스트 데이터**
키와 값을 지정합니다. 사용자 지정 컨텍스트 데이터를 추가할 경우 처리 규칙을 작성해야 합니다. 자세한 내용은 [처리 규칙 개요를](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)참조하십시오.

      * **source**
"newsletter" 또는 "homepage" 와 같은 원래 레퍼러를 지정합니다.

      * **보통**
"배너" 또는 "이메일" 와 같은 마케팅 미디어를 지정합니다.

      * **컨텐츠**
링크를 사용하여 광고의 이름 또는 ID를 지정합니다.

      * **기간광고에**
유료 용어나 다른 검색어를 지정합니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
1. 다음 필드에 정보를 입력하십시오.

   * **(필수)** **[!UICONTROL 폴백 URL]**&#x200B;에서 대상을 일치시킬 수 없을 때 (예: 사용자가 데스크톱 또는 대상 규칙과 일치하지 않는 다른 플랫폼에 있는 경우) 사용자에게 안내하는 URL를 지정합니다.
   * **[!UICONTROL 마케팅 링크 옵션]**&#x200B;에서 **[!UICONTROL 삽입 광고]** 또는 **범용 및 앱 링크[!UICONTROL 를 선택합니다]**.

      자세한 내용은 [Interstitials](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md) 또는 [Apple Universal Links 및 Android 앱 링크를 참조하십시오](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

   * **(조건부)** **[!UICONTROL 범용 또는 앱 링크가]** 선택된 경우 **[!UICONTROL 사용자 지정 경로에]**&#x200B;쿼리 매개 변수를 가진 도메인 다음에 URL 경로를 정의할 수 있습니다. 자세한 내용은 [Apple Universal Link 및 Android 앱 링크를 참조하십시오](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. Click **[!UICONTROL Edit Deep Link Interstitial]** and configure the link.

   (**Optional**) When there are multiple destinations, users can be routed depending on whether they have a mobile app installed. 앱이 설치되어 있는 경우 삽입 광고 랜딩 페이지가 표시됩니다.

   자세한 내용은 [중간 광고](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md).

1. **[!UICONTROL 저장을]** ****&#x200B;클릭하고 다음을 클릭합니다.
1. 대상 페이지에서 링크를 구성합니다.

   1. **[!UICONTROL 의사 결정]** 아이콘 (![결정 아이콘](assets/icon_decision.png)) 를 클릭하고 다음 의사 결정 위치 중 하나를 선택합니다.

      * **[!UICONTROL 결정 추가]**
      * **[!UICONTROL 경로 추가]**
   1. If you selected **[!UICONTROL Add Decision]**, select one of the following decision types:

      * **[!UICONTROL 운영 결정]**

         지원되는 운영 체제는 iOS, Android, AMX 등입니다.

      * **[!UICONTROL 장치 유형]**

         장치 유형에는 데스크톱, eReader, 게임 콘솔, 휴대 전화, 셋톱 박스 등과 같은 장치가 있습니다.
   1. **[!UICONTROL 대상]** 아이콘 ( ![사각형 아이콘](assets/icon_square.png) ) 를 클릭하고 다음 대상 유형 중 하나를 선택합니다.

      * **[!UICONTROL 앱스토어]**
      * **[!UICONTROL 웹 링크]**
      * **[!UICONTROL 앱 딥링크]**
      * **[!UICONTROL 하이브리드 링크]**
      >[!TIP]
      >
      >When you use the **[!UICONTROL Web Link]** destination type with a link to the app store, acquisition is not tracked. 획득을 추적하려면 **[!UICONTROL 앱스토어]대상 유형을 사용합니다.**

      자세한 내용은 새 링크 대상 [만들기를](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md)참조하십시오.




1. 마케팅 링크를 저장하려면 ![, e ipipses](assets/icon_elipses.png) 를 클릭한 다음 **[!UICONTROL 저장합니다]**.
