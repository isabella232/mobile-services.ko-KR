---
description: 다음은 ADBMobile.json 구성 파일을 사용하는 데 유용한 정보입니다.
seo-description: 다음은 ADBMobile.json 구성 파일을 사용하는 데 유용한 정보입니다.
seo-title: ADBMobile JSON 구성
solution: Marketing Cloud,Analytics
title: ADBMobile JSON 구성
topic: Developer and implementation
uuid: d9708d59-e30a-4f6c-ab1b-d9499855d0c2
translation-type: ht
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa
workflow-type: ht
source-wordcount: '1715'
ht-degree: 100%

---


# ADBMobile JSON 구성 {#adbmobile-json-config}

다음은 `ADBMobile.json` 구성 파일을 사용하는 데 유용한 정보입니다.

## ADBMobileConfig.json 구성 파일 참조 {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

여러 플랫폼에서 동일한 설정 파일을 앱에 사용할 수 있습니다.

>[!TIP]
>
>**iOS**&#x200B;에서 `ADBMobileConfig.json` 파일은 번들에서 액세스할 수 있는 모든 위치에 배치할 수 있습니다.

* **acquisition**

   모바일 앱 획득을 사용하도록 설정합니다.

   이 섹션이 없으면 모바일 앱 획득을 사용하도록 설정하고 SDK 구성 파일을 다시 다운로드하십시오. 자세한 내용은 아래의 *referrerTimeout*&#x200B;을 참조하십시오.

   * `server` - 처음 시작 시 획득 레퍼러가 확인된 획득 서버입니다.
   * `appid` - 획득 서버에서 이 앱을 고유하게 식별하는, 생성된 ID입니다.
   * 최소 SDK 버전: 4.1

* **analyticsForwardingEnabled**

   `audienceManager` 개체의 속성입니다. `Audience Manager`가 구성되어 있고 `analyticsForwardingEnabled`가 `true`로 설정된 경우 모든 Analytics 트래픽도 Audience Manager로 전달됩니다. 기본값은 `false`입니다.

   * 최소 SDK 버전: 4.8.0

* **backdateSessionInfo**

   세션 정보 히트를 소급 적용하는 Adobe SDK용 기능을 활성화하거나 비활성화합니다.

   세션 정보 히트는 현재 충돌 및 세션 길이로 구성되며 활성화하거나 비활성화할 수 있습니다.

   * 이 값을 `false`로 설정한 경우 히트가 **비활성화**&#x200B;됩니다. 

      SDK는 이전 세션에 대한 세션 정보와 후속 세션의 첫 번째 히트를 함께 묶는 이전 4.1 버전 동작으로 돌아갑니다. 또한 Adobe SDK는 세션 정보를 현재 라이프사이클에 첨부하므로 부풀려진 방문이 생성되지 않습니다. 부풀려진 방문이 더 이상 생성되지 않으므로 방문 횟수가 즉시 줄어듭니다.

   * 값을 제공하지 않은 경우 기본 값은 `true`이며 히트가 **활성화됩니다**.

      히트가 활성화되면 Adobe SDK는 이전 세션에서 최종 히트 후 세션 정보 히트를 1초로 소급 적용합니다. 다시 말해서, 충돌 및 세션 데이터가 충돌과 세션이 발생한 올바른 날짜와 상호 연결됩니다. 한 가지 부작용으로, SDK에서 오래된 히트에 대한 방문을 만들 수도 있습니다. 애플리케이션의 모든 새로운 시작 시 하나의 히트가 소급 적용됩니다.

   * 최소 SDK 버전: 4.6
   >[!IMPORTANT]
   >
   >오래된 세션 히트 정보는 세션 정보 서버 호출 시 전송되며, 추가 서버 호출이 적용될 수 있습니다.


* **batchLimit**

   연속적인 호출 시 전송할 히트 수에 대한 임계값입니다. 예를 들어 `batchLimit`이 10으로 설정되면 10번째 히트 전에 발생한 각 히트가 큐에 저장됩니다. 10번째 히트가 들어오면 10개의 히트가 모두 연속적으로 전송됩니다.

   * 기본값은 `0`이며, 이 경우 일괄 처리를 사용할 수 없습니다.
   * `offlineEnabled = true`가 필요합니다.
   * 최소 SDK 버전: 4.1

