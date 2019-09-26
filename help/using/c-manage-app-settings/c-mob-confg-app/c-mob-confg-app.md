---
description: 'On the Manage App Settings page, you can make the following types of changes '
seo-description: '앱 설정 관리 페이지에서 다음과 같은 유형의 변경을 수행할 수 있습니다 '
seo-title: 앱 구성
title: 앱 구성
uuid: c088e12d-73b6-40c4-b8cc-ec3bb3d3aa4a
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# 앱 구성 {#configuring-your-app}

[앱 설정 관리] 페이지에서 다음과 같은 유형을 변경할 수 있습니다.

* **앱 정보**

   이 섹션에는 앱 이름, 앱 유형, 주요 지표, 라이프사이클 및 위치 보고서와 같은 정보가 포함되어 있습니다.

   * **라이프사이클 보고서**

      >[!TIP]
      >
      >Adobe Analytics에서 보고서 세트를 만들었다면, 라이프사이클 보고서를 활성화해야 합니다. Adobe Mobile에서 보고서 세트를 만들었다면, 이 옵션이 기본적으로 활성화되어 있습니다.

      이 보고서에서는 다음 지표를 측정할 수 있습니다.

      * **획득**

         앱 다운로드 캠페인을 위해 참조 URL을 추적합니다. 자세한 내용은 [획득](/help/using/acquisition-main/acquisition-main.md).

      * **라이프사이클**

         라이프사이클이 구현된 후 모바일 라이브러리를 통해 자동으로 측정할 수 있는 지표와 차원을 추적합니다. 자세한 내용은 다음 섹션을 참조하십시오.

         * [iOS SDK 라이프사이클 지표](/help/ios/metrics.md)
         * [Android 라이프사이클 지표](/help/android/metrics.md)
         * [Windows 라이프사이클 지표](/help/universal-windows/metrics.md)
         * [BlackBerry 라이프사이클 지표](/help/blackberry/metrics.md)
      * **앱 작업**

         인앱 작업을 기반으로 보고서 및 경로 지정을 사용합니다.

      * **라이프타임 값**

         사용자가 구입, 광고 보기, 동영상 완료, 소셜 공유, 사진 업로드 등과 같은, 앱 KPI를 사용하여 시간이 지남에 따라 값을 누적시키는 방법을 이해합니다.

      * **시한 이벤트**

         첫 번째 구매 전 시간과 같이, 주요 앱 작업 간에 경과되는 시간(인앱 및 총 시간)을 측정합니다.


* **위치 보고서**

   이 옵션을 사용하면 보고서에서 위도 및 경도를 추적하고 특정 관심 영역(POI)을 식별할 수 있으며, 블루투스 비콘(UUID, 주, 보조 및 근접)을 추적할 수도 있습니다.

* **앱 SDK 및 개발자 테스터 도구**

   >[!IMPORTANT]
   >
   >SDK 및 도구를 다운로드하기 전에 SDK Analytics 옵션을 구성해야 합니다. 자세한 내용은 SDK Analytics [옵션 구성을 참조하십시오](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/t-config-analytics.md).

   4.x SDK로 업그레이드할 준비가 되었거나 새 앱에서 작업 중인 경우 [앱 설정 관리] 페이지 하단에서 최신 SDK 및 개발 도구를 다운로드합니다.

   설정이 완료되면, 데이터를 제대로 수집할 수 있도록 구성 파일을 개발자에게 보낼 수 있습니다. 지금 SDK 및 도구를 다운로드할 준비가 되어 있지 않다면 언제든지 앱 설정 관리를 클릭하고 앱을 클릭하여 앱 정보 페이지를 표시합니다.
