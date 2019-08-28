---
description: 범용 링크 (iOS) 및 앱 링크 (Android) 를 사용하면 iOS 또는 Android 앱의 딥 링크에 연결할 수 있습니다.
keywords: mobile
seo-description: 범용 링크 (iOS) 및 앱 링크 (Android) 를 사용하면 iOS 또는 Android 앱의 딥 링크에 연결할 수 있습니다.
seo-title: Apple Universal Link 및 Android 앱 링크
solution: Marketing Cloud, Analytics
title: Apple Universal Link 및 Android 앱 링크
topic: 지표
uuid: 8 D 6441 DC -4307-4454-95 EA-D 77 EC 796 F 918
translation-type: tm+mt
source-git-commit: e65add089499f728827321e96e439f04ebb19a73

---


# Apple Universal Link 및 Android 앱 링크{#universal-links-and-app-links}

범용 링크 (iOS) 및 앱 링크 (Android) 를 사용하면 iOS 또는 Android 앱의 딥 링크에 연결할 수 있습니다.

>[!IMPORTANT]
>
>iOS 9.2 부터는 딥 링크가 지원되지 않습니다. 앱 또는 웹 사이트에 연결하려면 Apple Universal Link를 사용해야 합니다.

## 범용 링크 {#section_F8147944679A42E59CF4FD8814E5EF12}

범용 링크를 사용하면 iOS 앱의 딥 링크에 연결할 수 있으며 iOS 9.2 이상에서 지원됩니다. 유니버설 링크가 액세스되면 iOS가 앱의 딥 링크로 바로 링크를 리디렉션합니다. 앱이 설치되어 있지 않으면 브라우저에서 웹 사이트에 대한 URL 이 열립니다. 범용 링크에 대한 자세한 내용은 범용 링크 [지원을](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html)참조하십시오.

## 앱 링크

앱 링크를 사용하면 Android 앱의 딥 링크에 연결할 수 있으며 Android 6.0 이상에서 지원됩니다. 앱 링크가 액세스되면 Android는 앱의 딥 링크로 링크를 리디렉션합니다. 앱이 설치되어 있지 않으면 브라우저에서 웹 사이트에 대한 URL 이 열립니다. For more information about App Links, see the [Handling Android App Links](https://developer.android.com/training/app-links/index.html).

## 범용 또는 앱 링크를 사용하여 마케팅 링크 만들기 {#section_609ADEFFB9B441C4A8C45E936D0DC859}

범용 또는 앱 링크를 사용하는 마케팅 링크를 만들 수 있습니다.

### Universal Link 구성

1. iOS 앱에서 범용 링크를 설정하려면 Apple의 범용 링크 [처리 이동하십시오](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links).

2. Adobe Mobile Services에서 사이트 연결 문서를 설정합니다.

   a. Mobile Services 홈 페이지에서 범용 링크를 설정할 앱을 선택합니다.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. 범용 링크를 처리하는 iOS 앱이 앱 스토어 앱 **[!UICONTROL 추가]** 섹션에 추가됩니다.

   >[!TIP]
   >
   >앱스토어 앱 **[!UICONTROL 추가]** 섹션이 표시되지 않으면 앱스토어 앱 **[!UICONTROL 추가]** 링크를 클릭합니다.

   d. **[!UICONTROL [유니버설 링크 및 앱 링크 옵션]]** 섹션에서 iOS 앱을 선택하고 앱 ID를 입력합니다.

   f. ****&#x200B;저장을 클릭합니다.

   하나 이상의 iOS 앱 선택 및 하나의 앱 ID를 제공해야 하며, 그렇지 않으면 오류가 표시됩니다.

   >[!IMPORTANT]
   >
   >범용 링크 및 앱 링크 옵션 섹션에서 업데이트를 클릭하여 문서를 업데이트할 수 있습니다. However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### 범용 링크 사용

1. Adobe Mobile Services에서 범용 링크를 사용하는 마케팅 링크를 만듭니다.

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. 새로 **[!UICONTROL 만들기를]**&#x200B;클릭합니다.

   c. Under **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Use Universal Links or App Links]**.

   d. 위의 Adobe Mobile Services에서 사이트 연결 문서 *설정 섹션에 사이트 연결 문서를 구성한 경우 이* 옵션이 기본적으로 선택되어 있습니다.

   문서를 구성하지 않은 경우 [유니버설 링크 사용] 또는 [앱 링크 **[!UICONTROL 사용]** ] 옵션이 비활성화되고 **[!UICONTROL 기본적으로 [대화형]]** 사용이 선택됩니다.

   e. [유니버설 링크 또는 앱 링크 **[!UICONTROL 사용]]** 옵션을 선택하면 **[!UICONTROL [사용자 정의 경로]** ] 필드가 표시됩니다.

   이 경우 사용자가 쿼리 매개 변수와 함께 도메인 뒤에 URL 경로를 정의할 수 있습니다. 예를 들어, `my/universal/link?os=9.2`이면 전체 마케팅 링크 URL `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`이 됩니다.

   f. **[!UICONTROL 의사 결정]** 탭을 클릭하고 의사 결정 트리를 구성합니다.

   h. iOS 앱이 설치된 경우 앱은 로직과 함께 딥 링크를 처리합니다. 최종 대상은 앱이 설치되지 않은 경우 폴백으로만 제공됩니다. 앱이 설치되어 있지 않으므로 최종 대상은 웹 링크 또는 앱스토어여야 합니다.

   i. ****&#x200B;저장을 클릭합니다.

