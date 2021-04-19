---
description: 사용자 경험을 유지 관리하기 위해 앱 및 웹 사이트 내에서 연결하는 것이 중요합니다. 유니버설 및 앱 링크의 작동 방식과 차이점에 대해 알아봅니다.
seo-description: 범용 링크(iOS) 및 앱 링크(Android)를 사용하면 iOS 또는 Android 앱의 딥 링크에 연결할 수 있습니다.
seo-title: Apple 범용 링크 및 Android 앱 링크
solution: Experience Cloud,Analytics
title: 범용 링크 및 앱 링크 안내서
topic-fix: Metrics
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
exl-id: 6613189f-7a14-4066-89e9-996d4fe7f128
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 96%

---

# 범용 링크와 앱 링크 비교:어떻게 작동합니까?{#universal-links-and-app-links}

범용 링크(iOS) 및 앱 링크(Android)를 사용하면 iOS 또는 Android 앱의 딥 링크에 연결할 수 있습니다.

>[!IMPORTANT]
>
>iOS 9.2부터 딥 링크가 지원되지 않습니다. 앱 또는 웹 사이트에 대한 딥 링크에는 Apple 범용 링크를 사용해야 합니다.

## 범용 링크 {#section_F8147944679A42E59CF4FD8814E5EF12}

범용 링크를 사용하면 iOS 앱의 딥 링크에 연결할 수 있으며, iOS 9.2 이상에서 지원됩니다. 범용 링크에 액세스하면 iOS에서 링크를 앱의 딥 링크에 직접 리디렉션합니다. 앱이 설치되지 않은 경우 브라우저에서 웹 사이트의 URL이 대신 열립니다. 범용 링크에 대한 자세한 내용은 [범용 링크 지원](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html)을 참조하십시오.

## 앱 링크

