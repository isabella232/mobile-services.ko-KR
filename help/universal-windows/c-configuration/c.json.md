---
description: ADBMobile JSON 구성 파일을 사용하는 데 유용한 정보입니다.
seo-description: ADBMobile JSON 구성 파일을 사용하는 데 유용한 정보입니다.
seo-title: ADBMobileConfig.json 구성
solution: Marketing Cloud,Analytics
title: ADBMobileConfig.json 구성
topic: 개발자 및 구현
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# ADBMobileConfig.json 구성 파일 {#adbmobileconfig-json-config}

ADBMobile JSON 구성 파일을 사용하는 데 유용한 정보입니다.

현재 SDK는 Analytics, Target 및 Audience Manager을 포함하여 여러 Adobe Experience Cloud 솔루션을 지원합니다. 메서드에는 솔루션에 따라 접두사가 붙습니다. 구성 메서드는 "Config"로 시작합니다.

* **rsids**

   (**Required by Analytics**) One or more report suites to receive Analytics data. 여러 보고서 세트 ID는 공백 없이 쉼표로 구분해야 합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Analytics 및 Audience Management에 필요**). Analytics 또는 고객 관리 서버로, 상위 노드를 기반으로 합니다. This variable should be populated with the server domain, without an `"https://"` or `"https://"` protocol prefix. 프로토콜 접두사는 `ssl` 변수를 기반으로 하여 라이브러리에서 자동으로 처리합니다.

   `ssl`이 `true`이면 이 서버에 보안 연결이 설정됩니다. `ssl`이 `false`이면 이 서버에 비보안 연결이 설정됩니다.

* **charset**

   Analytics로 전송되는 데이터에 사용하는 문자 세트를 정의합니다. charset은 들어오는 데이터를 저장 및 보고용으로 UTF-8로 변환하는 데 사용됩니다. For more information, see [s.charSet](https://marketing.adobe.com/resources/help/en_US/sc/implement/charset.html).

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (`HTTPS`). 기본값은 `false`입니다.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. 오프라인 추적을 사용하려면 보고서 세트에 타임스탬프가 설정되어 있어야 합니다.

   If time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. if your report suite is not timestamp enabled, your `offlineEnabled` configuration property *must* be `false`.

   이 속성이 제대로 구성되지 않으면 데이터가 손실됩니다. 보고서 세트에 타임스탬프가 활성화되어 있는지 확실하지 않은 경우 고객 지원 센터에 문의하십시오. If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   기본값은 `false`입니다.

* **lifecycleTimeout**

   앱 시작이 새 세션으로 간주되기 전에 다음 앱이 시작되기까지 경과되어야 하는 시간(초)을 지정합니다. 이 시간 초과는 응용 프로그램이 백그라운드로 전송되고 다시 활성화될 때도 적용됩니다. 앱이 백그라운드에서 소요하는 시간은 세션 길이에 포함되지 않습니다.

   기본값은 300초입니다.

* **batchLimit**

   일괄 처리에서 히트를 보냅니다.

   For example, if set to `50`, hits are queued until 50 are stored, then all queued hits are sent. Requires `offlineEnabled=true`, and the default value is `0` (No batching).

* **privacyDefault**

   The options are:

   * `optedin` - 히트가 즉시 전송됩니다.
   * `optedout` - 히트가 무시됩니다.
   * `optunknown` - 보고서 세트에 타임스탬프가 사용되면 개인정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트가 삭제됨)으로 변경될 때까지 히트가 저장됩니다. 보고서 세트에 타임스탬프가 사용되지 않으면 개인정보 상태가 옵트인으로 변경될 때까지 히트가 삭제됩니다.

      이 경우 기본값만 설정됩니다. 이 값이 코드에서 설정되거나 변경되면 코드에 설정된 값은 로컬 스토리지에 저장되고 변경될 때까지 계속 사용되거나 앱이 제거된 다음 다시 설치됩니다.

      기본값은 `optedin`입니다.

* **poi**

   각 POI 배열에는 해당 지점의 POI 이름, 위도, 경도 및 반경(미터 단위)이 저장됩니다. POI 이름은 임의의 문자열일 수 있습니다. `trackLocation` 호출이 전송될 때 현재 좌표가 정의된 POI 내에 있는 경우 컨텍스트 데이터 변수를 채워 `trackLocation` 호출로 보냅니다.

   * 다음은 이 변수의 코드 샘플입니다.

      ```js
       "poi" [ 
                ["san francisco",37.757144,-122.44812,7000], 
                ["santa cruz",36.972935,-122.01725,600] 
             ]
      ```

* **clientCode**

   (**Required by Target**) Your assigned client code.

* **timeout**

   Target이 응답을 기다리는 시간을 결정합니다.

다음은 `ADBMobileConfig.json` 파일 예제입니다.

```js
{ 
    "version" : "1.0",
    "analytics" : {
        "rsids" : "coolApp",
        "server" : "my.CoolApp.com",
        "charset" : "UTF-8",
        "ssl" : true,
        "offlineEnabled" : true,
        "lifecycleTimeout" : 5,
        "privacyDefault" : "optedin",
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000],
                    ["santa cruz",36.972935,-122.01725,600]
                ]
    },
 "target" : {
  "clientCode" : "myTargetClientCode",
  "timeout" : 1
 },
 "audienceManager" : {
  "server" : "myServer.demdex.com"
 }
}
```