>[!TIP]
>
>마케팅 링크가 저장되면 마케팅 링크 옵션을 변경할 수 없습니다. 이것은 이미 배포된 마케팅 링크의 동작을 변경하지 않으려는 것이기 때문입니다.


### 앱 링크 구성

1. Android 앱에서 앱 링크를 설정하려면 Android 앱 링크 [추가를](https://developer.android.com/studio/write/app-link-indexing)참조하십시오.

1. Adobe Mobile Services에서 사이트 연결 문서를 설정합니다.

   a. Mobile Services 홈 페이지에서 앱 링크를 설정할 앱을 선택합니다.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. 범용 링크 또는 앱 링크를 처리하는 Android 앱이 앱 스토어 앱 **[!UICONTROL 추가]** 섹션에 추가됩니다.

   >[!TIP]
   >
   >If this section does not display, click the **[!UICONTROL Add App Store App]** link.

   d. **[!UICONTROL 범용 링크 및 앱 링크 옵션]** 섹션으로 스크롤합니다.

   e. **[!UICONTROL 앱 링크 (Android)]** 탭을 클릭합니다.

   f. Android 앱을 선택하고 SHA -256 인증서 지문을 입력합니다.

   g. ****&#x200B;저장을 클릭합니다.

   하나 이상의 Android 앱 선택 및 SHA -256 인증서를 제공해야 합니다. 그렇지 않으면 오류가 표시됩니다.

   >[!IMPORTANT]
   >
   >**[!UICONTROL 범용 링크 및 앱 링크 옵션]섹션에서****업데이트[!UICONTROL 를 클릭하여 문서를 업데이트할 수 있습니다.]** However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### 앱 링크 사용

1. Adobe Mobile Services에서 앱 링크를 사용하는 마케팅 링크를 만듭니다.

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. 새로 **[!UICONTROL 만들기를]**&#x200B;클릭합니다.

   c. **[!UICONTROL 마케팅 링크 옵션]** 섹션에서 범용 링크 또는 앱 링크 **[!UICONTROL 사용을]**&#x200B;선택합니다.

   d. 2 단계에서 사이트 연결 문서를 구성한 경우 이 옵션은 기본적으로 선택되어 있습니다.

   If not, the **[!UICONTROL Use Universal Links or App Links]** option is disabled, and **[!UICONTROL Use Interstitials]** is selected by default.

   e. [유니버설 링크 ** 또는 [앱 링크]** 사용] 를 선택한 경우 [ **[!UICONTROL 사용자 정의 경로]** ] 필드가 표시됩니다.

   이 경우 사용자가 쿼리 매개 변수와 함께 도메인 뒤에 URL 경로를 정의할 수 있습니다. 예를 들어, `my/app/link?os=6.0`이면 전체 마케팅 링크 URL `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`이 됩니다.

   f. **[!UICONTROL 의사 결정]** 탭을 클릭하고 의사 결정 트리를 구성합니다.

   g. Android 앱이 설치된 경우 앱은 해당 로직으로 딥 링크를 처리합니다.

   최종 대상은 앱이 설치되지 않은 경우에만 대비책으로 사용됩니다. 앱이 설치되어 있지 않으므로 최종 대상은 웹 링크 또는 앱스토어여야 합니다.

   h.  ****&#x200B;저장을 클릭합니다.

>[!TIP]
>
>After a Marketing Link is saved, the **[!UICONTROL Marketing Links Options]** cannot be altered. 이것은 이미 배포된 마케팅 링크의 동작을 변경하지 않으려는 것이기 때문입니다.

## 마케팅 링크 사용

이제 앱의 메시징 및 기타 영역에서 이러한 마케팅 링크를 사용할 수 있습니다.

>[!IMPORTANT]
>
>범용 링크 또는 앱 링크가 있는 클릭 추적 횟수는 표시되지 않으며, 상호 작용을 사용할 수도 없습니다.

