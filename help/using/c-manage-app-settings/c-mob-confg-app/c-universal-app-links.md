---
description: 범용 링크(iOS) 및 앱 링크(Android)를 사용하면 iOS 또는 Android 앱의 딥 링크에 연결할 수 있습니다.
keywords: mobile
seo-description: Universal Links (iOS) and App Links (Android) allow you to connect to deep links in your iOS or Android apps.
seo-title: Apple Universal Links and Android App Links
solution: Marketing Cloud,Analytics
title: Apple Universal Links and Android App Links
topic: 지표
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
translation-type: tm+mt
source-git-commit: e65add089499f728827321e96e439f04ebb19a73

---


# Apple Universal Links and Android App Links{#universal-links-and-app-links}

Universal Links (iOS) and App Links (Android) allow you to connect to deep links in your iOS or Android apps.

>[!IMPORTANT]
>
>iOS 9.2부터 딥 링크는 지원되지 않습니다. 앱 또는 웹 사이트에 대한 딥 링크 연결을 위해서는 Apple 범용 링크를 사용해야 합니다.

## 범용 링크 {#section_F8147944679A42E59CF4FD8814E5EF12}

범용 링크를 사용하면 iOS 앱의 딥 링크에 연결할 수 있으며 iOS 9.2 이상에서 지원됩니다. Universal Link에 액세스하면 iOS에서 링크를 앱의 딥 링크로 직접 리디렉션합니다. If your app is not installed, it opens a URL for your website in a browser instead. 범용 링크에 대한 자세한 내용은 범용 링크 [지원을 참조하십시오](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html).

## 앱 링크

앱 링크를 사용하면 Android 앱의 딥 링크에 연결할 수 있으며 Android 6.0 이상에서 지원됩니다. 앱 링크에 액세스하면 Android가 해당 링크를 앱의 딥 링크로 직접 리디렉션합니다. If your app is not installed, it opens a URL for your website in a browser instead. For more information about App Links, see the [Handling Android App Links](https://developer.android.com/training/app-links/index.html).

## 범용 또는 앱 링크를 사용하여 마케팅 링크 만들기 {#section_609ADEFFB9B441C4A8C45E936D0DC859}

범용 또는 앱 링크를 사용하는 마케팅 링크를 만들 수 있습니다.

### 범용 링크 구성

1. iOS 앱에서 범용 링크를 설정하려면 Apple의 범용 [링크 처리로 이동합니다](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links).

2. Adobe Mobile Services에서 사이트 연결 문서를 설정합니다.

   a.Mobile Services 홈 페이지에서 범용 링크를 설정할 앱을 선택합니다.

   b. Click **[!UICONTROL Manage App Settings]**.

   c.범용 링크를 처리하는 iOS 앱이 앱스토어 앱 추가 **[!UICONTROL 섹션에 추가되어 있는지]** 확인합니다.

   >[!TIP]
   >
   >앱스토어 앱 **[!UICONTROL 추가]** 섹션이 표시되지 않으면 앱스토어 앱 **[!UICONTROL 추가 링크를]** 클릭합니다.

   d.범용 링크 **[!UICONTROL 및 앱 링크 옵션]** 섹션에서 iOS 앱을 선택하고 앱 ID를 입력합니다.

   f.저장을 **[!UICONTROL 클릭합니다]**.

   하나 이상의 iOS 앱 선택 및 하나의 앱 ID를 제공해야 합니다. 그렇지 않으면 오류가 표시됩니다.

   >[!IMPORTANT]
   >
   >범용 링크 및 앱 링크 옵션 섹션에서 업데이트를 클릭하여 문서를 업데이트할 수 있습니다. However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### 범용 링크 사용

1. In Adobe Mobile Services, create a Marketing Link that uses Universal Links:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b.새로 **[!UICONTROL 만들기를 클릭합니다]**.

   c. Under **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Use Universal Links or App Links]**.

   d. If you configured the site-association documents in the Setting up site-association documents in Adobe Mobile Services section above, this option is selected by default.**

   If you did not configure the documents, the Use Universal Links or App Links option is disabled and Use Interstitials is selected by default.********

   e.범용 링크 **[!UICONTROL 또는 앱 링크]** 사용 옵션을 선택하면 사용자 **[!UICONTROL 지정 경로]** 필드가 표시됩니다.

   이 경우 사용자가 쿼리 매개 변수와 함께 도메인 뒤에 URL 경로를 정의할 수 있습니다. 예를 들어, , your full Marketing Link URL becomes .`my/universal/link?os=9.2``https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`

   f.결정 **[!UICONTROL 탭을]** 클릭하고 결정 트리를 구성합니다.

   h. If the iOS app is installed, the app handles the deeplink with its logic. 최종 대상은 앱이 설치되지 않은 경우 폴백으로만 사용됩니다. 앱이 설치되지 않았으므로 최종 대상은 웹 링크 또는 앱스토어일 수 있습니다.

   i.저장을 **[!UICONTROL 클릭합니다]**.

