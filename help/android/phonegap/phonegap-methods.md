---
description: iOS PhoneGap 플러그인 메서드를 사용하여 다양한 작업을 완료할 수 있습니다.
keywords: Android; 라이브러리; 모바일; SDK
seo-description: iOS PhoneGap 플러그인 메서드를 사용하여 다양한 작업을 완료할 수 있습니다.
seo-title: Phonegap 플러그인 메서드
solution: Marketing Cloud, Analytics
title: Phonegap 플러그인 메서드
topic: 개발자 및 구현
uuid: bc 3 db 9 ce -81 b 7-45 ec -88 aa -6020 c 1 db 5 d 9 c
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# PhoneGap plug-in methods{#phonegap-plug-in-methods}

Android PhoneGap 플러그인 메서드를 사용하여 다양한 작업을 완료할 수 있습니다.

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```js
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## Configuration methods {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   현재 사용자의 개인 정보 상태를 반환합니다.

   사용 가능한 상태는 다음과 같습니다.

   * `ADB.optedIn`: 히트가 즉시 전송됩니다.
   * `ADB.optedOut`: 히트가 삭제됩니다.
   * `ADB.optUnknown`: 보고서 세트에 **** 타임스탬프가 활성화되어 있으면 개인 정보 상태가 옵트인 (히트 수) 로 변경될 때까지 히트가 저장됩니다 (히트가 무시됨). 보고서 세트에 타임스탬프가 활성화되어 있지 **않을** 경우 개인정보 상태가 옵트인으로 변경될 때까지 히트가 삭제됩니다.

      기본값은 `ADBMobileConfig.json` 파일에서 설정되어 있습니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      getPrivacyStatus(function (value) { myTempVal = value; }, function () {myTempVal = null;}); 
      ```

* **setPrivacyStatus**

   현재 사용자의 개인정보 상태를 `status`로 설정합니다.

   다음 상태 중 하나를 설정할 수 있습니다.

   * `ADB.optedIn`: 히트가 즉시 전송됩니다.
   * `ADB.optedOut`: 히트가 삭제됩니다.
   * `ADB.optUnknown`: 보고서 세트에 **** 타임스탬프가 활성화되어 있으면 개인 정보 상태가 옵트인 (히트 수) 로 변경될 때까지 히트가 저장됩니다 (히트가 무시됨). 보고서 세트에 타임스탬프가 활성화되어 있지 **않을** 경우 개인정보 상태가 옵트인으로 변경될 때까지 히트가 삭제됩니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.setPrivacyStatus('ADB.optedIn');
      ```

* **getLifetimeValue**

   현재 사용자의 수명 값을 반환합니다. 기본값은 0입니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.getLifetimeValue(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

* **setDebugLogging**

   Enables (`true`) or disables (`false`) viewing debug information. 기본적으로 이 변수는 `false`입니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   라이브러리 버전을 가져옵니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.getVersion(function (value) { versionNum = value }, function () { versionNum = 1.0;});
      ```

* **trackingIdentifier**

   자동 생성된 방문자 식별자를 반환합니다.

   이 식별자는 앱을 처음 실행될 때 생성되어 저장된 다음 그 이후부터 사용되는 앱별 고유 방문자 ID입니다. 이 ID는 앱 업그레이드 시에도 보존되며 앱을 제거하면 삭제됩니다.

   >[!TIP]
   >
   >앱 업그레이드가 Experience Cloud 3. x에서 4. x SDK로 업그레이드되는 경우 이전 방문자 ID (사용자 지정 또는 자동 생성) 가 검색하여 사용자 지정 사용자 식별자로 저장됩니다. 자세한 내용은 아래 `getUserIdentifier`을 참조하십시오. 이 ID는 SDK 업그레이드 시에도 방문자 데이터를 보존합니다.

   4.x SDK에 새로 설치하는 경우 사용자 식별자는 `null`이며 추적 식별자가 사용됩니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.trackingIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

