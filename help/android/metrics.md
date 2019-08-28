---
description: 다음은 라이프사이클을 구현한 후 모바일 라이브러리에서 자동으로 측정할 수 있는 지표 및 차원을 안내합니다. 또한 라이프사이클 데이터 문제 해결을 안내하는 링크도 제공합니다.
keywords: Android; 라이브러리; 모바일; SDK
seo-description: 다음은 라이프사이클을 구현한 후 모바일 라이브러리에서 자동으로 측정할 수 있는 지표 및 차원을 안내합니다. 또한 라이프사이클 데이터 문제 해결을 안내하는 링크도 제공합니다.
seo-title: 라이프사이클 지표
solution: Marketing Cloud, Analytics
title: 라이프사이클 지표
topic: 개발자 및 구현
uuid: a 8 f 3 ebac-be 3 b -4948-82 bb -105 d 46 cfff 6 d
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Lifecycle metrics{#lifecycle-metrics}

이 섹션에서는 라이프사이클이 구현된 후 모바일 라이브러리에서 자동으로 측정할 수 있는 지표 및 차원, 라이프사이클 데이터 문제 해결에 대한 링크를 제공합니다. 문제 해결에 대한 자세한 내용은 라이프사이클 데이터 [문제 해결을](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html)참조하십시오.

## 새 Adobe Experience Cloud SDK 릴리스

Adobe Experience Platform Mobile SDK와 관련된 정보 및 문서 찾기 최신 문서를 보려면 [여기](https://aep-sdks.gitbook.io/docs/)를 클릭하십시오.

>[!IMPORTANT]
>
>2018년 9월 일자로 SDK의 새로운 주요 버전을 릴리스하였습니다. 이러한 새로운 Adobe Experience Platform Mobile SDK는 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html)를 통해 구성할 수 있습니다.

* 시작하려면 [Launch](https://launch.adobe.com/)로 이동합니다.
* Experience Platform SDK 리포지토리의 항목을 보려면 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)로 이동하십시오.

## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

구성된 경우 라이프사이클 지표가 컨텍스트 데이터 매개 변수로 Analytics에 전송되고, 각 mbox 호출을 통해 매개 변수로 Target에 전송되며, 고객 관리에 신호로 전송됩니다. 분석 및 타겟은 같은 형식을 사용하지만, 대상 관리는 각 지표에 다른 접두사를 사용합니다.

Analytics의 경우 각 라이프사이클 추적 호출을 사용하여 전송된 컨텍스트 데이터는 지표 또는 차원을 사용하여 자동으로 캡처되고 보고되며 예외가 표시됩니다.

### 지표

* **첫 번째 실행**

   설치 또는 재설치 후 처음 실행할 때 트리거됩니다.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.InstallEvent`
   * Audience Manager 신호: `c_a_InstallEvent`

* **업그레이드**

   업그레이드 후 또는 버전 번호가 변경되고 처음 실행할 때 트리거됩니다.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.UpgradeEvent`
   * Audience Manager 신호: `c_a_UpgradeEvent`

* **일별 참여 사용자**

   특정 날짜에 애플리케이션을 사용할 때 트리거됩니다.

   >[!IMPORTANT]
   >
   >이 지표는 Analytics 지표에 자동으로 저장되지 않습니다. 이 지표를 캡처하려면 사용자 지정 이벤트를 설정하는 처리 규칙을 만들어야 합니다.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.DailyEngUserEvent`
   * Audience Manager 신호: `c_a_DailyEngUserEvent`

* **월별 참여 사용자**

   특정 월에 애플리케이션을 사용할 때 트리거됩니다.

   >[!IMPORTANT]
   >
   >이 지표는 Analytics 지표에 자동으로 저장되지 않습니다. 이 지표를 캡처하려면 사용자 지정 이벤트를 설정하는 처리 규칙을 만들어야 합니다.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.MonthlyEngUserEvent`
   * Audience Manager 신호: `c_a_MonthlyEngUserEvent`

* **시작**

   충돌 및 설치를 포함하여 매 실행 시 트리거됩니다. 또한 라이프사이클 세션 시간 제한이 초과되면 백그라운드에서 다시 시작될 때 트리거됩니다.

   >[!IMPORTANT]
   >
   >이 지표는 Analytics 지표에 자동으로 저장되지 않습니다. 이 지표를 캡처하려면 사용자 지정 이벤트를 설정하는 처리 규칙을 만들어야 합니다.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.LaunchEvent`
   * Audience Manager 신호: `c_a_LaunchEvent`

* **충돌**

   애플리케이션이 닫기 전에 백그라운드에 있지 않을 경우 트리거됩니다. 이 이벤트는 충돌 후 애플리케이션이 시작될 때 전송됩니다.  Adobe Mobile 충돌 보고는 발견되지 않은 전역 예외 핸들러를 구현하지 않습니다.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.CrashEvent`
   * Audience Manager 신호: `c_a_CrashEvent`

* **이전 세션 길이**

   애플리케이션이 전경에서 열려 있는 시간을 기반으로 하여 이전 애플리케이션 세션이 지속된 시간(초)을 보고합니다.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.PrevSessionLength`
   * Audience Manager 신호: `c_a_PrevSessionLength`


### 차원

* **설치 날짜**

   설치 후 처음 시작하는 날짜 날짜 형식은 YYYY/MM/DD입니다.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.InstallDate`
   * Audience Manager: `c_a_InstallDate`

* **앱 ID**

   Stores the application name and version in the `[AppName] [BundleVersion]` format. 이 형식의 예는 `myapp 1.1`입니다.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.AppID`
   * Audience Manager: `c_a_AppID`

* **시작 번호**

   응용 프로그램을 시작하거나 백그라운드에서 나온 횟수입니다.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.Launches`
   * Audience Manager: `c_a_Launches`

* **처음 사용한 이후 일수**

   처음 실행한 이후 일 수.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.DaysSinceFirstUse`
   * Audience Manager: `c_a_DaysSinceFirstUse`

* **마지막 사용한 이후 일수**

   마지막 사용한 이후 일 수.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.DaysSinceLastUse`
   * Audience Manager: `c_a_DaysSinceLastUse`

* **시간**

   앱을 시작한 시간을 측정합니다.  이 지표는 24시간 숫자 형식을 사용하며 최대 사용 시간을 판별하기 위한 시간 구분에 사용됩니다.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.HourOfDay`
   * Audience Manager: `c_a_HourOfDay`

* **요일**

   앱이 실행된 주의 일수

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.DayOfWeek`
   * Audience Manager: `c_a_DayOfWeek`

* **운영 체제 버전**

   OS 버전.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.OSVersion`
   * Audience Manager: `c_a_OSVersion`

* **마지막 업그레이드한 이후 일수**

   애플리케이션 버전 번호가 변경된 이후의 일수입니다.

   >[!IMPORTANT]
   >
   >이 지표는 Analytics 변수에 자동으로 저장되지 않습니다. 보고를 위해 이 값을 Analytics 변수에 복사하려면 처리 규칙을 생성해야 합니다.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.DaysSinceLastUpgrade`
   * Audience Manager: `c_a_DaysSinceLastUpgrade`

* **마지막 업그레이드 이후 출시**

   애플리케이션 버전 번호가 변경된 이후의 시작 횟수.

   >[!IMPORTANT]
   >
   >이 지표는 Analytics 변수에 자동으로 저장되지 않습니다. 보고를 위해 이 값을 Analytics 변수에 복사하려면 처리 규칙을 생성해야 합니다.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.LaunchesSinceUpgrade`
   * Audience Manager: `c_a_LaunchesSinceUpgrade`

* **장치 이름**

   장치 이름을 저장합니다.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.DeviceName`
   * Audience Manager: `c_a_DeviceName`

* **통신사 이름**

   장치에서 제공한 대로 모바일 서비스 공급자의 이름을 저장합니다.  중요: 이 지표는 Analytics 변수에 자동으로 저장되지 않습니다. 보고를 위해 이 값을 Analytics 변수에 복사하려면 처리 규칙을 생성해야 합니다.

   >[!IMPORTANT]
   >
   >이 지표는 Analytics 변수에 자동으로 저장되지 않습니다. 보고를 위해 이 값을 Analytics 변수에 복사하려면 처리 규칙을 생성해야 합니다.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.CarrierName`
   * Audience Manager: `c_a_CarrierName`

* **해상도**

   너비 x 높이(실제 픽셀)

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.Resolution`
   * Audience Manager: `c_a_Resolution`

## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

다음 메트릭 및 차원은 **설명** 열에 나열된 메서드에 따라 모바일 솔루션 변수에서 캡처됩니다.

### 지표

* **총 동작 시간**

   Populated by `trackTimedAction` methods.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.action.time.total`
   * Audience Manager 특성: `c_a_action_time_total`

* **앱의 동작 시간**

   Populated by `trackTimedAction` methods.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.action.time.inapp`
   * Audience Manager 특성: `c_a_action_time_inapp`

* **라이프타임 값(이벤트)**

   Populated by `trackLifetimeValue` methods.

   * Analytics 컨텍스트 데이터/타겟 매개 변수: `a.ltv.amount`
   * Audience Manager 특성: `c_a_ltv_amount`

### 차원

* **위치(10km까지)**

   Populated by `trackLocation` methods.

   * Analytics 컨텍스트 데이터/타겟 매개 변수:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Manager 트레이트:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **위치(100m까지)**

   trackLocation 메서드로 채워집니다.

   * Analytics 컨텍스트 데이터/타겟 매개 변수:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Manager 트레이트:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **위치(1m까지)**

   trackLocation 메서드로 채워집니다.

   * Analytics 컨텍스트 데이터/타겟 매개 변수:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Manager 트레이트:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **관심 영역 이름**

   디바이스가 정의된 POI 내에 있을 때 trackLocation 메서드로 채워집니다.

   * Analytics Context Data/Target Parameters: `a.loc.poi`
   * Audience Manager 특성: `c_a_loc_poi`

* **관심 영역 중앙까지의 거리**

   디바이스가 정의된 POI 내에 있을 때 trackLocation 메서드로 채워집니다.

   * Analytics Context Data/Target Parameters: `a.loc.dist`
   * Audience Manager 특성: `c_a_loc_dist`

* **라이프타임 값(전환 변수)**

   trackLifetimeValue 메서드로 채워집니다.

   * Analytics Context Data/Target Parameters: `a.ltv.amount`
   * Audience Manager 특성: `c_a_ltv_amount`

* **추적 코드**

   Mobile App Acquisition에 의해 채워지고 Adobe Mobile Services에 의해 자동으로 생성됩니다.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.trackingcode`
   * Audience Manager 특성: `c_a_referrer_campaign_trackingcode`

* ** 캠페인

   캠페인의 이름으로, 캠페인 변수에도 저장됩니다. 모바일 앱 획득을 통해 채워집니다.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.name`
   * Audience Manager 특성: `c_a_referrer_campaign_name`

* **캠페인 내용**

   링크를 표시한 콘텐츠의 이름 또는 ID입니다. 모바일 앱 획득을 통해 채워집니다.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.content`
   * Audience Manager 특성: `c_a_referrer_campaign_content`

* **캠페인 매체**

   배너 또는 이메일과 같은 마케팅 매체입니다. 모바일 앱 획득을 통해 채워집니다.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.medium`
   * Audience Manager 특성: `c_a_referrer_campaign_medium`

* **캠페인 소스**

   뉴스레터 또는 소셜 미디어 네트워크와 같은 원본 레퍼러입니다. 모바일 앱 획득을 통해 채워집니다.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.source`
   * Audience Manager 특성: `c_a_referrer_campaign_source`

* **캠페인 용어**

   이 획득을 사용하여 추적하려는 유료 키워드 또는 기타 용어입니다. 모바일 앱 획득을 통해 채워집니다.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.term`
   * Audience Manager 특성: `c_a_referrer_campaign_term`
