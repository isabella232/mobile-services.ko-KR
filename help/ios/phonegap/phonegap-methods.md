---
description: iOS PhoneGap 플러그인 메서드를 사용하여 다양한 작업을 완료할 수 있습니다.
keywords: phonegap
seo-description: iOS PhoneGap 플러그인 메서드를 사용하여 다양한 작업을 완료할 수 있습니다.
seo-title: PhoneGap 플러그인 메서드
solution: Marketing Cloud,Analytics
title: PhoneGap 플러그인 메서드
topic: 개발자 및 구현
uuid: bd830fe5-804a-4d0a-bbb6-99a6d8da6a03
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# PhoneGap plug-in methods {#phonegap-plug-in-methods}

iOS PhoneGap 플러그인 메서드를 사용하여 다양한 작업을 완료할 수 있습니다.

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## Configuration methods {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   현재 사용자의 개인 정보 상태를 반환합니다. 사용 가능한 상태는 다음과 같습니다.

   * `ADB.optedIn`: 히트가 즉시 전송됩니다.
   * `ADB.optedOut`으로 설정되어 있는 경우 히트가 무시됩니다.
   * `ADB.optUnknown`보고서 세트에 타임스탬프가 활성화되어 있을 경우 개인정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트가 삭제됨)으로 변경될 때까지 히트가 저장됩니다. **** 보고서 세트에 타임스탬프가 활성화되어 있지 **않을** 경우 개인정보 상태가 옵트인으로 변경될 때까지 히트가 삭제됩니다.\
      기본값은 `ADBMobileConfig.json` 파일에서 설정되어 있습니다.

      * 다음은 이 메서드의 코드 샘플입니다.

         ```javascript
         getPrivacyStatus(function (value){myTempVal = value;},function(){myTempVal = null;});
         ```

* **setPrivacyStatus**

   현재 사용자의 개인정보 상태를 `status`로 설정합니다. 다음 상태 중 하나를 설정할 수 있습니다.
   * `ADB.optedIn`: 히트가 즉시 전송됩니다.
   * `ADB.optedOut`으로 설정되어 있는 경우 히트가 무시됩니다.
   * `ADB.optUnknown`****: 보고서 세트에 타임스탬프가 활성화되어 있을 경우 개인정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트가 삭제됨)으로 변경될 때까지 히트가 저장됩니다. 

      보고서 세트에 타임스탬프가 활성화되어 있지 **않을** 경우 개인정보 상태가 옵트인으로 변경될 때까지 히트가 삭제됩니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
        ADB.setPrivacyStatus('ADB.optedIn'); 
      ```

* **getLifetimeValue**

   현재 사용자의 수명 값을 반환합니다. 기본값은 0입니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      ADB.getLifetimeValue(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```