>[!TIP]
>
>마케팅 링크가 저장되면 마케팅 링크 옵션을 변경할 수 없습니다. This is because you do not want to change the behavior of the Marketing Links that may have already been distributed.


### 앱 링크 구성

1. Android 앱에서 앱 링크를 설정하려면 Android 앱 링크 [추가로 이동합니다](https://developer.android.com/studio/write/app-link-indexing).

1. Adobe Mobile Services에서 사이트 연결 문서를 설정합니다.

   a.Mobile Services 홈 페이지에서 앱 링크를 설정할 앱을 선택합니다.

   b. Click **[!UICONTROL Manage App Settings]**.

   c.범용 링크 또는 앱 링크를 처리하는 Android 앱이 앱스토어 앱 **[!UICONTROL 추가 섹션에 추가되어 있는지]** 확인합니다.

   >[!TIP]
   >
   >If this section does not display, click the **[!UICONTROL Add App Store App]** link.

   d.범용 링크 **[!UICONTROL 및 앱 링크 옵션 섹션으로]** 스크롤합니다.

   e. Click the App Links (Android) tab.****

   f. Select an Android app and type a SHA-256 certificate fingerprint.

   g.저장을 **[!UICONTROL 클릭합니다]**.

   하나 이상의 Android 앱 선택 및 SHA-256 인증서 하나를 제공해야 합니다. 그렇지 않으면 오류가 표시됩니다.

   >[!IMPORTANT]
   >
   >**[!UICONTROL 범용 링크 및 앱 링크 옵션]섹션에서****업데이트[!UICONTROL 를 클릭하여 문서를 업데이트할 수 있습니다.]** However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Use an App Link

1. Adobe Mobile Services에서 앱 링크를 사용하는 마케팅 링크를 만듭니다.

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Click Create New.****

   c. In the Marketing Link Options section, select Use Universal Links or App Links.********

   d. If you configured the site-association documents from step 2, this option is selected by default.

   If not, the **[!UICONTROL Use Universal Links or App Links]** option is disabled, and **[!UICONTROL Use Interstitials]** is selected by default.

   e. If Use Universal Links or App Links is selected, the Custom Path field is displayed.********

   이 경우 사용자가 쿼리 매개 변수와 함께 도메인 뒤에 URL 경로를 정의할 수 있습니다. 예를 들어, , your full Marketing Link URL becomes .`my/app/link?os=6.0``https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`

   f. Click the Decisions tab and configure your decision tree.****

   g.Android 앱이 설치되어 있는 경우 앱은 해당 논리로 정의를 처리합니다.

   최종 대상은 앱이 설치되지 않은 경우에 대한 대체 사례로만 사용됩니다. 앱이 설치되지 않았으므로 최종 대상은 웹 링크 또는 앱스토어일 수 있습니다.

   h. Click Save.****

>[!TIP]
>
>After a Marketing Link is saved, the **[!UICONTROL Marketing Links Options]** cannot be altered. 이는 이미 배포된 마케팅 링크의 동작을 변경하려는 것이 아니므로

## 마케팅 링크 사용

이제 메시징과 앱의 다른 영역에서 이러한 마케팅 링크를 사용할 수 있습니다.

>[!IMPORTANT]
>
>범용 링크 또는 앱 링크에서는 클릭 추적 카운트가 표시되지 않으며, 상호 작용을 사용할 수도 없습니다.

