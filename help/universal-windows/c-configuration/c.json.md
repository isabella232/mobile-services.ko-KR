---
description: ADBMobile JSON 구성 파일을 사용하는 데 도움이 되는 정보입니다.
solution: Experience Cloud,Analytics
title: ADBMobileConfig.json 구성
topic-fix: Developer and implementation
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
exl-id: 57d50d30-651c-4943-835e-1cbce7467baf
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 39%

---

# ADBMobileConfig.json 구성 파일 {#adbmobileconfig-json-config}

ADBMobile JSON 구성 파일을 사용하는 데 도움이 되는 정보입니다.

현재 SDK는 Analytics, Target 및 Audience Manager 등 여러 Adobe Experience Cloud 솔루션을 지원합니다. 메서드에는 솔루션에 따라 접두사가 붙습니다. 구성 메서드 앞에는 &quot;Config&quot;가 붙습니다.

* **rsids**

   (**Analytics**&#x200B;에 필요) 하나 이상의 보고서 세트가 Analytics 데이터를 수신합니다. 여러 보고서 세트 ID는 공백 없이 쉼표로 구분해야 합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Analytics 및 Audience Management에 필요**). Analytics 또는 Audience Management 서버로, 상위 노드를 기반으로 합니다. 이 변수는 `"https://"` 또는 `"https://"` 프로토콜 접두사 없이 서버 도메인으로 채워야 합니다. 프로토콜 접두사는 `ssl` 변수를 기반으로 하여 라이브러리에서 자동으로 처리됩니다.

   `ssl`이 `true`이면 이 서버에 보안 연결이 설정됩니다. `ssl`이 `false`이면 이 서버에 비보안 연결이 설정됩니다.

* **charset**

   Analytics로 전송된 데이터에 사용할 문자 세트를 정의합니다. charset은 들어오는 데이터를 저장 및 보고용으로 UTF-8로 변환하는 데 사용됩니다. 자세한 내용은 Adobe Analytics 설명서에서 [charSet](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/charset.html) 변수를 참조하십시오.

* **ssl**

   SSL(`HTTPS`)을 통해 측정 데이터 전송을 활성화(`true`)하거나 비활성화(`false`)합니다. 기본값은 `false`입니다.

* **offlineEnabled**

   사용하도록 설정하면(`true`), 히트는 장치가 오프라인일 때 큐에 있다가 나중에 장치가 온라인 상태일 때 전송됩니다. 오프라인 추적을 사용하려면 보고서 세트에 타임스탬프가 설정되어 있어야 합니다.

   보고서 세트에서 타임스탬프가 활성화된 경우 `offlineEnabled` 구성 속성 *a2/>가 `true`여야 합니다.* 보고서 세트에서 타임스탬프가 사용되지 않는 경우에는 `offlineEnabled` 구성 속성 *a2/>가 `false`여야 합니다.*

   이 속성이 제대로 구성되지 않으면 데이터가 손실됩니다. 보고서 세트 타임스탬프 활성화 여부를 잘 모를 경우 고객 지원 센터에 문의하십시오. 현재 JavaScript의 데이터도 수집하는 보고서 세트에 AppMeasurement 데이터를 보고하는 경우, 모바일 데이터에 별도의 보고서 세트를 설정하거나 `s.timestamp` 변수를 사용하여 모든 JavaScript 히트에 사용자 지정 타임스탬프를 포함해야 할 수도 있습니다.

   기본값은 `false`입니다.

* **lifecycleTimeout**

   실행이 새로운 세션으로 간주되기 전에 앱 실행 사이에 경과해야 하는 시간(초)을 지정합니다. 이 시간 초과는 응용 프로그램이 백그라운드로 전송되고 다시 활성화될 때도 적용됩니다. 앱이 백그라운드에서 소요하는 시간은 세션 길이에 포함되지 않습니다.

   기본값은 300초입니다.

* **batchLimit**

   히트를 일괄로 보냅니다.

   예를 들어 `50` 로 설정하면 50이 저장될 때까지 히트는 큐에 있다가 모든 큐에 있는 히트가 전송됩니다. `offlineEnabled=true`이 필요하며, 기본값은 `0`(일괄 처리 없음)입니다.

* **privacyDefault**

   옵션은 다음과 같습니다.

   * `optedin` - 히트가 즉시 전송됩니다.
   * `optedout` - 히트가 삭제됩니다.
   * `optunknown` - 보고서 세트에 타임스탬프가 활성화되어 있을 경우 개인정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트 삭제)으로 변경될 때까지 히트가 저장됩니다. 보고서 세트에 타임스탬프가 활성화되어 있지 않을 경우 개인정보 상태가 옵트인으로 변경될 때까지 히트가 삭제됩니다.

      기본값은 설정됩니다. 코드에서 이 값을 설정하거나 변경한 경우 코드로 설정된 값은 로컬 저장소에 저장되고 변경될 때까지 사용되며 앱을 제거하고 다시 설치하기 전까지 사용됩니다.

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

   (**Target**&#x200B;에 필요) 지정된 클라이언트 코드입니다.

* **timeout**

   대상이 응답을 기다리는 시간을 결정합니다.

다음은 `ADBMobileConfig.json` 파일의 예입니다.

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
