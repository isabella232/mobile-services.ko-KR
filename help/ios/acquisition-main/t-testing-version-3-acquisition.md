---
description: 다음은 장치 지문 파일을 기반으로 V3 획득 캠페인 링크를 왕복하는 데 유용한 정보입니다.
seo-description: 다음은 장치 지문 파일을 기반으로 V3 획득 캠페인 링크를 왕복하는 데 유용한 정보입니다.
seo-title: V3 획득 테스트
solution: Experience Cloud,Analytics
title: V3 획득 테스트
uuid: 89137ccf-4839-4b37-926e-303cf8e511a5
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 97%

---


# V3 획득 테스트 {#testing-v-acquisition}

다음은 장치 지문 파일을 기반으로 V3 획득 캠페인 링크를 왕복하는 데 유용한 정보입니다.

>[!IMPORTANT]
>
> V3 Acquisition은 Adobe Mobile Services UI에서 Acquisition Builder로 생성한 획득 링크를 가리킵니다. 이 기능을 사용하려면 iOS SDK 버전 4.6.0 이상으로 업그레이드해야 합니다.

모바일 앱이 아직 App Store에 없는 경우 캠페인 링크를 만들 때 모든 모바일 앱을 대상으로 선택하십시오. 획득 링크를 클릭한 후 획득 서버가 리디렉션하는 앱에만 영향을 주지만 링크를 테스트하는 기능에는 영향을 주지 않습니다.

1. [모바일 앱 획득](/help/ios/acquisition-main/acquisition.md)의 필수 조건 작업을 완료합니다.
1. Adobe Mobile Services UI에서 **[!UICONTROL Acquisition Builder]**&#x200B;로 이동하고 획득 캠페인 URL을 생성합니다.

   예:

   ```
   https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode
   ```


   획득 링크에서 iOS 및 Android 앱을 모두 참조하는 경우 Apple Store를 기본 스토어로 사용하십시오.
1. 데스크탑 브라우저에서 생성된 링크를 열고 `https://c00.adobe.com/v3/<appid>/end`로 이동합니다.

   다음과 같이 JSON 응답에 `contextData`가 표시되어야 합니다.

   ```js
   {"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.
   ```

   `contextData`가 표시되지 않거나 일부가 누락된 경우 획득 URL이 수[동으로 획득 링크 작성](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md)에 지정된 형식을 따르는지 확인하십시오.
1. 구성 파일에서 다음 설정이 올바른지 확인합니다.

   | 설정 | 값 |
   |--- |--- |
   | acquisition | 서버는 `c00.adobe.com`이어야 합니다.   *`appid`*&#x200B;는 획득 링크에서 *`appid`*&#x200B;와 같아야 합니다. |
   | analytics | `referrerTimeout` 값은 0보다 커야 합니다. |


1. (선택 사항) 앱 구성 파일의 `ssl` 설정이 true일 경우 HTTPS 프로토콜을 사용하도록 획득 링크를 업데이트합니다.
1. 앱을 설치하려는 모바일 장치에서 생성된 링크를 클릭합니다.

   Adobe 서버(`c00.adobe.com`)는 지문 파일을 저장한 다음 앱스토어로 리디렉션합니다. 테스트를 위해 앱을 다운로드할 필요는 없습니다.
1. 6단계에서 사용한 것과 동일한 모바일 장치에서 처음으로 애플리케이션을 시작합니다.

   필요한 경우 앱을 삭제하고 다시 설치할 수 있습니다.
1. (선택 사항) SDK의 디버그 로깅을 사용하여 추가 정보를 가져옵니다.

   모두 올바르게 작동하면 다음 로그가 표시됩니다.

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   위의 로그가 표시되지 않으면 4단계와 5단계를 완료했는지 확인하십시오.

   다음은 가능한 오류에 대한 정보입니다.

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`
네트워크 오류가 발생했습니다.

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      응답 형식이 올바르지 않습니다.

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      응답에 `contextData` 매개 변수가 없습니다.

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name`이 `contextData`에 포함되어 있지 않습니다.

   * `Analytics - Acquisition referrer timed out`

      `referrerTimeout`에 정의된 시간 내에 응답을 가져오지 못했습니다. 값을 늘린 다음 다시 시도하십시오. 또한 앱을 설치하기 전에 획득 링크를 열어서 URL을 클릭하고 앱을 열 때 동일한 네트워크를 사용하고 있는지 확인해야 합니다.

      다음 정보를 숙지하십시오.

      * 획득 서버는 링크 클릭(6단계) 및 앱 실행(7단계)에 기록된 IP 주소 및 사용자 에이전트 정보를 기반으로 하는 속성 일치 기능을 제공합니다.

         URL을 클릭할 때와 앱을 열 때 동일한 네트워크에 있어야 합니다.

      * HTTP 모니터링 도구를 사용하면 앱에서 전송된 히트를 모니터링하여 획득 속성 확인을 제공할 수 있습니다.

         획득 서버로 전송되는 `/v3/<appid>/start` 요청과 `/v3/<appid>/end` 요청이 각각 하나씩 표시됩니다. 전송된 사용자 에이전트의 변형으로 인해 속성 확인이 실패할 수 있습니다.

         >[!TIP]
         >
         >`https://c00.adobe.com/v3/<appid>/start` 및 `https://c00.adobe.com/v3/<appid>/end`에 동일한 사용자 에이전트 값이 있는지 확인합니다.

      * 획득 링크와 SDK의 히트는 동일한 HTTP/HTTPS 프로토콜을 사용해야 합니다.

         링크는 HTTP를 사용하고 SDK는 HTTPS를 사용하는 등 링크와 히트가 다른 프로토콜을 사용하는 경우 IP 주소가 각 요청마다(일부 이동 통신사의 경우) 다를 수 있으며 속성 확인이 실패할 수 있습니다.
