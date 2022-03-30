---
description: 다음 단계를 완료하여, iOS 앱 데이터를 수집하도록 보고서 세트를 구성하십시오.
solution: Experience Cloud Services,Analytics
title: 시작하기 전에
topic-fix: Developer and implementation
uuid: 04133f68-3618-41fd-8a13-aec5b6f04df6
exl-id: 83da7cf5-3211-484d-bfe8-7b3b4999eea2
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 94%

---

# 시작하기 전에 {#before-you-start}

다음 단계를 완료하여, iOS 앱 데이터를 수집하도록 보고서 세트를 구성하십시오.

## 역할별 작업 {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

분석 관리자 및 앱 개발자는 다음 작업을 완료해야 합니다.

### Analytics 관리자

보고서 세트를 구성하고 모바일 앱 데이터를 수집하려면

1. [Adobe Mobile Services UI에 로그인](/help/ios/getting-started/getting-started.md)의 섹션 중 하나를 완료합니다.
1. 각 앱 개발자를 위한 Analytics 계정을 생성합니다.

이제 앱 개발자는 사용자가 생성한 보고서 세트를 보기 위해 액세스할 수 있습니다.

>[!IMPORTANT]
>
>새 보고서 세트를 생성하고 SDK를 다운로드하려면 Analytics 관리자여야 합니다.

### 앱 개발자

1. Analytics 관리자가 위의 *Analytics 관리자* 섹션에 있는 단계를 완료했는지 확인합니다.

1. Analytics 관리자가 아래 *Adobe Mobile Services UI에 로그인*&#x200B;의 섹션 중 하나를 완료했는지 확인합니다.
1. 보고서 세트를 구성한 후 아래의 *SDK 다운로드* 섹션의 단계를 완료합니다.

역할 및 사용 권한에 대한 자세한 내용은 [역할 및 권한](/help/using/gs/c-mob-roles-and-permissions.md)을 참조하십시오.

## Adobe Mobile Services UI에 로그인 {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services는 모바일 앱 분석 및 타깃팅용 주요 보고 인터페이스입니다. 이 단계를 완료하면 데이터 수집 서버, 보고서 세트 및 기타 다양한 설정을 통해 사전 구성된 구성 파일을 다운로드할 수 있습니다.

다음 방법 중 하나로 Adobe Mobile Services에 로그인할 수 있습니다.

* **Experience Cloud**

   Adobe ID를 사용하여 [Experience Cloud](https://experience.adobe.com)에 로그인합니다.

   이 방법에서는 회사가 프로비저닝되었으며, 사용자가 Analytics 계정을 연결했다고 가정합니다. 프로비저닝에 대한 자세한 내용은 [Experience Cloud 사용자 및 제품 관리](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=ko-KR) ( Experience Cloud 중앙 인터페이스 구성 요소 안내서). 계정 연결에 대한 자세한 내용은 [Experience Cloud의 조직](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=ko).

   >[!TIP]
   >
   >회사가 Experience Cloud에서 프로비저닝되었는지 확실하지 않을 경우 기존 Adobe Analytics 계정을 사용하십시오.

* **Adobe Analytics**

   **[!UICONTROL Analytics로 로그인]**&#x200B;을 클릭하고 Analytics 회사 이름, 사용자 이름 및 암호를 입력합니다.

## 보고서 세트 생성 {#section_7BC602ED1ABA42C6AB722F506B5219F3}

보고서 세트를 생성하여 앱 데이터를 수집하고 앱을 정의하려면

1. **[!UICONTROL 새 앱 만들기]**&#x200B;를 클릭합니다.

   이 단추가 표시되지 않으면 **[!UICONTROL 앱 관리]** > **[!UICONTROL 추가]**&#x200B;를 클릭하십시오.

1. **[!UICONTROL 보고서 세트]** 드롭다운에서 **[!UICONTROL 새 보고서 세트]**&#x200B;를 선택합니다.

1. 앱 이름을 입력하고 고유 보고서 세트 ID를 선택합니다.

   보고서 세트 ID의 예는 `mycomobileappdev`입니다. 개발 및 프로덕션 버전에 대해 별도의 보고서 세트와 앱을 설정해야 합니다. 프로덕션 버전을 설정할 준비가 되면 다음 단계를 반복합니다.
1. **[!UICONTROL 모바일 앱 템플릿]**&#x200B;을 선택한 상태로 둡니다.

   이 템플릿을 사용하면 타임스탬프에서 오프라인 데이터를 수집할 수 있으며, 라이프사이클 지표를 캡처하는 모바일 솔루션 변수를 활성화합니다.

1. **[!UICONTROL 시간대]**&#x200B;와 **[!UICONTROL 통화]**&#x200B;를 선택하고 **[!UICONTROL 저장을 클릭합니다]**.

## SDK 다운로드 {#section_044C17DF82BC4FD8A3E409C456CE9A46}

모바일 SDK를 다운로드하려면 다음을 수행하십시오.

1. 다음 방법 중 하나로 Mobile Services에 로그인하고 앱을 엽니다.

   * **[!UICONTROL 모든 앱]** 드롭다운 목록에서 앱을 선택합니다.
   * 오른쪽 패널에서 앱을 찾아서 엽니다.

1. **[!UICONTROL 앱 설정 관리를 클릭합니다]**.
1. **[!UICONTROL 앱 SDK 다운로드]** 섹션에서 **[!UICONTROL 앱 SDK 다운로드 섹션으로 스크롤합니다.]**

1. 플랫폼용 SDK 및 샘플 앱을 다운로드합니다.

>[!TIP]
>
>앱의 구성 파일은 SDK 다운로드에 자동으로 포함되므로 별도로 이 파일을 다운로드할 필요가 없습니다. 그러나 이미 SDK를 다운로드한 경우 업데이트된 설정을 가져오려면 구성 파일을 다시 다운로드하십시오.
