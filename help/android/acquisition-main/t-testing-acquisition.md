---
description: 다음은 Android 장치에서 기존 획득 캠페인 링크를 왕복하는 데 유용한 정보입니다.
keywords: android;라이브러리;모바일;sdk
seo-description: 다음은 Android 장치에서 기존 획득 캠페인 링크를 왕복하는 데 유용한 정보입니다.
seo-title: 기존 획득 테스트
solution: Experience Cloud,Analytics
title: 기존 획득 테스트
topic-fix: Developer and implementation
uuid: bb7ace96-68eb-4f43-b3cf-af80730b9cee
exl-id: 43e3b24e-e8bc-407c-b788-5ab85e459a90
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 100%

---

# 기존 획득 테스트 {#testing-legacy-acquisition}

다음은 Android 장치에서 기존 획득 캠페인 링크를 왕복하는 데 유용한 정보입니다.

모바일 앱이 아직 Google Play에 없을 경우 캠페인 링크를 생성할 때 모바일 앱을 대상으로 선택할 수 있습니다. 획득 링크를 클릭한 후 획득 서버가 리디렉션하는 앱에만 영향을 주지만 획득 링크를 테스트하는 기능에는 영향을 주지 않습니다. 쿼리 문자열 매개 변수가 Google Play 스토어에 전달되고 캠페인 브로드캐스트의 일부로 설치 시 앱에 전달됩니다. 양방향 모바일 앱 확보 테스트에서는 이러한 유형의 브로드캐스트를 시뮬레이션해야 합니다.

테스트가 실행될 때마다 앱을 새로 설치하거나 **[!UICONTROL 설정]**&#x200B;에서 데이터를 지워야 합니다. 이렇게 하면 앱을 처음 시작할 때 캠페인 쿼리 문자열 매개 변수와 연결된 초기 라이프사이클 지표를 전달할 수 있습니다.

1. Mobile Services UI에서 기존 취득 캠페인 URL을 생성합니다.

   자세한 내용은 [기존 획득 링크 사용](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md)을 참조하십시오.
1. 장치를 컴퓨터에 연결하고 ADB 셸을 시작한 다음 장치에서 애플리케이션을·시작합니다.
1. 다음 형식으로 브로드캐스트를 전송합니다.

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.example.adobetesttapp/com.google.analytics.tracking.android.CampaignTrackingReceiver --es "referrer" "utm_source=testSource&utm_medium=testMedium&utm_term=testTerm&utm_content=testContent&utm_campaign=testCampaign&trackingcode=trackingvalue"
   ```

1. 다음 단계를 완료합니다.
   1. `com.example.adobetesttapp.com`을 애플리케이션의 역방향 DNS 시작으로 바꿉니다.
   1. 앱에서 캠페인 추적 수신자 위치 참조로 수신자 참조를 업데이트합니다.
   1. `utm_source`, `utm_medium`, `utm_term`, `utm_content`, `utm_campaign` 등과 관련된 값을 적절한 값으로 바꿉니다.

브로드캐스트에 성공하면 아래 응답과 유사한 응답이 표시됩니다.

```
Broadcasting: Intent { act=com.android.vending.INSTALL_REFERRER cmp=com.example.analyticsecommtest/com.google.analytics.tracking.android.AnalyticsReceiver has extras) } Broadcast completed: result=0
```

Adobe의 데이터 수집 서버로 보낸 이미지 요청도 표시됩니다. SDK에서 캠페인 매개 변수를 포함하지 않는 이미지 요청과 함께 1단계에서 설정한 레퍼러 제한 시간을 모두 소진하면 브로드캐스트가 실패했습니다.