* **getUserIdentifier**

   고객 사용자 ID가 설정된 경우 이 식별자를 반환하고 ID가 설정되지 않은 경우 `null`을 반환합니다. 기본값은 `null`입니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      getUserIdentifier(function(value) { myTempVal = value; }, function () { myTempVal = null; });
      ```

* **setUserIdentifier**

   사용자 식별자를 `identifier`로 설정합니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   푸시 알림용 장치 토큰을 설정합니다.

   ```java
   getUserIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; });
   ```

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.setPushIdentifier(pushIdentifier, success, fail);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.setPushIdentifier('test_push_identifier',function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **keepLifecycleSessionAlive**

   라이플사이클 세션의 환경 설정을 실행 유지로 설정합니다.

   >[!IMPORTANT]
   >
   >Calling `keepLifecycleSessionAlive` prevents your app from launching a new session the next time it is resumed from background. 이 메서드는 앱이 백그라운드 알림에 등록되어 있을 경우에만 사용해야만 합니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADB.keepLifecycleSessionAlive(); 
      ```

* **trackingSendQueuedHits**

   현재 일괄 처리 옵션과 상관없이 라이브러리에서 큐에 있는 모든 히트를 강제로 전송합니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   오프라인 큐에서 저장된 추적 호출 수를 가져오거나 설정합니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADB.trackingGetQueueSize(function (value) { myTempVal = value;}, function () { myTempVal = null;}); 
      ```

* **trackingClearQueue**

   오프라인 큐에서 모든 저장된 추적 호출을 제거합니다.

   >[!WARNING]
   >
   >대기열을 되돌릴 수 없으므로 큐를 수동으로 지울 때는 주의하십시오.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADB.trackingClearQueue(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

## PII methods {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectPII**

   PII 컬렉션 요청을 제출합니다.

   * 다음은 이 메서드에 대한 구문입니다.
   ```javascript
   ADB.collectPII(piiData,success, fail);
   ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success') },function (value) { alert('fail') ;});
      ```


## Tracking methods {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   Adobe 딥링크 클릭스루를 추적합니다.

   >[!TIP]
   >
   >라이프사이클 호출이 시작 이벤트인 경우 Adobe 링크 데이터가 추가되며, 그렇지 않으면 추가 호출이 전송됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```js
      ADB.trackAdobeDeepLink(deeplinkURL, success, fail); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function (value) { alert('success'); },function (value) { alert('fail') }); 
      ```

* **trackState**

   선택적 컨텍스트 데이터로 앱 상태를 추적합니다. States are the views that are available in your app, such as such as `home dashboard`, `app settings`, `cart`, and so on. 이 상태는 웹 사이트의 페이지와 유사하며 `trackState` 호출은 페이지 보기를 증가시킵니다.

   `cData`: 컨텍스트 데이터 호출을 위해 키 값 쌍을 포함한 JSON 개체. 

   * 다음은 이 메서드에 대한 구문입니다.

      ```js
      ADB.trackState(string stateName[,JSON cData]);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
        ADB.trackState("login&amp;nbsp;page"); 
      ```

      ```js
        ADB.trackState("login page", {"user":"john","remember":"true"});
      ```

* **trackAction**

   앱의 작업을 추적합니다. Actions include `logins`, `banner taps`, `feed subscriptions`, and other metrics that occur in your app and that you want to measure.

   * 다음은 이 메서드에 대한 구문입니다.

      ```js
      ADB.trackAction(string action[,JSON cData]); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
        ADB.trackAction("login");
      ```

      ```js
        ADB.trackAction("login", {"user":"john","remember":"true"}); 
      ```

* **trackLocation**

   현재 xy 좌표를 보냅니다. 또한 `ADBMobileConfig.json` 파일에서 정의된 관심 영역을 사용하여 매개변수로 제공된 위치가 POI 내에 있는지 파악합니다. 현재 좌표가 정의된 POI 내에 있을 경우 컨텍스트 데이터 변수를 채워 `trackLocation` 호출로 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.trackLocation(x, y[,JSON cData]); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.trackLocation('40.431596', '-111.893713'); 
      ```

