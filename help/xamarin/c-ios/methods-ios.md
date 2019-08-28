---
description: Experience Cloud 솔루션 4.x SDK용 Xamarin 구성 요소에 대한 iOS 메서드입니다.
keywords: Xamarin
seo-description: Experience Cloud 솔루션 4.x SDK용 Xamarin 구성 요소에 대한 iOS 메서드입니다.
seo-title: iOS 메서드
solution: Marketing Cloud, 개발자
title: iOS 메서드
uuid: D 6 A 056 DB -80 C 1-44 D 0-970 F-C 961 AD 01 B 0 BC
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# iOS methods{#ios-methods}

Experience Cloud 솔루션 4.x SDK용 Xamarin 구성 요소에 대한 iOS 메서드입니다.

## Configuration methods {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **CollectLifecycleData**

   SDK의 솔루션 전체에서 사용하기 위해 라이프사이클 데이터를 수집해야 함을 SDK에 표시합니다. 자세한 내용은 [라이프사이클 지표](/help/ios/metrics.md)를 참조하십시오.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void CollectLifecycleData();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.CollectLifecycleData();
      ```

* **Debuglogging**

   현재 디버그 로깅 기본 설정을 반환합니다. 기본값은 `false`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static bool DebugLogging(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var debugEnabled = ADBMobile.DebugLogging();
      ```

* **SetDebugLogging**

   디버그 로깅 기본 설정을 활성화됨으로 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void SetDebugLogging(bool enabled); 
      
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.SetDebugLogging(true);
      
* **LifetimeValue**

   현재 사용자의 수명 값을 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static double LifetimeValue(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var lifetimeValue = ADBMobile.LifetimeValue(); 
      ```

* **PrivacyStatus**

   현재 사용자에 대한 개인 정보 상태의 열거 표현을 반환합니다.
   * `ADBMobilePrivacyStatus.OptIn` - 히트가 즉시 전송됩니다.
   * `ADBMobilePrivacyStatus.OptOut` - 히트는 무시됩니다.
   * ADBMobilePrivacyStatus.Unknown - 오프라인 추적이 활성화되면 개인 정보 상태가 옵트인(그런 다음 히트를 보냄) 또는 옵트아웃(그런 다음 히트가 무시됨)으로 변경될 때까지 히트가 저장됩니다. 오프라인 추적이 비활성화되면 개인 정보 상태가 옵트인으로 변경될 때까지 히트가 무시됩니다.
   The default value is set in the [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md).

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static ADBPrivacyStatus PrivacyStatus();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
       var privacyStatus = ADBMobile.PrivacyStatus(); 
      ```


* **SetPrivacyStatus**

   현재 사용자의 개인 정보 상태를 상태로 설정합니다. 다음 값 중 하나를 설정합니다.
   * `ADBMobilePrivacyStatus.OptIn` - 히트가 즉시 전송됩니다.
   * `ADBMobilePrivacyStatus.OptOut` - 히트는 무시됩니다.
   * `ADBMobilePrivacyStatus.Unknown` - 오프라인 추적이 활성화되면 개인 정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트 삭제)으로 변경될 때까지 히트가 저장됩니다. 오프라인 추적이 비활성화되면 개인 정보 상태가 옵트인으로 변경될 때까지 히트가 무시됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void SetPrivacyStatus(ADBPrivacyStatus status) 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.SetPrivacyStatus(ADBMobilePrivacyStatus.OptIn); 
      ```

* **UserIdentifier**

   사용자 지정 식별자가 설정된 경우 사용자 지정 사용자 식별자를 반환합니다. 사용자 지정 식별자가 설정되지 않은 경우 null을 반환합니다. 기본값은 `null`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static string UserIdentifier(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var userId = ADBMobile.UserIdentifier(); 
      ```

