---
description: 다음은 Android 장치에서 버전 3 획득 캠페인 링크를 왕복하는 데 유용한 정보입니다.
keywords: android;라이브러리;모바일;sdk
seo-description: 다음은 Android 장치에서 버전 3 획득 캠페인 링크를 왕복하는 데 유용한 정보입니다.
seo-title: 버전 3 획득 테스트
solution: Experience Cloud,Analytics
title: 버전 3 획득 테스트
topic-fix: Developer and implementation
uuid: 5e38b43d-389e-4412-99e5-3e6223b6ad28
exl-id: 2ce78e2e-da51-4af8-a461-ec6c642a7854
source-git-commit: bb2459e57274183e55c1facd1a510cf55a83ddb4
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 100%

---

# V3 획득 테스트 {#testing-version-acquisition}

다음은 Android 장치에서 버전 3 획득 캠페인 링크를 왕복하는 데 유용한 정보입니다.

>[!IMPORTANT]
>
>V3의 획득은 Adobe Mobile Services UI에서 획득 빌더로 생성한 획득 링크를 가리킵니다. 이 기능을 사용하려면 Experience Cloud 솔루션 4.6.0 이상을 위한 Android SDK 4.x로 업그레이드해야 합니다.

모바일 앱이 아직 Google Play에 없는 경우 캠페인 링크를 만들 때 모바일 앱을 대상으로 선택할 수 있습니다. 획득 링크를 클릭한 후 획득 서버가 리디렉션하는 앱에만 영향을 주지만 링크를 테스트하는 기능에는 영향을 주지 않습니다. 쿼리 문자열 매개 변수가 Google Play 스토어에 전달되고 캠페인 브로드캐스트의 일부로 설치 시 앱에 전달됩니다. 양방향 모바일 앱 확보 테스트에서는 이러한 유형의 브로드캐스트를 시뮬레이션해야 합니다.

>[!IMPORTANT]
>
>Google Play 설치 레퍼러 API를 사용하여 구현하는 경우 Google Play Store에 앱이 있기 전에 획득을 테스트할 수 없습니다.

테스트가 실행될 때마다 앱을 새로 설치하거나 **[!UICONTROL 설정]**&#x200B;에서 데이터를 지워야 합니다. 이렇게 하면 앱을 처음 시작할 때 캠페인 쿼리 문자열 매개 변수와 연결된 초기 라이프사이클 지표를 전달할 수 있습니다.

1. [모바일 앱 획득](/help/android/acquisition-main/acquisition.md)에서 사전 요구 작업을 완료하고 `INSTALL_REFERRER`에 대한 브로드캐스트 수신기를 올바르게 구현했는지 확인합니다.

1. Adobe Mobile Services UI에서 **[!UICONTROL 획득]** > **[!UICONTROL 마케팅 링크 빌더]**&#x200B;를 클릭하고 Google Play를 Android 장치의 대상으로 설정하는 획득 마케팅 링크 URL을 생성합니다.

   자세한 정보는 [마케팅 링크 빌더](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)를 참조하십시오.

   예, `https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=g&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode`.

   >[!TIP]
   >
   >획득 링크에서 Android 및 iOS 앱을 모두 참조하는 경우 Google Play를 기본 스토어로 사용하십시오.

1. 데스크탑 브라우저에서 생성된 링크를 엽니다.

   다음 예와 비슷한 URL이 포함된 페이지로 리디렉션해야 합니다.
   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. `utm_content%3D` 뒤의 고유 ID를 복사합니다.

   이전 예에서 이 ID는 `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`입니다.

1. 3단계의 고유 ID를 사용하여 다음 형식의 획득 종료 링크를 구성합니다.

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`에 로그인되어 있는지 확인하십시오.

   예, `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

1. 데스크탑 브라우저에서 링크를 엽니다.

   JSON 응답에 `contextData`가 표시되어야 합니다.

   `{"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.`

   `contextData`가 표시되지 않거나 문자열 일부가 누락된 경우 획득 URL이 [수동으로 획득 링크 작성](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md)의 형식을 따르는지 확인하십시오.
