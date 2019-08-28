---
description: 다음 단계를 완료하여, iOS 앱 데이터를 수집하도록 보고서 세트를 구성하십시오.
seo-description: 다음 단계를 완료하여, iOS 앱 데이터를 수집하도록 보고서 세트를 구성하십시오.
seo-title: 시작하기 전에
solution: Marketing Cloud, Analytics
title: 시작하기 전에
topic: 개발자 및 구현
uuid: 04133 F 68-3618-41 FD -8 A 13-AEC 5 B 6 F 04 DF 6
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Before you start {#before-you-start}

다음 단계를 완료하여, iOS 앱 데이터를 수집하도록 보고서 세트를 구성하십시오.

## Role-specific tasks {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

분석 관리자 및 앱 개발자는 다음 작업을 완료해야 합니다.

### Analytics 관리자

보고서 세트를 구성하고 모바일 앱 데이터를 수집하려면

1. [Adobe Mobile Services UI에 로그인](/help/ios/getting-started/getting-started.md)의 섹션 중 하나를 완료합니다.
1. 각 앱 개발자를 위한 Analytics 계정을 생성합니다.

이제 앱 개발자는 사용자가 생성한 보고서 세트를 보기 위해 액세스할 수 있습니다.

>[!IMPORTANT]
>
>새 보고서 세트를 만들고 SDK를 다운로드하려면 Analytics 관리자여야 합니다.

### 앱 개발자

1. Ensure that your Analytics administrator has completed the steps in the *Analytics Administrators* section above.

1. Verify that your Analytics administrator has completed one of the sections in the *Log in to the Adobe Mobile Services UI* below.
1. After the report suite has been configured, complete steps in the *Download the SDK* section below.

역할 및 사용 권한에 대한 자세한 내용은 [역할 및 권한](/help/using/gs/c-mob-roles-and-permissions.md)을 참조하십시오.

## Adobe Mobile Services UI에 로그인 {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services는 모바일 앱 분석 및 타깃팅용 주요 보고 인터페이스입니다. 이 단계를 완료하면 데이터 수집 서버, 보고서 세트 및 기타 다양한 설정을 통해 사전 구성된 구성 파일을 다운로드할 수 있습니다.

다음 방법 중 하나로 Adobe Mobile Services에 로그인할 수 있습니다.

* **Experience Cloud**

   Adobe ID를 사용하여 [Experience Cloud](https://marketing.adobe.com)에 로그인합니다.

   이 방법은 회사가 프로비저닝되었으며 Analytics 계정을 연결했다고 가정합니다. 프로비저닝에 대한 자세한 내용은 Experience Cloud 사용자 및 제품 [관리를](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html)참조하십시오. 계정 연결에 대한 자세한 내용은 [조직 및 계정 연결을 참조하십시오](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/organizations.html).

   >[!TIP]
   >
   >회사가 Experience Cloud에서 프로비저닝되었는지 확신할 수 없는 경우 기존 Adobe Analytics 계정을 사용하십시오.

* **Adobe Analytics**

   **[!UICONTROL Analytics으로 로그인]**&#x200B;을 클릭하고 Analytics 회사 이름, 사용자 이름 및 암호를 입력합니다.

## 보고서 세트 만들기 {#section_7BC602ED1ABA42C6AB722F506B5219F3}

보고서 세트를 생성하여 앱 데이터를 수집하고 앱을 정의하려면

1. **[!UICONTROL 새 앱 만들기를 클릭합니다]**.

   If you do not see this button, click **[!UICONTROL Manage Apps]** &gt; **[!UICONTROL Add]**.

1. **[!UICONTROL 보고서 세트]** 드롭다운에서 **[!UICONTROL 새 보고서 세트를 선택합니다]**.

1. 앱 이름을 입력하고 고유 보고서 세트 ID를 선택합니다.

   보고서 세트 ID의 예는 `mycomobileappdev`입니다. 개발 및 프로덕션 버전에 대해 별도의 보고서 세트와 앱을 설정해야 합니다. 프로덕션 버전을 설정할 준비가 되었으면 다음 단계를 반복합니다.
1. **[!UICONTROL 모바일 앱 템플릿]을 선택한 상태로 둡니다.**

   이 템플릿을 사용하면 타임스탬프에서 오프라인 데이터를 수집할 수 있으며, 라이프사이클 지표를 캡처하는 모바일 솔루션 변수를 활성화합니다.

1. **[!UICONTROL 시간대]**&#x200B;와 **[!UICONTROL 통화]**&#x200B;를 선택하고 **저장[!UICONTROL 을 클릭합니다]**.

## SDK 다운로드 {#section_044C17DF82BC4FD8A3E409C456CE9A46}

모바일 SDK를 다운로드하려면 다음을 수행하십시오.

1. Mobile Services에 로그인하여 다음 방법 중 하나를 사용하여 앱을 엽니다.

   * **[!UICONTROL 모든 앱]드롭다운 목록에서 앱을 선택합니다.**
   * 오른쪽 패널에서 앱을 찾아서 엽니다.

1. **[!UICONTROL 앱 설정 관리를 클릭합니다]**.
1. **[!UICONTROL 앱 SDK 다운로드]** 섹션에서 **앱 SDK 다운로드[!UICONTROL 섹션으로 스크롤합니다.]**

1. 플랫폼용 SDK 및 샘플 앱을 다운로드합니다.

>[!TIP]
>
>앱에 대한 구성 파일은 SDK 다운로드에 자동으로 포함되므로 해당 파일을 별도로 다운로드할 필요가 없습니다. 그러나 이미 SDK를 다운로드한 경우 업데이트된 설정을 가져오려면 구성 파일을 다시 다운로드하십시오.