* **trackLifetimeValueIncrease**

   사용자의 라이프타임 값에 `amount`를 추가합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSON cData]); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.trackLifetimeValueIncrease('10.01'); 
      ```

* **trackTimedActionStart**

   이름이 `action`인 시간 작업을 시작합니다.

   이미 시작한 작업에 대해 이 메서드를 호출하는 경우 이전 시간 제한 작업을 덮어씁니다.

   >[!TIP]
   >
   >이 호출은 히트를 전송하지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.trackTimedActionStart(action[,JSON cData]);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimedActionUpdate**

   Pass in `cData` to update the context data that is associated with the `action`&gt;.

   전달된 `cData`는 기존 작업 데이터에 추가되며 `action`에 대해 동일한 키가 이미 정의된 경우 데이터를 덮어씁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.trackTimedActionUpdate(String action[,JSON cData]);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.trackTimedActionUpdate("cartToCheckout",{'SampleContextDataKey3':'SampleContextDataVal3','SampleContextDataKey4':'SampleContextDataVal4'});
      ```

* **trackTimedActionEnd**

   시간 제한 작업을 종료합니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.trackTimedActionEnd("cartToCheckout"); 
      ```

* **trackingTimedActionExists**

   시간 작업이 진행 중인지 여부를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.trackingTimedActionExists(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

## Beacon methods {#section_F9500D6BD95348E08E283C02B657019D}

* **trackBeacon**

   사용자가 비콘 근접 위치에 들어오면 추적합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```js
      ADB.trackBeacon(uuid, major, minor, proximity, cData) 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADB.trackBeacon('2F234454-CF6D-4A0F-ADF2-F4911BA9FFA6', 1, 2, 
      ADB.beaconUnknown, {'hp':'hp_val','hp.company':'adobe'}
      ```

* **clearCurrentBeacon**

   사용자가 비콘 근접 위치를 벗어나면 비콘 데이터를 삭제합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```js
      ADB.clearCurrentBeacon(success, fail)
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADB.clearCurrentBeacon(); 
      ```

## Target methods {#section_8670140C5A3F455E887830AFFDF91D59}

* **targetLoadRequest**

   구성된 `Target` 서버에 요청을 보내고 오퍼의 문자열 값을 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.targetLoadRequest(success, fail, name, defaultContent, parameters);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.targetLoadRequest(function&nbsp;(value)
      {myTempVal = value }, function () { myTempVal = null;},'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   구성된 `Target` 서버에 요청을 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.targetLoadOrderConfirmRequest(success, fail name orderId, orderTotal, productPurchaseId, parameters); 
      ```

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.targetLoadRequest(function (value) { myTempVal = value }
      , function ()
      { myTempVal = null; } 
      , 'name' 'orderId' 'total', 'purchaseId',
      {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   공유 쿠키 저장소에서 `Target` 쿠키를 지웁니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.targetClearCookies(); 
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   `Target` 서비스 요청을 처리합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(
        success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters requestLocationParameters
        ); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters  (function () { alert('success'); }, function () { alert('fail'); }, ;'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}, {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'});
      ```

* **targetLoadRequestWithName**

   `Target` 서비스 요청을 처리합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.targetLoadRequestWithRequestName(success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.targetLoadRequestWithName(
      function (value){ // handle target success} ,
      function() { // handle target failure }, 
      "mboxName",
      "defaultContent",
      {"profileParameters":"profileParametervalues"}
      {"orderId" : "32FGJ4XK" , "orderTotal" : "123.33" , "purchasedProductIds":"[46,34]" }
      {"mboxParameters":"mboxParametersvalues"}
      );
      ```

* **targetSessionID**

   Target 서버가 이 방문자에 대해 반환한 `SessionID` 쿠키의 값을 가져옵니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.targetSessionID (success, fail); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.targetSessionID(function (value) { alert(value) },function (value){ alert('fail'); });  
      ```

* **targetPcID**

   `PcID` 서버가 이 방문자에 대해 반환한 `Target` 쿠키의 값을 가져옵니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.targetPcID (success, fail); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.targetPcID(function  (value) { alert(value) },function (value) { alert('fail'); });
      ```

* **targetSetThirdPartyID**

   Target에 대해 사용자 지정 방문자 ID를 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID, success, fail); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id' function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **targetThirdPartyID**

   Target에 대해 사용자 지정 방문자 ID를 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.targetThirdPartyID(success, fail);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
       ADB.targetThirdPartyID(function (value) { alert(value); },function (value) { alert('fail')__;});
      ```

## Acquisition methods {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   구성된 Target 서버에 요청을 보내고 오퍼의 문자열 값을 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.acquisitionCampaignStartForApp(appId, data, success, fail); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’});  
      ```

## Advertising identifier {#section_194607D101B047A19C51B19E176E1500}

In the main activity that is generated by Cordova, call `Config.submitAdvertisingIdentifierTask()` in the `onResume()` method. 자세한 내용은 [구성 방법을](/help/android/configuration/methods.md)참조하십시오.

## Audience Manager methods {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **audienceGetVisitorProfile**

   방문자의 프로필을 가져옵니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.audienceGetVisitorProfile(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.audienceGetVisitorProfile(function(value) { profile = value;}, function() { profile = null; }); 
      ```

* **audienceGetDpuuid**

   DPUUID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.audienceGetDpuuid(success fail);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.audienceGetDpuuid(function(value) { dpuuid = value;}, function(){dpuuid = null; }); 
      ```

* **audienceGetDpid**

   DPID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.audienceGetDpid(success, fail);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;}, function() {dpid =  null;}); 
      ```

* **audienceSetDpidAndDpuuid**

   DPID 및 DPUUID를 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid, dpuuid, success, fail); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’, function() {…}, function(){…};
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’); 
      ```