1. 3단계를 반복하여 새 고유 ID를 얻습니다.
1. 구성 파일에서 다음 설정이 올바른지 확인합니다.

   | 설정 | 값 |
   |--- |--- |
   | acquisition | 서버는 `c00.adobe.com`이어야 합니다.   *`appid`*  는 획득 링크에서 `appid`  와 같아야 합니다. |
   | analytics | 테스트를 위해 레퍼러 시간 초과를 설정하여 브로드캐스트를 수동으로 전송하는 적절한 시간(60초 이상)을 허용합니다. 테스트 후 원래 시간 초과 설정을 복원할 수 있습니다. |

1. 장치를 컴퓨터에 연결하고 앱을 제거한 다음 다시 설치합니다.
1. ADB 셸을 실행하고 장치에서 애플리케이션을 실행합니다.
1. 다음 `adb`명령을 사용하여 브로드캐스트를 전송합니다.

   `am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"`

1. 다음 단계를 완료합니다.
   1. `com.adobe.android` 을 애플리케이션의 패키지 이름으로 바꿉니다.
   1. 수신자 참조를 앱의 캠페인 추적 수신자 위치로 업데이트합니다.
   1. `utm_content`와 관련된 값을 대체합니다.

   브로드캐스트가 성공하면 다음 예시와 같은 응답을 받을 것입니다.

   ```
   Broadcasting: Intent
   { act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) }
   Broadcast completed: result=0
   ```

1. (선택 사항) SDK의 디버그 로깅을 사용하여 추가 정보를 가져옵니다.

   모두 올바르게 작동하면 다음 로그가 표시됩니다.

`"Analytics - Received referrer information(<referrer content>)"   "Analytics - Trying to fetch referrer data from (acquisition end url)"; "Analytics - Received Referrer Data(<A JSON Response>)"`

위 로그가 표시되지 않으면 6~12단계를 완료했는지 확인하십시오.

다음 표에는 가능한 오류에 대한 추가 정보가 포함되어 있습니다.

| 오류 | 설명 |
|--- |--- |
| Analytics - Unable to decode response(*String*). | 응답 형식이 잘못되었습니다. |
| Analytics - Unable to parse response (*a JSON Response*). | JSON 문자열의 형식이 잘못되었습니다. |
| Analytics - Unable to parse acquisition service response (no contextData parameter in response). | 응답에 contextData 매개 변수가 없습니다. |
| Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name`이 contextData에 포함되어 있지 않습니다. |
| Analytics - Acquisition referrer timed out. | `referrerTimeout`에 정의된 시간 내에 응답을 가져오지 못했습니다. 값을 늘린 다음 다시 시도하십시오.  또한 앱을 설치하기 전에 획득 링크를 열었는지 확인해야 합니다. |

다음 정보를 숙지하십시오.

* HTTP 모니터링 도구를 사용하여 획득 속성을 확인하여 앱에서 전송된 히트를 모니터링할 수 있습니다.
* `INSTALL_REFERRER`를 브로드캐스트하는 자세한 방법은 Google 개발자 가이드의 [Google Play 캠페인 측정 테스트](https://developers.google.com/analytics/solutions/testing-play-campaigns)를 참조하십시오.

* Android 4.8.2의 획득에 대한 버그 수정이 릴리스되었습니다.

   테스트하기 전에 SDK를 최신 버전으로 업그레이드하십시오.

* 제공된 `acquisitionTest.jar` Java 도구를 사용하여 고유 ID 및 브로드캐스트 설치 레퍼러를 가져와 3-12단계의 정보를 차례로 가져올 수 있습니다.

   **Java 도구 설치**

Java 도구를 설치하려면

1. [`acquisitionTester.zip`](/help/android/assets/acquisitionTester.zip) 파일을 다운로드합니다.

1. .jar 파일을 추출합니다.

   명령줄에서 파일을 실행할 수 있습니다.

   예:

   ```java
   java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
   ```