* **charset**

   Analytics로 전송되는 데이터에 사용하는 문자 세트를 정의합니다. charset은 들어오는 데이터를 저장 및 보고용으로 UTF-8로 변환하는 데 사용됩니다. 자세한 내용은 [s.charSet](https://docs.adobe.com/content/help/ko-KR/analytics/implementation/vars/config-vars/charset.html)을 참조하십시오.

   * 최소 SDK 버전: 4.0

* **clientCode**

   할당된 클라이언트 코드입니다.

   >[!IMPORTANT]
   >
   >이 변수는 Target에 필수입니다.

   * 최소 SDK 버전: 4.0

* **coopUnsafe**

   이 값을 `true` 로 설정해야 하는 Device Co-op 멤버의 경우, Device Co-op 계정에서 블랙리스트 플래그를 요청하려면 Co-op 팀과 작업해야 합니다. 이 플래그를 활성화하기 위한 셀프 서비스 경로가 없습니다.

   다음 정보를 숙지하십시오.

   * `coopUnsafe`가 `true`로 설정되면 `coop_unsafe=1`이 항상 Audience Manager 및 방문자 ID 히트에 추가됩니다.
   * Audience Manager에 Analytics 서버측 전달을 활성화하는 경우, Analytics 조회수에 `coop_unsafe=1`이 표시됩니다.
   다음은 몇 가지 추가 정보입니다.

   * 최소 SDK 버전: 4.16.1
   * `marketingCloud`로 설정된 경우 `true` 개체의 부울 속성으로 인해 장치가 Experience Cloud의 Device Co-Op에서 옵트아웃됩니다.
   * 기본값은 `false`입니다.
   * 이 설정은 Device Co-op 프로비저닝 고객&#x200B;**에게만** 사용됩니다.



* **environmentId**

   사용할 환경 ID입니다. 유효한 ID(`environmentId=8`)를 지정할 수 있으며, `environmentId`가 포함되지 않은 경우 기본 프로덕션 환경이 사용됩니다.

   * 최소 SDK 버전: 4.14

* **lifecycleTimeout**

   기본값은 300초입니다.

   앱 시작이 새로운 세션으로 간주되기 전에 다음 앱이 시작되기까지 경과해야 하는 시간(초)을 지정합니다. 이 시간 초과는 응용 프로그램이 백그라운드로 전송되고 다시 활성화될 때도 적용됩니다. 앱이 백그라운드에서 소요하는 시간은 세션 길이에 포함되지 않습니다.

   * 최소 SDK 버전: 4.0

* **messages**

   Adobe Mobile Services에서 자동으로 생성되며, 인앱 메시지의 설정을 정의합니다. 자세한 내용은 아래의 *메시지 설명* 섹션을 참조하십시오.

   * 최소 SDK 버전: 4.2

* **offlineEnabled**

   사용하도록 설정하면 히트는 장치가 오프라인일 때 큐에 있다가 나중에 장치가 온라인으로 전환될 때 전송됩니다. 오프라인 추적을 사용하려면 보고서 세트에 타임스탬프가 설정되어 있어야 합니다. 기본값은 `false`입니다.

   다음은 몇 가지 중요한 정보입니다.

   * 보고서 세트에서 타임스탬프가 활성화된 경우 `offlineEnabled` 구성 속성이 *true*&#x200B;이어야 합니다.
   * 보고서 세트에서 타임스탬프가 사용되지 않는 경우에는 `offlineEnabled` 구성 속성이 *반드시* false여야 합니다.

      이 속성이 제대로 구성되지 않으면 데이터가 손실됩니다. 보고서 세트 타임 스탬프 활성화 여부가 확실치 않으면  Customer Care에 문의하거나 Adobe Mobile Services에서 구성 파일을 다운로드하십시오. 현재 JavaScript의 데이터도 수집하는 보고서 세트에 AppMeasurement 데이터를 보고하는 경우, 모바일 데이터에 별도의 보고서 세트를 설정하거나 `s.timestamp` 변수를 사용하는 모든 JavaScript 히트에 사용자 지정 타임스탬프를 포함해야 할 수도 있습니다.

   * 최소 SDK 버전: 4.0

* **org**

   Adobe Experience Platform ID 서비스에 대한 Experience Cloud 조직 ID를 지정합니다.

   * 최소 SDK 버전: 4.3

* **poi**

   각 POI 배열에는 해당 지점의 POI 이름, 위도, 경도 및 반경(미터 단위)이 저장됩니다. POI 이름은 임의의 문자열일 수 있습니다. `trackLocation` 호출이 전송될 때 현재 좌표가 정의된 POI 내에 있는 경우 컨텍스트 데이터 변수를 채워 `trackLocation` 호출로 보냅니다.

   * 최소 SDK 버전: 4.0

   ```js
   "poi" [ 
           ["sanfrancisco",37.757144,-122.44812,7000]
           ["santacruz",36.972935,-122.01725,600]
         ] 
   ```

   >[!TIP]
   >
   >버전 4.2부터 POI는 Adobe Mobile 인터페이스에서 정의되며 앱 구성 파일과 동적으로 동기화됩니다. 이렇게 동기화되려면 `analytics.poi` 설정이 필요합니다.

   ```js
   “analytics.poi”: “`https://assets.adobedtm.com/…/yourfile.json`”,
   ```

   이 설정을 구성하지 않으면 이 행을 포함하도록 `ADBMobile.json` 파일을 업데이트해야 합니다. 업데이트된 구성 파일을 다운로드하려면 [시작하기 전에](/help/ios/getting-started/requirements.md)를 참조하십시오.

* **postback**

   &quot;콜백&quot; 메시지 템플릿에 대한 정의는 다음과 같습니다.

   ```js
   "payload":{
       "templateurl":"",//required- will be token-expanded prior to being sent
       "templatebody":"", //optional-if this length > 0 POST will be used as transport method. This is a base-64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"", //optional-if this is length > 0 and POST type is selected, this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout": 0 //optional-number of seconds to wait before timingout.Defaultis2.}
   ```

   코드에서 `payload` 개체는 `ADBMobileConfig.json` 파일에 적용할 메시지 정의에 대한 예제 페이로드입니다. 자세한 내용은 [포스트백](/help/ios/analytics-main/postback/postback.md)을 참조하십시오.

   * 최소 SDK 버전: 4.6

* **privacyDefault**

   * `optedin`의 경우 히트가 즉시 전송됩니다.
   * `optedout`의 경우 히트가 삭제됩니다.
   * `optunknown`의 경우 보고서 세트에 타임스탬프가 사용되면 개인정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트가 삭제됨)으로 변경될 때까지 히트가 저장됩니다.

      보고서 세트에 타임스탬프가 활성화되어 있지 않을 경우 개인정보 상태가 옵트인으로 변경될 때까지 히트가 삭제됩니다.

      초기값만 설정됩니다. 코드에서 이 값을 설정하거나 변경하고 나면 해당 값을 다시 변경하거나 앱을 제거하고 다시 설치할 때까지 새 값이 사용됩니다. 기본값은 `optedin`입니다.

   * 최소 SDK 버전: 4.0

* **referrerTimeout**

   SDK가 시간 초과 전까지 처음 시작 시 획득 레퍼러 데이터를 대기하는 시간(초)입니다. 획득을 사용 중인 경우 5초의 시간제한이 권장됩니다.

   >[!IMPORTANT]
   >
   >고객 확보의 경우 이 변수는 필수입니다. 이 변수를 `0`으로 설정하거나 이 변수를 포함하지 않는 경우 SDK는 획득 데이터를 기다리지 않고 획득 지표가 추적되지 않습니다.

   * 최소 SDK 버전: 4.1

* **remotes**

   동적 구성 파일에 대해 Adobe에서 호스팅되는 종단점을 정의합니다. 자동으로 구성됩니다. 각 구성 파일의 최종 업데이트 시간은 시작 시마다 현재 버전과 비교하여 확인되며, 해당 업데이트가 다운로드되어 저장됩니다.

   * `analytics.poi`: 호스팅된 POI 구성의 종단점입니다.

   * `messages`: 호스팅된 인앱 메시지 구성의 종단점입니다.

   * 최소 SDK 버전: 4.2

* **rsids**

   Analytics 데이터를 수신할 하나 이상의 보고서 세트입니다. 여러 보고서 세트 ID는 공백 없이 쉼표로 구분해야 합니다.

   ```js
   "rsids": "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2" 
   ```

   >[!IMPORTANT]
   >
   >Analytics의 경우 이 변수는 필수입니다.

   * 최소 SDK 버전: 4.0

* **server**

   Analytics 또는 고객 관리 서버로, 상위 노드를 기반으로 합니다.

   이 변수는 `https://` 또는 `https://` 프로토콜 접두사 없이 서버 도메인으로 채워야 합니다. 이 접두사는 라이브러리에서 자동으로 처리되며 `ssl` 변수를 기반으로 합니다.

   `ssl`이 `true`이면 이 서버에 보안 연결이 설정됩니다. `ssl`이 `false`이면 이 서버에 비보안 연결이 설정됩니다.

   >[!IMPORTANT]
   >
   >Analytics 및/또는 고객 관리의 경우 이 변수는 필수입니다.

   * 최소 SDK 버전: 4.0

* **ssl**

   >[!IMPORTANT]
   >
   > 버전 4.10.0부터는 플래그가 설정되지 않은 경우 SSL이 기본적으로 true로 설정됩니다.

   SSL(HTTPS)을 사용하여 측정 데이터를 전송하는 기능을 활성화(`true`)하거나 비활성화(`false`)합니다.

   &quot;콜백&quot; 메시지 템플릿에 대한 정의는 다음과 같습니다.

   ```js
   "payload":{
       "templateurl":"",//required-will be token-expanded prior to being sent
       "templatebody":"",//optional-if this length > 0, POST will be used as transport method. This is a base64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"",//optional-if this is length > 0 and POST type is selected this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout":0//optional-numberofsecondstowaitbeforetimingout.Defaultis2.} 
   ```

   코드에서 `payload` 개체는 `ADBMobileConfig.json` 파일에 적용할 메시지 정의에 대한 샘플 페이로드입니다. 자세한 내용은 [포스트백](/help/ios/analytics-main/postback/postback.md)을 참조하십시오.

   * 최소 SDK 버전: 4.0

* **timeout**

   Target이 응답을 기다리는 시간을 결정합니다.

   * 최소 SDK 버전: 4.0


## 샘플 `ADBMobileConfig.json` 파일 {#section_52FA7C71A99147AFA9BE08D2177D8DA7}

다음은 `ADBMobileConfig.json` 파일 샘플입니다.

```js
{ 
    "version": "2014-08-05T19:18:28.169Z", 
    "marketingCloud" : { 
        "org": "016D5C175213CCA80A490D05@AdobeOrg", 
        "coopUnsafe": false 
    }, 
    "target": { 
        "clientCode": "", 
        "timeout": 5, 
        "environmentId": 8 
    }, 
    "audienceManager": { 
        "server": "", 
        "analyticsForwardingEnabled": false 
    }, 
    "acquisition": { 
        "server": "c00.adobe.com", 
        "appid": "10a77a60192fbb628376e1b1daeeb65debf934e2c807e067ceb2963a41b165ee" 
    }, 
    "analytics": { 
        "rsids": "coolApp", 
        "server": "my.CoolApp.com", 
        "ssl": true, 
        "offlineEnabled": true, 
        "charset": "UTF-8", 
        "lifecycleTimeout": 300, 
        "privacyDefault": "optedin", 
        "batchLimit": 0, 
        "referrerTimeout": 5, 
        "poi": [ 
            ["san francisco",37.757144,-122.44812,7000],  
            ["santa cruz",36.972935,-122.01725,600] 
        ] 
    }, 
    "messages": [ 
        { 
            "messageId": "cb426565-a563-497a-a889-9dbeb451f8ae", 
            "template": "fullscreen", 
            "payload": { 
                 "html": "<!DOCTYPE html><html><head><meta charset=\"utf-8\" /><title></title><style></style></head><body><iframe src=\"https://www.adobe.com/\" frameborder=\"0\"></iframe></body></html>"
            },
            "showOffline": false,
            "showRule": "always",
            "endDate": 2524730400,
            "startDate": 0,
            "audiences": [],
            "triggers": [
                {
                    "key": "pev2",
                    "matches": "eq",
                    "values": [
                        "AMACTION:custom"
                    ] 
                } 
            ] 
        } 
    ], 
    "remotes": {
        "analytics.poi": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0faadc2f9ed92bc00003b.json",
        "messages": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0f9e2c2f9ed92bc000032.json"
    }
}
```

## 메시지 설명 {#section_B97D654BA92149CE91F525268D7AD71F}

메시지 노드는 Adobe Mobile Services에서 자동으로 생성되며, 일반적으로 수동으로 변경하지 않아도 됩니다. 다음 설명은 문제 해결 용도로 제공됩니다.

* &quot;messageId&quot;

   * 생성된 ID, 필수

* &quot;template&quot;

   * &quot;alert&quot;, &quot;fullscreen&quot; 또는 &quot;local&quot;
   * 필수

* &quot;payload&quot;

   * &quot;html&quot;

      * 전체 화면 템플릿 전용, 필수
      * 메시지를 정의하는 html
   * &quot;image&quot;

      * 전체 화면 전용, 선택 사항
      * 전체 화면 이미지에 사용할 이미지 URL
   * &quot;altImage&quot;

      * 전체 화면 전용, 선택 사항
      * 
         `image`에 지정된 URL에 연결할 수 없는 경우 번들 이미지의 이름
   * &quot;title&quot;

      * 전체 화면 및 경고, 필수
      * 전체 화면 또는 경고 메시지의 제목 텍스트
   * &quot;콘텐츠&quot;

      * 경고 및 로컬 알림, 필수
      * 경고 메시지의 하위 텍스트 또는 로컬 알림 메시지의 알림 텍스트
   * &quot;confirm&quot;

      * 경고, 선택 사항
      * 확인 단추에 사용되는 텍스트
   * &quot;cancel&quot;

      * 경고, 필수
      * 취소 단추에 사용되는 텍스트
   * &quot;url&quot;

      * 경고, 선택 사항
      * 확인 단추를 클릭하면 로드할 URL 작업
   * &quot;wait&quot;

      * 로컬 알림, 필수
      * 기준에 일치하는 항목을 찾은 후 로컬 알림 게시를 위해 대기하는 시간(초)









* &quot;showOffline&quot;

   * true 또는 false
   * 기본값은 false입니다.

* &quot;showRule&quot;

   * &quot;always&quot;, &quot;once&quot; 또는 &quot;untilClick&quot;
   * 필수

* &quot;endDate&quot;

   * 1970년 1월 1일 이후 시간(초)
   * 기본값은 2524730400입니다.

* &quot;startDate&quot;

   * 1970년 1월 1일 이후 시간(초)
   * 기본값은 0입니다.

* &quot;audiences&quot;

   메시지를 표시하는 방법을 정의하는 객체 배열입니다.

   * &quot;key&quot;

      히트에서 찾을 변수 이름 및 필수 필드입니다.

   * &quot;matches&quot;

      비교를 수행할 때 사용하는 선택기 유형:

      * eq = 같음
      * ne = 같지 않음
      * co = 포함
      * nc = 포함하지 않음
      * sw = 다음으로 시작
      * ew = 다음으로 끝남
      * ex = 존재
      * nx = 존재하지 않음
      * lt = 보다 작음
      * le = 보다 작거나 같음
      * gt = 보다 큼
      * ge = 보다 크거나 같음
   * &quot;values&quot;

      다음에서 이름이 지정된 변수의 값에 대해 일치시키는 데 사용되는 값의 배열입니다.

      * key
      * with the matcher type in
      * matches


* &quot;triggers&quot;

   대상과 동일하지만 대상 대신 다음과 같은 작업이 있습니다.

   * &quot;key&quot;
   * &quot;matches&quot;
   * &quot;values&quot;
