---
description: Acquisition tracking must be enabled in the SDK configuration before you can track and report on Marketing Links.
keywords: mobile
seo-description: Acquisition tracking must be enabled in the SDK configuration before you can track and report on Marketing Links.
seo-title: 획득 구성
solution: Marketing Cloud,Analytics
title: 획득 구성
topic: 지표
uuid: e996e43e-8a77-47a3-a6fb-53f676f92bef
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# 획득 구성{#configure-acquisition}을 참조하십시오 

Acquisition tracking must be enabled in the SDK configuration before you can track and report on Marketing Links.

1. 앱에 대한 앱 설정 관리 페이지에서 **[!UICONTROL SDK 획득 옵션]** 섹션으로 스크롤합니다.
1. 다음 작업을 완료하십시오.

   * To enable Acquisition, select the **[!UICONTROL Enable]** check box.

      When you select this check box, the **[!UICONTROL Referrer Timeout]** field becomes active, and the value changes from 0 to 5.

   * 레퍼러 시간 초과( **[!UICONTROL 초)]** 필드에 값을 입력합니다.

      (**Optional**) If you enabled the **[!UICONTROL Enable]** check box, this field is optional. 초로 지정된 시간 초과 값을 변경할 수 있습니다. 이 설정은 첫 번째 시작 히트를 보내기 전에 획득 정보를 기다리는 기간을 지정합니다.
   >[!IMPORTANT]
   >0이 아닌 값을 입력해야 합니다. 획득을 활성화하지만 값을 0으로 두면 획득 링크가 작동하지 않습니다. 5초 기본값을 사용하는 것이 좋습니다.

1. 새로운 SDK 구성 파일을 다운로드하여 앱에서 사용합니다.

   **iOS**에 대한 획득을 성공적으로 구성했습니다.
To enable Acquisition on **Android**, complete the steps in [Tracking Mobile Acquisition](/help/android/acquisition-main/acquisition.md).
