---
description: 다음은 장치 지문을 기반으로 하는 마케팅 링크를 사용하는 획득 캠페인을 왕복하는 데 유용한 지침입니다.
keywords: android;라이브러리;모바일;sdk
solution: Experience Cloud Services,Analytics
title: 마케팅 링크 획득 테스트
topic-fix: Developer and implementation
uuid: 69503e01-182d-44c6-b0fb-e1c012ffa3bd
exl-id: 2fb02b36-172e-4c16-9ef9-13f8288ab8a4
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 마케팅 링크 획득 테스트 {#testing-marketing-link-acquisition}

다음은 장치 지문을 기반으로 하는 마케팅 링크를 사용하는 획득 캠페인을 왕복하는 데 유용한 지침입니다.

1. [모바일 앱 획득](/help/ios/acquisition-main/acquisition.md)의 필수 조건 작업을 완료합니다.
1. Adobe Mobile Services UI에서 **[!UICONTROL 마케팅 링크 빌더]**&#x200B;를 클릭하고 앱스토어를 iOS 장치의 대상으로 설정하는 획득 마케팅 링크 URL을 생성합니다.

   예:

   ```
   https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=57477650072932ec6d3a470f
   ```

   자세한 정보는 [마케팅 링크 빌더](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)를 참조하십시오.


1. iOS 기기에서 생성된 링크를 열고 `https://c00.adobe.com/v3/<appid>/end`를 엽니다.

   다음과 같이 JSON 응답에 contextData가 표시되어야 합니다.

   ```js
   {"fingerprint":"bae91bb778f0ad52e37f0892961d06ac6a5c935b","endCallbacks":["***"],"timestamp":1464301217,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData":
   {"a.launch.campaign.trackingcode":"twdf4546","a.referrer.campaign.name":"iOS Demo","a.referrer.campaign.trackingcode":"twdf4546"}
   ,"adobeData":{"unique_id":"8c14098d7c79e8a180c15e4b2403549d3cc21ea8","deeplinkid":"57477650072932ec6d3a470f"}}
   ```

1. 구성 파일에서 다음 설정이 올바른지 확인합니다.

   | 설정 | 값 |
   |--- |--- |
   | acquisition | 서버는 `c00.adobe.com`이어야 합니다.   `appid`는 획득 링크에서 *`appid`*&#x200B;와 같아야 합니다. |
   | analytics | `referrerTimeout` 값은 0보다 커야 합니다. |

1. (선택 사항) 앱 구성 파일의 SSL 설정이`false`일 경우 HTTPS 대신 HTTP 프로토콜을 사용하도록 획득 링크를 업데이트합니다.
1. 앱을 설치하려는 모바일 장치에서 생성된 링크를 클릭합니다.

   Adobe 서버(`c00.adobe.com`)는 지문 파일을 저장한 다음 앱스토어로 리디렉션합니다. 테스트를 위해 앱을 다운로드할 필요는 없습니다.
1. 6단계에서 사용한 것과 동일한 모바일 장치에서 처음으로 애플리케이션을 시작합니다.

   필요한 경우 앱을 삭제하고 다시 설치할 수 있습니다.
1. (선택 사항) SDK의 디버그 로깅을 사용하여 추가 정보를 얻습니다.

   모두 올바르게 작동하면 다음 로그가 표시됩니다.

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   이러한 로그가 표시되지 않으면 4~5단계를 완료했는지 확인하십시오.

   다음은 가능한 오류에 대한 정보입니다.

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`:

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

* 획득 서버는 링크 클릭(6단계) 및 앱 실행(7단계)에 기록된 IP 주소 및 사용자 에이전트 정보를 기반으로 속성 일치를 제공합니다.

   URL을 클릭할 때와 앱을 열 때 동일한 네트워크에 있어야 합니다.

* HTTP 모니터링 도구를 사용하면 앱에서 전송된 히트를 모니터링하여 획득 속성을 확인할 수 있습니다.

   획득 서버로 전송되는 `/v3/<appid>/start` 요청과 `/v3/<appid>/end` 요청이 각각 하나씩 표시됩니다.

* 전송된 사용자 에이전트의 변형으로 인해 속성 확인이 실패할 수 있습니다.

   `https://c00.adobe.com/v3/<appid>/start` 및 `https://c00.adobe.com/v3/<appid>/end`에 동일한 사용자 에이전트 값이 있는지 확인합니다.

* 획득 링크와 SDK의 히트는 동일한 HTTP/HTTPS 프로토콜을 사용해야 합니다.

   링크는 HTTP를 사용하고 SDK는 HTTPS를 사용하는 것과 같이 링크와 히트가 다른 프로토콜을 사용하는 경우 통신사에 따라 각 요청의 IP 주소가 다를 수 있습니다. 이로 인해 속성 확인이 실패할 수 있습니다.

* 마케팅 링크는 서버 측에 캐시되며 만료 시간은 10분입니다. 

   마케팅 링크를 변경할 경우 링크를 사용하기 전에 변경 사항이 적용되도록 10분 정도 기다려야 합니다.