* **audienceSignalWithData**

   Audience Manager 서비스 요청을 처리합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.audienceSignalWithData(success, fail, data);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
       ADB.audienceSignalWithData(function() {}, function() {} {‘key1’: ’value1’ ‘key2’: ‘value2’}); 
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’: ’value1’, ‘key2’:‘value2’}); 
      ```

* **audienceReset**

   Audience Manager UUID를 삭제하고 현재 방문자 프로필을 삭제합니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.audienceReset();
      ```

## ID Service methods {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **visitorGetMarketingCloudId**

   ID 서비스에서 Experience Cloud ID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.visitorGetMarketingCloudId(success, fail); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.visitorGetMarketingCloudId(function (value) { mcid = value;},function (){ mcid = null;});
      ```

* **visitorSyncIdentifiers**

   제공된 식별자를 ID 서비스에 동기화합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.visitorSyncIdentifiers(identifiers, success, fail); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’: ‘value_id_1’});  
      ```

* **visitorSyncIdentifiersWithAuthenticationState**

   제공된 식별자를 ID 서비스에 동기화합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState
      (identifiers, authenticationState, success, fail); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'}, ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **visitorSyncIdentifierWithType**

   제공된 식별자를 ID 서비스에 동기화합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType, identifier authenticationState, success, fail); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type', 'test-identifier', ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success') },function (value) { alert('fail'); }); 
      ```

* **visitorAppendToURL**

   지정된 URL에 방문자 식별자를 추가합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
       ADB.visitorAppendToURL(urlToAppend, success, fail); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.visitorAppendToURL('test_visitor_url', function (value) alert(value);},'');
      ```

* **visitorGetIDs**

   Returns all `visitorID`s that have been synced.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.visitorGetIDs (success, fail);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.visitorGetIDs(function (value) { alert(value); },function (value) { alert('fail') ;}); 
      ```
