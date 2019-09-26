---
description: 다양한 변수 및 지표를 구성하여 앱에서 받은 데이터를 추적하고 관리할 수 있습니다.
keywords: mobile
seo-description: 다양한 변수 및 지표를 구성하여 앱에서 받은 데이터를 추적하고 관리할 수 있습니다.
seo-title: 앱 관리
solution: Marketing Cloud,Analytics
title: 앱 관리
topic: 지표
uuid: 0cc356c3-8457-40a7-8c97-7cbc68a5dc0c
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# 앱 관리 {#managing-your-app}

다양한 변수 및 지표를 구성하여 앱에서 받은 데이터를 추적하고 관리할 수 있습니다.

## 변수 및 지표 관리 {#section_EC2D58AC334F4ED49E764B81C2423A62}

* **표준 변수 및 지표**

   각 앱에는 장바구니 및 구매 활동을 추적하기 위한 변수와 지표가 포함되어 있습니다. Some purchase information cannot be handled with processing rules, so the SDK exposes the special `"&&products"` context data. 예를 들면, 카트 추가, 카트 제거, 체크아웃, 주문 등의 변수가 있을 수 있습니다. 컨텍스트 데이터는 Adobe Analytics의 데이터에 매핑해야 합니다. 이 변수가 컨텍스트 데이터의 간단한 매핑으로 채워지는 경우 컨텍스트 데이터는 변수를 매핑하는 키입니다. Analytics 관리 도구에서 더 복잡한 규칙으로 변수를 채우는 경우 비워 둡니다.

   이러한 변수 및 지표에 대한 자세한 내용은 다음을 참조하십시오.

   * [Product Variables in Android](/help/android/analytics-main/products/products.md)
   * [Product Variables in iOS](/help/ios/analytics-main/products/products.md)

* **사용자 지정 변수**

   사용자 지정 변수 페이지에는 앱 데이터를 포함하는 보고서 세트에 대해 구성된 모든 사용자 지정 Analytics 변수가 모두 표시됩니다. 이 페이지에서 추가적인 변수를 사용할 수 있도록 설정하고, 컨텍스트 데이터를 Analytics 변수에 매핑할 수 있습니다.

### 컨텍스트 데이터를 Analytics 변수에 매핑

Click **[!UICONTROL Manage App Settings]** &gt; **[!UICONTROL Manage Variables &amp; Metrics]** &gt; **[!UICONTROL Custom Variables]**.