앱 링크를 사용하면 Android 앱의 딥 링크에 연결할 수 있으며, Android 6.0 이상에서 지원됩니다. 앱 링크에 액세스하면 Android에서 링크를 앱의 딥 링크에 직접 리디렉션합니다. 앱이 설치되지 않은 경우 브라우저에서 웹 사이트의 URL이 대신 열립니다. 앱 링크에 대한 자세한 내용은 [Android 앱 링크 처리](https://developer.android.com/training/app-links/index.html)를 참조하십시오.

## 범용 또는 앱 링크를 사용하여 마케팅 링크 만들기 {#section_609ADEFFB9B441C4A8C45E936D0DC859}

범용 또는 앱 링크를 사용하는 마케팅 링크를 만들 수 있습니다.

### 범용 링크 구성

1. iOS 앱에서 범용 링크를 설정하려면 [Apple의 범용 링크 처리](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links)로 이동합니다.

2. Adobe Mobile Services에서 사이트 연결 문서를 설정합니다.

   a. Mobile Services 홈 페이지에서 범용 링크를 설정할 앱을 선택합니다.

   b. **[!UICONTROL 앱 설정 관리]**&#x200B;를 클릭합니다.

   c. 범용 링크를 처리하는 iOS 앱이 **[!UICONTROL 앱스토어 앱 추가]** 섹션에 추가되어 있는지 확인합니다.

   >[!TIP]
   >
   >**[!UICONTROL 앱스토어 앱 추가]** 섹션이 표시되지 않으면 **[!UICONTROL 앱스토어 앱 추가]** 링크를 클릭합니다.

   d. **[!UICONTROL 범용 링크 및 앱 링크 옵션]** 섹션에서 iOS 앱을 선택하고 앱 ID를 입력합니다.

   f. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   하나 이상의 iOS 앱과 하나의 앱 ID를 선택해야 합니다. 선택하지 않으면 오류가 표시됩니다.

   >[!IMPORTANT]
   >
   >범용 링크 및 앱 링크 옵션 섹션에서 업데이트를 클릭하여 문서를 업데이트할 수 있습니다. 그러나 **[!UICONTROL 업데이트]**&#x200B;를 클릭하면 이전에 만든 모든 범용 링크 또는 앱 링크가 영향을 받는다는 경고가 표시됩니다.

### 범용 링크 사용

1. Adobe Mobile Services에서 범용 링크를 사용하는 마케팅 링크를 만듭니다.

   a. 모바일 서비스 홈 페이지에서 앱을 선택하고 **[!UICONTROL 획득]** > **[!UICONTROL 마케팅 링크 빌더]**&#x200B;를 클릭합니다.

   b. **[!UICONTROL 새로 만들기]**&#x200B;를 클릭합니다.

   c. **[!UICONTROL 마케팅 링크 옵션]**&#x200B;에서 **[!UICONTROL 범용 링크 또는 앱 링크 사용]**&#x200B;을 선택합니다.

   d. 위의 *Adobe Mobile Services에서 사이트 연결 문서 설정* 섹션에서 사이트 연결 문서를 구성한 경우 이 옵션이 기본적으로 선택됩니다.

   이 문서를 구성하지 않은 경우 **[!UICONTROL 범용 링크 또는 앱 링크 사용]** 옵션이 비활성화되고, **[!UICONTROL 삽입 광고 사용]**&#x200B;이 기본적으로 선택됩니다.

   e. **[!UICONTROL 범용 링크 또는 앱 링크 사용]** 옵션을 선택하면 **[!UICONTROL 사용자 지정 경로]** 필드가 표시됩니다.

   이를 통해 사용자는 쿼리 매개 변수를 사용하여 도메인 뒤에 URL 경로를 정의할 수 있습니다. 예를 들어, `my/universal/link?os=9.2` 입력 시, 전체 마케팅 링크 URL은 `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`입니다.

   f. **[!UICONTROL 결정]** 탭을 클릭하고 결정 트리를 구성합니다.

   h. iOS 앱이 설치되어 있는 경우 앱이 해당 논리로 딥링크를 처리합니다. 최종 대상은 앱이 설치되지 않은 경우에만 대체 역할을 합니다. 앱이 설치되지 않았으므로 최종 대상은 웹 링크 또는 앱스토어일 수 있습니다.

   i. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

>[!TIP]
>
>마케팅 링크가 저장되면 마케팅 링크 옵션을 변경할 수 없습니다. 이미 배포되었을 수도 있는 마케팅 링크의 동작을 변경하고 싶지 않기 때문입니다.


### 앱 링크 구성

1. Android 앱에서 앱 링크를 설정하려면 [Android 앱 링크 추가](https://developer.android.com/studio/write/app-link-indexing)로 이동합니다.

1. Adobe Mobile Services에서 사이트 연결 문서를 설정합니다.

   a. Mobile Services 홈 페이지에서 앱 링크를 설정할 앱을 선택합니다.

   b. **[!UICONTROL 앱 설정 관리]**&#x200B;를 클릭합니다.

   c. 범용 링크를 처리하는 Android 앱이 **[!UICONTROL 앱스토어 앱 추가]** 섹션에 추가되어 있는지 확인합니다.

   >[!TIP]
   >
   >이 섹션이 표시되지 않으면 **[!UICONTROL 앱스토어 앱 추가]** 링크를 클릭합니다.

   d. **[!UICONTROL 범용 링크 및 앱 링크 옵션]** 섹션으로 스크롤합니다.

   e. **[!UICONTROL 앱 링크(Android)]** 탭을 클릭합니다.

   f. Android 앱을 선택하고 SHA-256 인증서 지문을 입력합니다.

   g.**[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   하나 이상의 Android 앱과 하나의 SHA-256 인증서를 선택해야 합니다. 선택하지 않으면 오류가 표시됩니다.

   >[!IMPORTANT]
   >
   >**[!UICONTROL 범용 링크 및 앱 링크 옵션]** 섹션에서 **[!UICONTROL 업데이트를 클릭하여 문서를 업데이트할 수 있습니다.]** 그러나 **[!UICONTROL 업데이트]**&#x200B;를 클릭하면 이전에 만든 모든 범용 링크 또는 앱 링크가 영향을 받는다는 경고가 표시됩니다.

### 앱 링크 사용

1. Adobe Mobile Services에서 앱 링크를 사용하는 마케팅 링크를 만듭니다.

   a. 모바일 서비스 홈 페이지에서 앱을 선택하고 **[!UICONTROL 획득]** > **[!UICONTROL 마케팅 링크 빌더]**&#x200B;를 클릭합니다.

   b. **[!UICONTROL 새로 만들기]**&#x200B;를 클릭합니다.

   c. **[!UICONTROL 마케팅 링크 옵션]** 섹션에서 **[!UICONTROL 범용 링크 또는 앱 링크 사용]**&#x200B;을 선택합니다.

   d. 2단계에서 사이트 연결 문서를 구성한 경우 이 옵션이 기본적으로 선택됩니다.

   구성하지 않은 경우 **[!UICONTROL 범용 링크 또는 앱 링크 사용]** 옵션이 비활성화되고 **[!UICONTROL 삽입 광고 사용]**&#x200B;이 기본적으로 선택됩니다.

   e. **[!UICONTROL 범용 링크 또는 앱 링크 사용]**&#x200B;을 선택하면 **[!UICONTROL 사용자 지정 경로]** 필드가 표시됩니다.

   이를 통해 사용자는 쿼리 매개 변수를 사용하여 도메인 뒤에 URL 경로를 정의할 수 있습니다. 예를 들어, `my/app/link?os=6.0` 입력 시, 전체 마케팅 링크 URL은 `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`입니다.

   f. **[!UICONTROL 결정]** 탭을 클릭하고 결정 트리를 구성합니다.

   g. Android 앱이 설치되어 있는 경우 앱이 해당 논리로 딥링크를 처리합니다.

   최종 대상은 앱이 설치되지 않은 경우에만 대체 사례 역할을 합니다. 앱이 설치되지 않았으므로 최종 대상은 웹 링크 또는 앱스토어일 수 있습니다.

   h.**[!UICONTROL 저장]**&#x200B;을 클릭합니다.

>[!TIP]
>
>마케팅 링크가 저장되면 **[!UICONTROL 마케팅 링크 옵션]**&#x200B;을 변경할 수 없습니다. 이미 배포되었을 수도 있는 마케팅 링크의 동작을 변경하고 싶지 않기 때문입니다.

## 마케팅 링크 사용

이제 메시징과 앱의 다른 영역에서 이러한 마케팅 링크를 사용할 수 있습니다.

>[!IMPORTANT]
>
>범용 링크 또는 앱 링크에서는 클릭 추적 수가 표시되지 않으며, 상호 작용을 사용할 수도 없습니다.
