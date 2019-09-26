---
description: 앱(앱 딥링크) 설치 여부에 따라 사용자를 대상(웹 사이트 또는 앱스토어)으로 안내할 수 있습니다.
keywords: mobile
seo-description: 앱(앱 딥링크) 설치 여부에 따라 사용자를 대상(웹 사이트 또는 앱스토어)으로 안내할 수 있습니다.
seo-title: 중간 광고
solution: Marketing Cloud,Analytics
title: 중간 광고
topic: 지표
uuid: 7dce8ab2-2a5d-4384-ac1e-e31dfaa3654
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# 중간 광고{#interstitials}

앱(앱 딥링크) 설치 여부에 따라 사용자를 대상(웹 사이트 또는 앱스토어)으로 안내할 수 있습니다. 라우팅은 사용자가 선택하는 것이 가장 좋습니다. 마케터는 사용 가능한 랜딩 대상을 사용자에게 표시하는 삽입 광고 페이지를 구성하여 사용자 선택을 제공할 수 있습니다.

새 마케팅 링크를 만들 때 creating a Marketing Link:

1. Click **[!UICONTROL Edit Deep Link Interstitial]**.

   ![딥 링크 삽입](assets/interstitial2.png)

1. 다음 필드에 정보를 입력하십시오.

   * **[!UICONTROL 사용자 지정 HTML]**

      사용자 지정 광고 삽입 HTML 페이지를 선택합니다.

      마케터는 맞춤형 인터페이스를 사용하여 페이지 브랜딩을 지원하는 맞춤형 HTML/CSS/JS를 사용하여 중간 랜딩 페이지를 사용자 정의할 수 있습니다.

      다음은 HTML 페이지에 대한 요구 사항입니다.

      * HTML 파일이어야 합니다.
      * Must contain the `%%DEST%%` and `%%FALLBACK%%` placeholders.
      * The uploaded HTML will be served in an `<iframe>`.

         링크 대상이 상위 창을 가리키는지 확인해야 합니다. You can include `<base target="_parent" />` in `<head>` or specify a target property for each `<a/>` individually.

         >[!TIP]
         >
         >사용자 지정 HTML을 업로드하는 경우 업로드된 파일을 제거하지 않는 한 이 표의 다른 네 가지 옵션이 사용되지 않습니다.
   * **[!UICONTROL 이미지 URL]**

      이미지 자산 URL을 지정합니다.

   * **[!UICONTROL 본문]**

      삽입 광고 본문을 지정합니다.

   * **[!UICONTROL 텍스트 확인]**

      텍스트 단추의 텍스트를 지정합니다.

   * **[!UICONTROL 대체 텍스트]**

      표시할 대체 텍스트를 지정합니다.

      딥링크가 실패하면 이 필드는 텍스트 단추를 업데이트합니다. 사용자는 다른 대체 옵션으로 이동하기 전에 먼저 딥링크 연결을 시도하도록 안내됩니다. 예를 들어, 앱을 다운로드하여 설치하는 앱스토어로 대체되거나 사용자를 회사 웹사이트로 이동할 수 있습니다. 대체 텍스트를 사용하면 사용자가 딥링크 연결에 실패하는 경우 사용할 수 있는 다른 옵션이 있음을 알 수 있습니다.


1. (**Optional**) Click the icons above the image to see how the interstitial looks rotated and on different devices.

   이미지가 다른 상황에서 제대로 표시되는지 확인하기 위해 Mobile Services 밖에서 이미지를 변경하거나 편집할 수 있습니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
