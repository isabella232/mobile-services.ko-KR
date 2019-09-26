---
description: '상관 관계 목적으로 사용하고, 인앱 메시지로 타깃팅하는 등의 작업을 수행할 수 있는 지리적 위치를 정의할 수 있는 관심 영역을 만들고 관리할 수 있습니다. 히트가 관심 영역에서 전송되는 경우 해당 관심 영역이 해당 히트에 연결됩니다. '
keywords: mobile
seo-description: '상관 관계 목적으로 사용하고, 인앱 메시지로 타깃팅하는 등의 작업을 수행할 수 있는 지리적 위치를 정의할 수 있는 관심 영역을 만들고 관리할 수 있습니다. 히트가 관심 영역에서 전송되는 경우 해당 관심 영역이 해당 히트에 연결됩니다. '
seo-title: 관심 영역 관리
solution: Marketing Cloud,Analytics
title: 관심 영역 관리
topic: 지표
uuid: 7b362534-54fb-43a3-b6b2-dfc8f45ff7c6
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Manage points of interest {#manage-points-of-interest}

You can create and manage POIs, which allow you to define geographical locations that you can use for correlation purposes, target with in-app messages, and so on. POI에서 히트가 전송되면 POI가 히트에 연결됩니다.

위치를 사용하려면 먼저 다음 요구 사항을 확인하십시오.

* Analytics—Mobile Apps 또는 Analytics Premium이 있어야 합니다.
* 앱에 대해 **[!UICONTROL 위치 보고서]를 활성화해야 합니다.**
* If you are using a version of the iOS SDK or Android SDK older than version 4.2, after adding new **[!UICONTROL Points of Interest]**, you must download a new configuration file and give it to your app developers.

   If you are using the iOS SDK or Android SDK version 4.2 or later, you do not need to submit an app update to the store to update your **[!UICONTROL Points of Interest]**. [관심 영역 관리] 페이지에서 [ **[!UICONTROL 저장]**]을 클릭하면 변경 내용이 관심 영역 **[!UICONTROL 목록에]** 패키지되고 라이브 앱에 대한 구성 파일이 업데이트됩니다. 앱이 원격 POI URL과 함께 업데이트된 SDK와 구성을 사용하는 한, 저장을 하면 사용자 디바이스에서 앱의 포인트 목록도 업데이트됩니다.

On the user's device, for a hit to be assigned to a **[!UICONTROL Points of Interest]**, location must be enabled for the app.

위치를 사용하려면 다음 작업을 완료하십시오.

1. 앱 이름을 클릭하여 해당 앱 설정 관리 페이지로 이동합니다.
1. Click **[!UICONTROL Location]** &gt; **[!UICONTROL Manage Points of Interest]**.

   ![단계 결과](assets/poi.png)

1. 다음 각 필드에 정보를 입력합니다.

   * **[!UICONTROL 지점 이름]**

      **[!UICONTROL 지점]이름을 입력합니다.**

      이 이름은 도시, 국가 또는 지역일 수 있습니다. 경기장이나 사업체와 같은 특정 위치 주변에 **[!UICONTROL 지점]을 만들 수도 있습니다.**

   * **[!UICONTROL 위도]**

      **[!UICONTROL 지점의 위도를 입력합니다]**. 이 정보는 인터넷을 포함한 다른 소스에서 찾을 수 있습니다.

   * **[!UICONTROL 경도]**

      **[!UICONTROL 지점의 경도를 입력합니다]**. 이 정보는 인터넷을 포함한 다른 소스에서 찾을 수 있습니다.

   * **[!UICONTROL 반경(미터)]**

      포함할 **[!UICONTROL 지점]주변 반경(미터 단위)을 입력합니다.** 예를 들어, Colorado의 Denver용 POI를 만드는 경우, Denver 시와 주변 영역을 포함할 만큼 큰 반경을 지정할 수 있지만 Colorado Springs는 제외할 수 있습니다.

   * **[!UICONTROL 맵 아이콘]**

      개요 및 맵 보고서에 표시할 [아이콘을](/help/using/location/c-location-overview.md) [선택합니다](/help/using/location/c-map-points.md) .

1. 필요에 따라 POI를 더 추가합니다.

   5,000개 이하의 POI를 추가하는 것이 좋습니다. 5,000개 이상을 추가하는 경우, 지점을 저장할 수는 있지만, 우수 사례에 5,000개 이하의 영역을 추가하라고 언급되어 있다는 경고 메시지가 표시됩니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

To delete one or more POIs, select the applicable check boxes, and click **[!UICONTROL Remove Selected]**.

Click **[!UICONTROL Import]** or **[!UICONTROL Export]** to work with the data by using a `.csv` file instead of using the Adobe Mobile user interface.