These mappings call the same API that is used in [Processing Rules](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

![Context Data Mapping](assets/custom_data_content.png)

다음은 구성할 수 있는 사용자 지정 변수 목록입니다.

* The **[!UICONTROL Custom Properties]** (or props) answer the question "which one?" Prop은 동일한 히트로 전송된 다른 변수 및 지표와 연결될 텍스트 값으로 설정될 수 있습니다. 이 값은 보고서를 필터링하기 위해 사용되고 연결된 지표 순위에 표시될 수 있습니다.

   추적 호출에서 속성 값이 설정되면 이 값은 해당 호출(또는 히트)에만 적용됩니다.

* The **[!UICONTROL Custom Variables]** (or evars) also answer the question "which one?" 하지만 evar 값은 값이 만료되거나 새로운 값이 설정되기 전까지 전송된 히트만이 아니라 다음 히트에 전송되는 변수 및 지표에도 적용될 수 있습니다.
* The **[!UICONTROL Custom List Variables (or Multi-Value Variables)]** behave the same as variables except they allow you to capture multiple values on one hit. For more information, see List Variables.[](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/variables-analytics-reporting/page-variables.html)

다음 매핑은 Mobile Services에서 만들어지는 것으로 Analytics에 표시됩니다.

* **[!UICONTROL 이름]**

   데이터 컬렉션 변수의 친숙한 이름입니다.

* **[!UICONTROL 컨텍스트 데이터]**

   이 변수가 컨텍스트 데이터의 간단한 매핑으로 채워지는 경우 컨텍스트 데이터는 변수를 매핑하는 키입니다. 이 변수가 Analytics 관리 도구의 더 복잡한 규칙으로 채워지는 경우에는 이 필드를 비워 두십시오.

   컨텍스트 데이터 열을 클릭하고 매핑할 컨텍스트 데이터 변수를 선택합니다. 드롭다운 목록에는 과거 30일 동안 받은 변수가 들어 있으며, 매핑할 컨텍스트 데이터가 목록에 없으면 입력하면 됩니다.

* **[!UICONTROL Persistence (Custom Variables and Custom List Variables)]**

   지속성은 사용자 지정 변수(eVar) 값이 만료되거나 더 이상 추가 히트와 연결되지 않는 지점을 결정합니다. 히트가 실행될 때 eVar가 만료된 경우 없음 값이 해당 eVar에 대한 해당 히트과 연결됩니다. 즉, 히트가 실행되었을 때 eVar 값이 활성화되지 않았습니다.

   다음 옵션 중 하나를 선택할 수 있습니다.

   * **[!UICONTROL 세션]**

      eVar 값은 Analytics 방문 기간 동안 지속됩니다.

   * **[!UICONTROL 추적 호출]**

      eVar 값은 추적 호출 또는 포함된 히트에 대해서만 유지됩니다.

   * **[!UICONTROL 만료 기간 제한 없음]**

      eVar 값은 모든 후속 추적 호출에 대해 지속됩니다.
   * **[!UICONTROL Advanced]**

      Adobe Analytics에는 eVars의 지속성 설정에 대한 고급 UI가 있습니다. Mobile Services에서 지원되지 않는 eVar에 대해 지속성 값이 설정된 경우 이 값이 Mobile Services UI에 표시됩니다.

      To manage eVars, click **[!UICONTROL Adobe Analytics Report Suite Manager]** &gt; **[!UICONTROL Conversion Variables UI]**.

   * **[!UICONTROL 목록 지원]**

      하나의 추적 호출에서 속성과 연결할 여러 값을 전달할 수 있습니다. 구분 기호는 한 문자여야 하며 0이나 공백은 될 수 없습니다.

   * **[!UICONTROL 구분 기호]**

      구분 기호는 한 문자여야 하며 0이나 공백은 될 수 없습니다.

### 추가 Analytics 변수

각 변수 섹션의 맨 아래에서 드롭다운 목록을 사용하여 추가 변수를 사용하도록 설정할 수 있습니다.

![add a variable](assets/add_variable.png)

사용하지 않은 변수 번호를 선택하고 이름을 입력합니다. 저장하려는 컨텍스트 데이터 변수 및 추가 정보를 선택적으로 제공할 수 있습니다.

* **사용자 지정 지표**

   *Metrics (or events) answer the questions how much? or how many?*** 구문을 사용하는 키-값 쌍으로 전달됩니다. 이벤트는 사용자가 조치를 취하거나 가격과 같은 숫자 값을 보유할 때마다 증가할 수 있습니다. 사용자 지정 지표에는 앱이 생성됨, PDF 또는 CSV 파일이 다운로드되거나 내보내짐, 캠페인이 저장됨, SDK가 다운로드됨, 보고서가 실행됨, 앱스토어에 대한 링크가 추가됨, 인앱 메시지가 활성화됨 등의 이벤트가 포함되어 있습니다.

   Select one of the following custom metric types:

   * **[!UICONTROL 전체 번호]**
   * **[!UICONTROL 십진수]**
   * **[!UICONTROL 통화]**

## 관심 영역 관리{#section_990EF15E4E3B42CC807FCD9BEC8DB4C6}를 참조하십시오 

관심 영역을 사용하면 상관 관계 목적, 인앱 메시지로 타깃팅하는 등 사용할 수 있는 지리적 위치를 정의할 수 있습니다. 히트가 관심 영역에서 전송되는 경우 해당 관심 영역이 해당 히트에 연결됩니다. 관심 영역에 대한 자세한 내용은 [관심 영역 관리](/help/using/location/t-manage-points.md).

## 링크 대상 관리{#section_F722A387E22A430187B063D358A87711}를 참조하십시오 

링크 대상을 작성, 편집, 보관/보관 해제 및 삭제할 수 있습니다. These destinations can then be called inline when building Marketing Links, push notifications, or in-app messages. For more information about link destinations, see Manage Link Destinations.[](/help/using/acquisition-main/c-manage-link-destinations/t-archive-unarchive-link-destinations.md)

## 포스트백 관리 {#section_78B0A8D7AE6940E78D85AE3AB829E860}

포스트백을 이용하면 Adobe Mobile로 수집한 데이터를 별도의 타사 서버에 보낼 수 있습니다. 인앱 메시지를 표시하는 데 사용하는 것과 동일한 트리거와 트레이트를 이용하면 사용자 지정된 데이터를 타사 대상에 보내도록 Mobile을 구성할 수 있습니다. 포스트백에 대한 자세한 내용은 [포스트백 구성](/help/using/c-manage-app-settings/c-mob-confg-app/signals.md).