* **setDebugLogging**

   Enables (`true`) or disables (`false`) viewing debug information. 기본적으로 이 변수는 `false`입니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   라이브러리 버전을 가져옵니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      ADB.getVersion(function(value){versionNum = value;},function(){versionNum=1.0;}); 
      ```

* **trackingIdentifier**

   자동 생성된 방문자 식별자를 반환합니다. 이 식별자는 앱을 처음 실행될 때 생성되어 저장된 다음 그 이후부터 사용되는 앱별 고유 방문자 ID입니다. 이 ID는 앱 업그레이드 시에도 보존되며 앱을 제거하면 삭제됩니다.

   >[!TIP]
   >
   >If your app upgrades from the Experience Cloud 3.x to 4.x SDK, the previous visitor ID (custom or automatically generated) is retrieved and stored as the custom user identifier (see `getUserIdentifier` below). 이렇게 하면 SDK 업그레이드 시에도 방문자 데이터가 보존됩니다. For new installations on the 4.x SDK, the user identifier is `null`, and tracking identifier is used.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
       ADB.trackingIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **getUserIdentifier**

   사용자 지정 식별자가 설정된 경우 사용자 지정 사용자 식별자를 반환하고 사용자 지정 식별자가 설정되지 않은 경우 `null`을 반환합니다. 기본값은 `null`입니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      getUserIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **setUserIdentifier**

   사용자 식별자를 `identifier`로 설정합니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   푸시 알림용 장치 토큰을 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```javascript
      ADB.setPushIdentifier(pushIdentifier,success,fail);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      ADB.setPushIdentifier('test_push_identifier',function(value){alert('success');},function(value){alert('fail');
      ```

* **keepLifecycleSessionAlive**

   라이플사이클 세션의 환경 설정을 실행 유지로 설정합니다.

   >[!IMPORTANT]
   >
   >Calling `keepLifecycleSessionAlive` prevents your app from launching a new session the next time it is resumed from background. 이 메서드는 앱이 백그라운드 알림에 등록되어 있을 경우에만 사용해야만 합니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **trackingSendQueuedHits**

   현재 일괄 처리 옵션과 상관없이 라이브러리에서 큐에 있는 모든 히트를 강제로 전송합니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   오프라인 큐에서 저장된 추적 호출 수를 가져오거나 설정합니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      ADB.trackingGetQueueSize(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **trackingClearQueue**

   오프라인 큐에서 모든 저장된 추적 호출을 제거합니다.

   >[!CAUTION]
   >
   >되돌릴 수 없으므로 큐를 수동으로 지울 때는 주의하십시오.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      ADB.trackingClearQueue(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **keepLifecycleSessionAlive**

   구성 파일의 라이프사이클 세션 시간 제한 값과 상관없이 다음 번에 백그라운드에서 세션이 다시 시작할 때 새 세션이 시작하지 않아야 함을 SDK에 표시합니다.

   >[!IMPORTANT]
   >
   >중요: 이 메서드는 앱이 백그라운드에 있을 때 알림을 등록하는 앱에 사용하도록 만들었으며 앱이 백그라운드에 있을 때 실행하는 코드에서만 호출되어야 합니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **collectLifecycleData**

   SDK의 솔루션 전체에서 사용하기 위해 라이프사이클 데이터를 수집해야 함을 SDK에 표시합니다. For more information, see [Lifecycle metrics](/help/ios/metrics.md).

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      ADB.collectLifecycleData(); 
      ```


## PII methods {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectPII**

   PII 컬렉션 요청을 제출합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```javascript
      ADB.collectPII(piiData,success,fail); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success'); },function (value) { alert('fail'); });
      ```

## Tracking methods {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   Adobe 딥링크 클릭스루를 추적합니다.

   >[!TIP]
   >
   >If the Lifecycle call is a launch event, the Adobe Link data will be appended, otherwise an extra call will be sent.

   * 다음은 이 메서드에 대한 구문입니다.

      ```javascript
      ADB.trackAdobeDeepLink(deeplinkURL,success,fail);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackPushMessageClickthrough**

   푸시 메시지 클릭스루를 추적합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```javascrpt
      ADB.trackPushMessageClickthrough(userInfo,success,fail); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      ADB.trackPushMessageClickthrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackLocalNotificationClickThrough**

   로컬 알림 메시지의 클릭스루를 추적합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```javascript
      ADB.trackLocalNotificationClickThrough(userInfo,success,fail); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      ADB.trackLocalNotificationClickThrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackState**

   선택적 컨텍스트 데이터로 앱 상태를 추적합니다. States are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on. 이 상태는 웹 사이트의 페이지와 유사하며 `trackState` 호출은 페이지 보기를 증가시킵니다. cData는 컨텍스트 데이터로 전송할 키-값 쌍이 있는 JSON 개체입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```javascript
      ADB.trackState(stringstateName[,JSONcData]); 
      ```

   * Here are the code samples for this method:

      ```javascript
      ADB.trackState("loginpage");
      ```

      ```javascript
        ADB.trackState("loginpage",{"user":"john","remember":"true"});
      ```

* **trackAction**

   앱의 작업을 추적합니다. Actions are the things that happen in your app that you want to measure, include `logins`, `banner taps`, `feed subscriptions` and other metrics.

   * 다음은 이 메서드에 대한 구문입니다.

      ```javascript
      ADB.trackAction(stringaction[,JSONcData]);
      ```

   * Here are the code samples for this method:

      ```javascript
      ADB.trackAction("login");
      ```

      ```javascript
      ADB.trackAction("login",{"user":"john","remember":"true"})
      ```

* **trackActionFromBackground**

   백그라운드에서 발생된 작업을 추적합니다. 특정 시나리오에서 라이프사이클 이벤트의 시작을 억제합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```javascript
      ADB.trackActionFromBackground(stringaction[,JSONcData]); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      ADB.trackActionFromBackground("login");
      ```

      ```javascript
      ADB.trackActionFromBackground("login",{"user":"john","remember":"true"});
      ```

* **trackLocation**

   현재 x 및 y 좌표를 전송합니다. Also uses the points of interest that were defined in the `ADBMobileConfig.json` file to determine if the location provided as a parameter is within any of your POIs. 현재 좌표가 정의된 POI 내에 있을 경우 컨텍스트 데이터 변수를 채워 `trackLocation` 호출로 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```javascript
       ADB.trackLocation(x,y[,JSONcData]);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      ADB.trackLocation('40.431596','-111.893713');
      ```

* **trackLifetimeValueIncrease**

   사용자의 라이프타임 값에 `amount`를 추가합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSONcData]);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.trackLifetimeValueIncrease('10.01');
      ```

* **trackTimedActionStart**

   `action` 이름으로 시간 작업을 시작합니다.. 이미 시작한 작업에 대해 이 메서드를 호출하는 경우 이전 시간 제한 작업을 덮어씁니다.

   >[!TIP]
   >
   >이 호출은 히트를 전송하지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.trackTimedActionStart(action[,JSONcData]);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimedActionUpdate**

   `cData`를 전달하여 제공된 `action`과 연관된 컨텍스트 데이터를 업데이트합니다. 전달한 `cData`는 지정된 작업의 기존 데이터에 추가되며 `action`에 대해 동일한 키가 이미 정의된 경우 데이터를 덮어씁니다.

   >[!TIP]
   >
   >이 호출은 히트를 전송하지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.trackTimedActionUpdate(Stringaction[,JSONcData]);
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

   시간 제한 작업이 진행 중인지 여부를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.trackingTimedActionExists(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```


## Target methods {#section_C45D2FE54AE04EB5BD24D3508F8A3212}

* **targetLoadRequest**

   구성된 `Target` 서버에 요청을 보내고 오퍼의 문자열 값을 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.targetLoadRequest(success,fail,name,defaultContent,parameters); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.targetLoadRequest(function (value)
      {myTempVal = value;},function() {myTempVal = null;},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   구성된 Target 서버에 요청을 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.targetLoadOrderConfirmRequest(success,fail,name,orderId,orderTotal,productPurchaseId,parameters); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.targetLoadRequest(function(value){myTempVal=value;}
      ,function()
      {myTempVal = null; }
      ,'name','orderId','total','purchaseId'
      ,{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   공유 쿠키 저장소에서 Target 쿠키를 지웁니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.targetClearCookies();
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   Target 서비스 요청을 처리합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(success,fail,name,defaultContent,profileParameters,orderParameters,mboxParameters,requestLocationParameters
      ); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(function(){alert('success');},function(){alert('fail');},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadRequestWithName**

   Target 서비스 요청을 처리합니다.

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
      ADB.targetSessionID(success,fail); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
        ADB.targetSessionID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

* **targetPcID**

   Target 서버가 이 방문자에 대해 반환한 `PcID` 쿠키의 값을 가져옵니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.targetPcID(success,fail);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.targetPcID(function(value){alert(value);},function(value){alert('fail');});
      ```

* **targetSetThirdPartyID**

   Target에 대해 사용자 지정 방문자 ID를 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID,success,fail); 
      ```

   * Here is the code sample for this group:

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **targetThirdPartyID**

   Target에 대해 사용자 지정 방문자 ID를 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.targetThirdPartyID(success,fail); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.targetThirdPartyID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

## Acquisition methods {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   사용자가 링크를 클릭한 것처럼 개발자가 앱 획득 캠페인을 시작할 수 있도록 해줍니다. 이 메서드는 `SKStoreView`를 사용하여 작업하는 경우처럼, 획득 링크를 수동으로 만들고 직접 앱스토어 리디렉션을 처리하는 데 유용합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.acquisitionCampaignStartForApp(appId,data,success,fail); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.acquisitionCampaignStartForApp('0652024f-adcd-49f9-9bd7-2552a4564d2f',{'extraDataKey':'extraDataValue'},success,fail); 
      ```


## Advertising identifier {#section_194607D101B047A19C51B19E176E1500}

In the `AppDelegate` generated by Cordova, call `[ADBMobile setAdvertisingIdentifier:]` in the `application:didFinishLaunchingWithOptions:` delegate method. 자세한 내용은 구성 [방법을 참조하십시오](/help/ios/configuration/sdk-methods.md).

## Audience Manager methods {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **audienceGetVisitorProfile**

   방문자의 프로필을 가져옵니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.audienceGetVisitorProfile();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.audienceGetVisitorProfile(function(value){profile = value;},function(){profile = null;}); 
      ```

* **audienceGetDpuuid**

   DPUUID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.audienceGetDpuuid(success,fail);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
       ADB.audienceGetDpuuid(function(value){dpuuid=value;},function(){dpuuid=null;}); 
      ```

* **audienceGetDpid**

   DPID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
       ADB.audienceGetDpid(success,fail);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;},function(){dpid = null;}); 
      ```

* **audienceSetDpidAndDpuuid**

   DPID 및 DPUUID를 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid,dpuuid,success,fail);
      ```

   * Here are the code samples for this method:

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’,function(){…},function(){…});
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’);
      ```

* **audienceSignalWithData**

   Audience Manager 서비스 요청을 처리합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.audienceSignalWithData(success,fail,data);
      ```

   * Here are the code samples for this method:

      ```java
      ADB.audienceSignalWithData(function(){},function(){},{‘key1’:’value1’,‘key2’:‘value2’});
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’:’value1’,‘key2’:‘value2’}); 
      ```

