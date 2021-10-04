---
description: '보고서 세트를 구성하고 Android 앱 데이터를 수집하려면 먼저 다음 사전 요구 작업을 완료하십시오. '
solution: Experience Cloud,Analytics
title: 시작하기 전에
topic-fix: Developer and implementation
uuid: 0ca9e937-8d40-4570-9dbf-9aecc6ecedf6
exl-id: e9c0fd94-b61d-4f56-97b8-f71aac096c93
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 95%

---

# 시작하기 전에 {#before-you-start}

보고서 세트를 구성하고 Android 앱 데이터를 수집하려면 먼저 다음 사전 요구 작업을 완료하십시오.

## 역할별 작업 {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

분석 관리자 및 앱 개발자는 다음 작업을 완료해야 합니다.

### Analytics 관리자

보고서 세트를 구성하고 모바일 앱 데이터를 수집하려면

1. [Adobe Mobile Services UI에 로그인](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8)의 섹션 중 하나를 완료합니다.
1. 각 앱 개발자를 위한 Analytics 계정을 생성합니다.

이제 앱 개발자는 사용자가 생성한 보고서 세트를 보기 위해 액세스할 수 있습니다.

>[!IMPORTANT]
>
>새 보고서 세트를 생성하고 SDK를 다운로드하려면 Analytics 관리자여야 합니다.

### 앱 개발자

1. Analytics 관리자가 *역할별 작업*&#x200B;의 [Analytics 관리자](../getting-started/requirements.md#section_8B9EA1FA189F4C6DB7D829F0B5844FBC)에 있는 단계를 완료했는지 확인합니다.
1. Analytics 관리자가 [Adobe Mobile Services UI에 로그인](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8)의 섹션 중 하나를 완료했는지 확인합니다.
1. 보고서 세트를 구성한 후 [SDK 다운로드](../getting-started/requirements.md#section_044C17DF82BC4FD8A3E409C456CE9A46)의 단계를 완료합니다.

역할 및 사용 권한에 대한 자세한 내용은 [역할 및 권한](/help/using/gs/c-mob-roles-and-permissions.md)을 참조하십시오.

## Adobe Mobile Services UI에 로그인 {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services는 모바일 앱 분석 및 타깃팅용 주요 보고 인터페이스입니다. 이 단계를 완료하면 데이터 수집 서버, 보고서 세트 및 기타 다양한 설정을 통해 사전 구성된 구성 파일을 다운로드할 수 있습니다.

다음 방법 중 하나로 Adobe Mobile Services UI에 로그인할 수 있습니다.

### Experience Cloud

Adobe ID를 사용하여 [Experience Cloud](https://experiencecloud.adobe.com)에 로그인합니다. 이 방법에서는 회사가 Experience Cloud에서 프로비저닝되었으며, 사용자가 Analytics 계정을 연결했다고 가정합니다. 자세한 내용은 Experience Cloud 중앙 인터페이스 구성 요소 안내서의 [Experience Cloud 사용자 및 제품 관리](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html)를 참조하십시오.

>[!TIP]
>
>회사가 Experience Cloud에서 프로비저닝되었는지 확실하지 않을 경우 기존 Adobe Analytics 계정을 사용하십시오.

### Adobe Analytics

**[!UICONTROL Analytics로 로그인]**&#x200B;을 클릭하고 Analytics 회사 이름, 사용자 이름 및 암호를 입력합니다.

## 보고서 세트 생성 {#section_7BC602ED1ABA42C6AB722F506B5219F3}

보고서 세트를 생성하여 앱 데이터를 수집하고 앱을 정의하려면

1. [Mobile Services Adobe](https://mobilemarketing.adobe.com)에 로그인합니다.
1. **[!UICONTROL 앱 만들기]**&#x200B;를 클릭합니다.

   이 단추가 표시되지 않으면 **[!UICONTROL 앱 관리]** > **[!UICONTROL 추가]**&#x200B;를 클릭하십시오.

1. **[!UICONTROL 보고서 세트]** 드롭다운에서 **[!UICONTROL 새 보고서 세트]**&#x200B;를 선택합니다.

1. 앱 이름을 입력하고 보고서 세트 유형을 선택합니다.

   보고서 세트 ID의 예는 `mycomobileappdev`입니다. 개발 및 프로덕션 버전에 대해 별도의 보고서 세트 및 앱을 설정해야 하므로 프로덕션 버전을 설정할 준비가 되면 이 단계를 반복할 수 있습니다.
1. **[!UICONTROL 보고서 세트 ID]**&#x200B;에서 보고서 세트 이름이 표시되는지 확인합니다.
1. **[!UICONTROL 다음에서 설정 복사]**&#x200B;에서 **[!UICONTROL 모바일 앱 템플릿]**&#x200B;이 선택되어 있는지 확인합니다.

   이 템플릿을 사용하면 타임스탬프에서 오프라인 데이터를 수집할 수 있으며, 라이프사이클 지표를 캡처하는 모바일 솔루션 변수를 활성화합니다.

1. 시간대와 통화를 선택하고 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

## SDK 다운로드 {#section_044C17DF82BC4FD8A3E409C456CE9A46}

모바일 SDK를 다운로드하려면 다음을 수행하십시오.

1. 브라우저에 [https://mobilemarketing.adobe.com/](https://mobilemarketing.adobe.com/)을 입력하여 Mobile Services UI에 로그인합니다.
1. 왼쪽 창에서 **[!UICONTROL 모든 앱]** 드롭다운 목록을 클릭하고 앱을 선택합니다.
오른쪽 창에서 앱을 선택할 수도 있습니다.

   >[!IMPORTANT]
   >
   >오른쪽 창에 앱이 표시되도록 하려면 먼저 앱을 만들어야 합니다. 앱 만들기에 대한 자세한 내용은 [새 앱 추가](/help/using/manage-apps/t-new-app.md)를 참조하십시오.

1. 앱의 왼쪽 창에서 **[!UICONTROL 앱 설정 관리]**&#x200B;를 클릭합니다.

   >[!IMPORTANT]
   >
   >**[!UICONTROL 앱 설정 관리]** 옵션이 표시되지 않는 경우, Adobe Mobile Services에 로그인되어 있는지 확인하십시오. 확인하려면 페이지 오른쪽 상단의 ![솔루션 전환기](assets/solution-switcher.png) 아이콘을 클릭하고 **[!UICONTROL Adobe Mobile Services]**&#x200B;가 왼쪽 상단에 표시되는지 확인합니다.

1. 앱 설정 관리 페이지 하단의 **[!UICONTROL 앱 SDK 다운로드]** 섹션에서 플랫폼용 SDK 및 샘플 앱을 다운로드합니다.

>[!TIP]
>
>앱의 구성 파일은 SDK 다운로드에 자동으로 포함되므로 별도로 이 파일을 다운로드할 필요가 없습니다. 그러나 이미 SDK를 다운로드한 경우 업데이트된 설정을 가져오려면 구성 파일을 다시 다운로드하십시오.

Android Studio를 사용하는 경우 앱의 `build.gradle` 파일에 다음을 추가할 수도 있습니다.

```java
compile 'com.adobe.mobile:adobeMobileLibrary:4.13.7'
```

다음 정보를 숙지하십시오.

* 코드 샘플의 버전 번호를 Android SDK의 적절한 버전으로 바꾸십시오.
* 구성 파일을 다운로드하여 프로젝트에 포함하십시오.