* **SetUserIdentifier**

   사용자 지정 식별자가 설정된 경우 사용자 지정 사용자 식별자를 반환합니다. 사용자 지정 식별자가 설정되지 않은 경우 null을 반환합니다. 기본값은 `null`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static string UserIdentifier();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.SetUserIdentifier ("customUserIdentifier”); 
      ```

* **GetVersion**

   라이브러리 버전을 가져옵니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static string Version();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var version = ADBMobile.Version();
      ```

* **KeepLifecycleSessionAlive(iOS만 해당)**

   구성 파일의 라이프사이클 세션 시간 제한 값과 상관없이 다음 번에 백그라운드에서 세션이 다시 시작할 때 새 세션이 시작하지 않아야 함을 SDK에 표시합니다.

   >[!TIP]
   >
   >이 메서드는 백그라운드에 있는 동안 알림을 등록하는 앱에 사용하기 위해 만들었으며 앱이 백그라운드에 있을 때 실행하는 코드에서만 호출되어야 합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
       public static void KeepLifecycleSessionAlive();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.KeepLifecycleSessionAlive();
      ```

## Analytics methods {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   분석 추적 식별자를 검색합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static string TrackingIdentifier();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
       var trackingId = ADBMobile.TrackingIdentifier();
      ```

* **TrackState**

   선택적 컨텍스트 데이터로 앱 상태를 추적합니다. 상태는 "제목 화면", "레벨 1", "일시 중지" 등 앱에서 사용할 수 있는 보기입니다. 이러한 상태는 웹 사이트의 페이지와 유사하며 증분 페이지 보기를 `TrackState` 호출합니다. 상태가 비어 있으면 보고서에 "앱 이름 앱 버전 (빌드)" 로 표시됩니다. 보고서에서 이 값이 표시되면 반드시 각각의 `TrackState` 호출에서 상태를 설정해야 합니다.

   [!TIP]
   >페이지 보기를 증가시키는 유일한 추적 호출입니다.
   >
   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void TrackState(string state, NSDictionary cdata); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSDictionary contextData; 
       contextData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val"),NSObject.FromObject("key")); 
        ADBMobile.TrackState("title screen", contextData); 
      ```

* **TrackAction**

   앱의 작업을 추적합니다. 작업은 "예기치 못한 종료", "획득 레벨", "피드 구독" 및 기타 지표 등 측정하려는 앱에서 발생하는 일을 의미합니다.

   >[!TIP]
   If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void TrackAction(string action, NSDictionary cdata); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.TrackAction("level gained", null); 
      ```

* **TrackActionFromBackground(iOS만 해당)**

   백그라운드에서 발생된 작업을 추적합니다. 특정 시나리오에서 라이프사이클 이벤트의 시작을 억제합니다.

   >[!TIP]
   앱이 백그라운드에 있을 때 실행하는 코드에서만 이 메서드를 호출해야 합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void TrackActionFromBackground(string action, NSDictionary cdata); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   현재 위도 및 경도 좌표를 보냅니다. 또한 `ADBMobileConfig.json` 파일에서 정의된 관심 영역을 사용하여 매개변수로 제공된 위치가 POI 내에 있는지 파악합니다. 현재 좌표가 정의된 POI 내에 있을 경우 컨텍스트 데이터 변수를 채워 `TrackLocation` 호출로 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void TrackLocation(CLLocation location, NSDictionary cdata); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      CoreLocation.CLLocation l = new CoreLocation.CLLocation  (111.111, 44.156);
      ADBMobile.TrackLocation (l, null);
      ```

* **TrackBeacon**

   사용자가 비콘 근접 위치에 들어오면 추적합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void TrackBeacon( CLBeacon beacon, NSDictionary cdata);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      CoreLocation.CLBeacon beacon = new CoreLocation.CLBeacon (); 
      ADBMobile.TrackBeacon (beacon, null);
      ```

* **TrackingClearCurrentBeacon**

   사용자가 비콘 근접 위치를 떠난 후 비콘 데이터를 지웁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void TrackingClearCurrentBeacon();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   사용자의 라이프타임 값에 양을 추가합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      공개 nbsp; static void tracklifetimevalueincrease (double amount, nsdictionary CDATA);

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.TrackLifetimeValueIncrease(5, null); 
      ```

* **TrackTimedActionStart**

   이름 작업으로 시간 제한 작업을 시작합니다. 이미 시작한 작업에 대해 이 메서드를 호출하는 경우 이전 시간 제한 작업을 덮어씁니다.

   >[!TIP]
   이 호출은 히트를 전송하지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void TrackTimedActionStart(string action, NSDictionary cdata); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   주어진 작업과 연관된 컨텍스트 데이터를 업데이트하기 위해 데이터를 전달합니다. 전달한 데이터는 주어진 작업의 기존 데이터에 추가되며 작업에 대해 동일한 키가 이미 정의된 경우 데이터를 덮어씁니다.

   >[!TIP]
   이 호출은 히트를 전송하지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void TrackTimedActionUpdate(string action, NSDictionary cdata); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSDictionary updatedData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val2"), NSObject.FromObject ("key2")); 
        ADBMobile.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   시간 제한 작업을 종료합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void TrackTimedActionEnd(string action, Func<double, double, NSMutableDictionary, sbyte> block); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("level2", (double  arg1,  double  arg2,  NSMutableDictionary  arg3)  =>  { 
      return  Convert.ToSByte(true); 
      }); 
      
* **TrackingTimedActionExists**

   Timed Action 이 진행 중 (또는 진행 중) 인지를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static bool TrackingTimedActionExists(string action); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("timedAction",  (double  inAppDuration, 
      double  totalDuration,  NSMutableDictionary  data)  =>  { 
                   return  true; 
      });
      ```

* **TrackingSendQueuedHits**

   현재 큐에 올라가 있는 히트 개수와 상관없이 라이브러리에서 오프라인 큐의 모든 히트를 강제로 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void TrackingSendQueuedHits();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.TrackingSendQueuedHits(); 
      ```

* **TrackingClearQueue**

   오프라인 큐에서 모든 히트를 지웁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void TrackingClearQueue(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
       ADBMobile.TrackingClearQueue();
      ```

* **TrackingGetQueueSize**

   현재 오프라인 큐에 올라가 있는 히트 수를 검색합니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      public static int TrackingGetQueueSize();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var queueSize = ADBMobile.TrackingGetQueueSize(); 
      ```

## Experience Cloud ID methods {#section_157919E46030443DBB5CED60D656AD9F}

* **GetMarketingCloudID**

   ID 서비스에서 Experience Cloud ID를 검색합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static string GetMarketingCloudID(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   Experience Cloud ID를 사용하면 각 방문자에 연결할 추가 고객 ID를 설정할 수 있습니다. 방문자 API는 여러 다른 고객 ID의 범위를 구분하기 위해 동일한 방문자의 여러 고객 ID와 고객 유형 식별자를 수락합니다. 이 메서드는 JavaScript 라이브러리의 setCustomerID에 해당합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void VisitorSyncIdentifiers(NSDictionary identifiers);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
       NSDictionary  ids  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("pushID")); 
       ADBMobile.VisitorSyncIdentifiers(ids); 
      ```

## Target methods {#section_C1E4121CAF9D43538511D857A1F549A7}

* **TargetLoadRequest**

   Sends request to your configured Target server and returns the string value of the offer generated in a `Action<NSDictionary>` callback.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void TargetLoadRequest (ADBTargetLocationRequest request, Action<NSString> callback); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
       NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
       ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
       ADBMobile.TargetLoadRequest(req,    (context)  =>  { 
       Console.WriteLine  (context); 
       });
      ```

* **TargetCreateRequest**

   주어진 매개 변수로 `ADBTargetLocationRequest` 개체를 만드는 편의 생성자입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
      ```

* **TargetCreateOrderConfirmRequest**

   를 만듭니다 `ADBTargetLocationRequest`.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters);
      
   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.TargetCreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **TargetClearCookies**

   앱에서 모든 타겟 쿠키를 지웁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void TargetClearCookies(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.TargetClearCookies(); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **AudienceVisitorProfile**

   가장 최근 획득한 방문자 프로필을 반환합니다. 아직 어떤 신호도 제출되지 않은 경우 nil을 반환합니다. 방문자 프로필은 앱이 여러 번 시작되는 경우에도 쉽게 액세스할 수 있도록 `NSUserDefaults`에 저장됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static NSDictionary AudienceVisitorProfile (); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSDictionary profile = ADBMobile.AudienceVisitorProfile();
      ```

* **AudienceDpid**

   현재 DPID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static string AudienceDpid ();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      string currentDpid = ADBMobile.AudienceDpid();
      ```

* **AudienceDpuuid**

   현재 DPUUID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static string AudienceDpuuid ();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      string currentDpuuid = ADBMobile.AudienceDpuuid(); 
      ```

* **AudienceSetDpidAndDpuuid**

   dpid 및 dpuuid를 설정합니다. dpid 및 dpuuid가 설정되면 각 신호와 함께 전송됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void AudienceSetDpidAndDpuuid (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.AudienceSetDpidAndDpuuid ("testDppid", "testDpuuid")
      ```

* **AudienceSignalWithData**

   Sends audience management a signal with traits and get the matching segments returned in a `Action<NSDictionary>`  callback.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void AudienceSignalWithData (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSDictionary  audienceData  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBMobile.AudienceSignalWithData  (audienceData,  (context)  =>  { 
      Console.WriteLine  (context); 
      }); 
      ```

* **AudienceReset**

   Audience Manager UUID를 재설정하고 현재 방문자 프로필을 삭제합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void AudienceReset ();
      ```

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      ADBMobile.AudienceReset ();
      ```

## 비디오 {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

자세한 내용은 [비디오 분석](/help/ios/getting-started/dev-qs.md)을 참조하십시오.

* **MediaCreateSettings**

   지정된 매개 변수와 함께 `ADBMediaSettings` 개체를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static ADBMediaSettings MediaCreateSettings ([string name, double length, string playerName, string playerID); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings ("name1", 10, "playerName1", "playerID1"); 
      ```

* **MediaAdCreateSettings**

   광고 비디오 추적에 사용할 `ADBMediaSettings` 개체를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static ADBMediaSettings MediaAdCreateSettings ( string name,  double length,  string playerName,  string parentName,  string parentPod,  double parentPodPosition,  string CPM); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMediaSettings adSettings = ADBMobile.MediaAdCreateSettings("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1");
      ```

* **MediaOpenWithSettings**

   추적을 위해 `ADBMediaSettings` 개체를 엽니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void MediaOpenWithSettings ( ADBMediaSettings settings,  Action<ADBMediaState> callback); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings  ("name1",  10,  "playerName1",  "playerID1"); 
      ADBMobile.MediaOpenWithSettings  (settings,  (state)  =>  { 
      Console.WriteLine  (state.Name); 
      }); 
      ```

* **MediaClose**

   이름이 명명된 미디어 항목을 닫습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void MediaClose ( string name);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.MediaClose  (settings.Name);
      ```

* **MediaPlay**

   제공된 오프셋(초)에서 이름이 명명된 미디어 항목을 재생합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void MediaPlay ( string name, double offset);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.MediaPlay (settings.Name, 0); 
      ```

* **MediaComplete**

   제공된 오프셋(초)에서 완료된 미디어 항목을 수동으로 표시합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void MediaComplete ( string name, double offset);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMobile.MediaComplete (settings.Name, 5);
      ```

* **MediaStop**

   제공된 오프셋에서 비디오가 중지 또는 일시 중지되었음을 미디어 모듈에 알립니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void MediaStop ( string name, double offset);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
       ADBMobile.MediaStop (settings.Name, 3);
      ```

* **MediaClick**

   미디어 항목이 클릭되었음을 미디어 모듈에 알립니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void MediaClick ( string name, double offset); 
      ```

* **MediaTrack**

   현재 미디어 상태에 대한 추적 작업 호출(페이지 보기 없음)을 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      public static void MediaTrack ( string name, NSDictionary data); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
       ADBMobile.MediaTrack (settings.Name, null);
      ```