* **audienceReset**

   Audience Manager UUID를 재설정하고 현재 방문자 프로필을 삭제합니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.audienceReset(); 
      ```

## ID Service methods {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **visitorGetMarketingCloudId**

   ID 서비스에서 Experience Cloud ID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.visitorGetMarketingCloudId(success,fail);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.visitorGetMarketingCloudId(function(value){mcid=value;},function(){mcid=null;}); 
      ```

* **visitorSyncIdentifiers**

   제공된 식별자를 ID 서비스에 동기화합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.visitorSyncIdentifiers(identifiers,success,fail);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’},function(){…},function(){…})) 
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:‘value_id_1’});
      ```

* **visitorSyncIdentifiersWithAuthenticationState**

   제공된 식별자를 방문자 ID 서비스에 동기화합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState(identifiers,authenticationState,success,fail); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'},ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');});
      ```

* **visitorSyncIdentifierWithType**

   제공된 식별자를 방문자 ID 서비스에 동기화합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType,identifier,authenticationState,success,fail); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type','test-identifier',ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **visitorAppendToURL**

   지정된 URL에 방문자 식별자를 추가합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.visitorAppendToURL(urlToAppend,success,fail);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.visitorAppendToURL('test_visitor_url',function(value){alert(value);},'');
      ```

* **visitorGetIDs**

   동기화된 모든 `visitorIDs`를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      ADB.visitorGetIDs(success,fail)
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADB.visitorGetIDs(function(value){alert(value);},function(value){alert('fail');}); 
      ```

