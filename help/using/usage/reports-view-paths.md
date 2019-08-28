---
description: 경로 분석을 기반으로 하는 경로 보기 보고서는 앱의 상태 간에 이동된 경로를 나타내는 경로 지정 차트를 표시합니다.
keywords: mobile
seo-description: 경로 분석을 기반으로 하는 경로 보기 보고서는 앱의 상태 간에 이동된 경로를 나타내는 경로 지정 차트를 표시합니다.
seo-title: 경로 보고서 보기
solution: Marketing Cloud, Analytics
title: 경로 보고서 보기
topic: 보고서,지표
uuid: BC 73 EDCE -0 CC 0-4349-9 A 48-E 0 A 40 CBE 1 B 67
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# 경로 보고서 보기 {#view-paths}

경로 분석을 기반으로 하는 **[!UICONTROL 경로 보기]보고서는 앱의 상태 간에 이동된 경로를 나타내는 경로 지정 차트를 표시합니다.**

>[!TIP]
>
>The **[!UICONTROL View Paths]** and **[!UICONTROL View Action]** reports are similar because both are pathing reports. **[!UICONTROL 경로 보기]보고서를 사용하면 사용자가 앱의 한 화면에서 다음 화면으로 이동하는 방식을 알 수 있습니다.** **[!UICONTROL 작업 보기]보고서는 사용자가 앱에서 수행하는 클릭, 선택, 크기 조정 등과 같은 작업 및 이벤트 순서를 표시합니다.** 단계 보고서를 사용하여 한 보고서의 탐색 및 작업을 결합할 수 있습니다. 자세한 내용은 [깔때기를 참조하십시오.](/help/using/usage/reports-funnel.md)

![경로 보기](assets/view_paths.png)

상자 모양의 각 노드는 앱에서 사용자 경로에 있는 상태를 나타냅니다. 예를 들어, 위의 그림에서 맨 위의 노드는 앱을 시작한 다음, 기본 보기로 이동한 사용자의 수를 나타냅니다.

노드를 클릭하여 차트를 수정할 수 있는 추가 옵션을 제공하면 **[!UICONTROL 포커스]** 또는 **확장]과 같은 추가 옵션이 표시됩니다.[!UICONTROL ** 예를 들어, 맨 위 노드에서 **[!UICONTROL 기본 보기]** 상태를 클릭하면, **[!UICONTROL 포커스]및**&#x200B;확장] 아이콘이 표시됩니다.**[!UICONTROL **

To expand the view, click the **[!UICONTROL +]** icon to display the additional paths that come in to or go from the node. 아래 그림에서 상태 1은 앱을 실행하고, 상태 2는 앱의 기본 페이지를 표시하고, 상태 3에는 사용자가 수행한 다음 경로가 포함되어 있음을 나타냅니다.

* 카메라 롤로 이동
* 항목 선택기로 이동
* 카메라로 이동
* 항목 정보 페이지로 이동

![](assets/view_paths_expand.png)

![포커스 아이콘을](assets/icon_focus.png) 클릭하여 노드를 분리하고 선택한 노드에서 들어오고 나가는 경로를 표시합니다. 아래 그림에서 다음 경로는 앱의 기본 보기를 보고 있는 사용자보다 먼저 발생했습니다.

* 항목 정보
* 항목 선택기
* 카메라 롤
* 카메라

![경로 포커스 보기](assets/view_paths_focus.png)

여러 노드에 초점을 맞추거나 확장하여 앱에서 사용자가 선택하는 경로를 자세히 볼 수 있습니다. 예:

![View Path Multi](assets/view_paths_mult.png)

이 보고서에 대해 다음 옵션을 구성할 수 있습니다.

* **[!UICONTROL 기간]**
 **[!UICONTROL 달력]** 아이콘을 클릭하여 사용자 지정 기간을 선택하거나 드롭다운 목록에서 사전 설정 기간을 선택합니다.
* **[!UICONTROL 표시]**&#x200B;방법 옵션별 **[!UICONTROL 표시, 지표 및 필터 추가,]** 추가 시리즈 (지표) 추가 등의 방법으로 보고서를 사용자 정의합니다. For more information, see [Customize Reports](/help/using/usage/reports-customize/reports-customize.md).
* **[!UICONTROL 필터]**
필터를 클릭하여 **[!UICONTROL 여러]** 보고서에 걸친 필터를 만들어 모든 모바일 보고서에서 세그먼트가 수행되는 방식을 확인합니다. 고정 필터를 사용하면 경로 지정 외의 모든 보고서에 적용되는 필터를 정의할 수 있습니다. 자세한 내용은 고정 필터 [추가를](/help/using/usage/reports-customize/t-sticky-filter.md)참조하십시오.
* **[!UICONTROL 다운로드]**
 **[!UICONTROL PDF]** 또는 **[!UICONTROL CSV]** 를 클릭하여 문서를 다운로드하거나 열거나 Mobile Services에 액세스할 수 없는 사용자와 공유하거나 프레젠테이션에 파일을 사용할 수 있습니다.