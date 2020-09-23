---
description: Experience Cloud 솔루션 4.x SDK용 Xamarin 구성 요소에 대한 Android 메서드입니다.
keywords: Xamarin
seo-description: Experience Cloud 솔루션 4.x SDK용 Xamarin 구성 요소에 대한 Android 메서드입니다.
seo-title: Android 메서드
solution: Experience Cloud
title: Android 메서드
uuid: 860af1c4-f57e-4bcb-8308-4e316da9a27b
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1767'
ht-degree: 67%

---


# Android 메서드{#android-methods}

Experience Cloud 솔루션 4.x SDK용 Xamarin 구성 요소에 대한 Android 메서드입니다.

## 구성 메서드 {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **디버그 로깅**

   현재 디버그 로깅 기본 설정을 반환하며 기본값은 false입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static Boolean DebugLogging;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      getter: var debuglog = Config.DebugLogging;
      setter: Config.DebugLogging = (Java.Lang.Boolean)true;
      ```

* **라이프타임 값**

   현재 사용자의 수명 값을 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static BigDecimal LifetimeValue; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
       var lifetimeValue = Config.LifetimeValue;
      ```

* **개인 정보 상태**

   현재 사용자에 대한 개인 정보 상태의 열거 표현을 반환합니다.
   * `ADBMobilePrivacyStatus.OptIn` - 히트가 즉시 전송됩니다.
   * `ADBMobilePrivacyStatus.OptOut` - 히트가 삭제됩니다.
   * `ADBMobilePrivacyStatus.Unknown` - 오프라인 추적이 활성화되면 개인 정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트 삭제)으로 변경될 때까지 히트가 저장됩니다. 오프라인 추적이 비활성화되면 개인 정보 상태가 옵트인으로 변경될 때까지 히트가 무시됩니다.

   The default value is set in the [ADBMobileConfig.json](/help/android/configuration/json-config/json-config.md) file.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static MobilePrivacyStatus PrivacyStatus; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      getter: var privacyStatus = Config.PrivacyStatus; 
      setter: Config.PrivacyStatus = MobilePrivacyStatus.MobilePrivacyStatusUnknown;
      ```


* **사용자 식별자**

   사용자 지정 식별자가 설정된 경우 이 식별자를 반환합니다. 사용자 지정 식별자가 설정되지 않은 경우 null을 반환합니다. 기본값은 `null`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static UserIdentifier();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      getter: var userId = Config.UserIdentifier;
      setter: Config.UserIdentifier = "imBatman";
      ```

* **버전**

   라이브러리 버전을 가져옵니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static string Version;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      var version = ADBMobile.Version;
      ```

* **PauseCollectingLifecycleData**

   라이프사이클 지표를 정확히 계산하기 위해 앱이 일시 중지되었음을 SDK에 표시합니다. 예를 들어 일시 중지 시 타임스탬프를 수집하여 이전 세션 길이를 결정합니다. 또한 앱이 충돌하지 않았음을 라이프사이클에서 정확히 알 수 있도록 플래그를 설정합니다. 자세한 내용은 [라이프사이클 지표](/help/android/metrics.md)를 참조하십시오.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void PauseCollectingLifecycleData (); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Config.PauseCollectingLifecycleData();
      ```

* **CollectLifecycleData(활동)**

   (4.2 이상 버전) SDK의 모든 솔루션에서 사용하기 위해 라이프사이클 데이터를 수집해야 함을 SDK에 표시합니다. 자세한 내용은 [라이프사이클 지표](/help/android/metrics.md)를 참조하십시오.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void collectLifecycleData(Activity activity); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Config.CollectLifecycleData (this);
      ```

* **CollectLifecycleData(활동)**

   (4.2 이상 버전) SDK의 모든 솔루션에서 사용하기 위해 라이프사이클 데이터를 수집해야 함을 SDK에 표시합니다. 자세한 내용은 [라이프사이클 지표](/help/android/metrics.md)를 참조하십시오.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void collectLifecycleData(Activity activity, IDictionary<string, Object> context));
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      IDictionary<string, Java.Lang.Object> context = new Dictionary<string, 
      Java.Lang.Object> ();
      context.Add ("key", "value");
      Config.CollectLifecycleData (this, context);
      ```

* **OverrideConfigStream**

   (4.2 or later) Lets you load a different `ADBMobile JSON` config file when the application starts. 애플리케이션이 닫힐 때까지 다른 구성을 사용합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void OverrideConfigStream (Stream stream);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Stream st1 = Assets.Open ("ADBMobileConfig-2.json"); 
      Config.OverrideConfigStream (st1); 
      ```

* **SetLargeIconResourceId(int resourceId)**

   (4.2 이상 버전) SDK에서 만든 알림에 사용되는 큰 아이콘을 설정합니다. 이 아이콘이 사용자가 알림 센터에서 전체 알림을 볼 때 표시되는 기본 이미지입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void SetLargeIconResourceId( int resourceId);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Config.SetLargeIconResourceId(R.drawable.appIcon);
      ```

* **SetSmallIconResourceId(int resourceId)**

   (4.2 이상 버전) SDK에서 만든 알림에 사용되는 작은 아이콘을 설정합니다. 이 아이콘은 상태 표시줄에 표시되고 사용자가 알림 센터에서 전체 알림을 볼 때 표시되는 보조 이미지입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void SetSmallIconResourceId( int resourceId); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
       Config.SetSmallIconResourceId(R.drawable.appIcon);
      ```

## Analytics 메서드 {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   Analytics에 대해 자동으로 생성된 ID를 반환합니다. 이 ID는 처음 실행 시 생성되며 이 때부터 저장되고 사용됩니다. 이 ID는 앱 업그레이드 간에 유지되며 제거 시 제거됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static string TrackingIdentifier;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Var trackingId = Analytics.TrackingIdentifier
      ```

* **TrackState**

   선택적 컨텍스트 데이터로 앱 상태를 추적합니다. `States` 는 &quot;제목 화면&quot;, &quot;레벨 1&quot;, &quot;일시 중지&quot; 등과 같이 앱에서 사용할 수 있는 보기입니다. 이 상태는 웹 사이트의 페이지와 유사하며 `TrackState` 호출은 페이지 보기를 증가시킵니다. 상태가 비어 있으면 보고서에 &quot;앱 이름 앱 버전(빌드)&quot;로 표시됩니다. If you see this value in reports, make sure you are setting state in each `TrackState` call.

   >[!TIP]
   >
   >페이지 보기 횟수를 늘리는 유일한 추적 호출입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackState (string state, IDictionary<string, Object> cdata); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object>(); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackState ("stateName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackAction**

   앱의 작업을 추적합니다. 작업은 &quot;죽음&quot;, &quot;획득 레벨&quot;, &quot;피드 구독&quot; 및 기타 지표 등 측정하려는 앱에서 발생하는 일들입니다.

   >[!TIP]
   >
   >
   >백그라운드에 앱이 있을 때 실행할 수 있는 코드가 있는 경우(예: 백그라운드 데이터 검색) `trackActionFromBackground`를 대신 사용합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackAction(string action, IDictionary<string,Object> cdata); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value");
      Analytics.TrackAction ("actionName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackLocation**

   현재 위도 및 경도 좌표를 보냅니다. Also uses points of interest defined in the `ADBMobileConfig.json` file to determine whether the location that was provided as a parameter is in any of your POIs. 정의된 POI 내에 현재 좌표가 있는 경우 컨텍스트 데이터 변수를 채워 `TrackLocation` 호출로 전송합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackLocation(Location location, IDictionary<string, Object> cdata); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
       Location loc = new Location(LocationManager.GpsProvider);;
       loc.Latitude = 111; 
       loc.Longitude = 44; 
       loc.Accuracy = 5; 
       Analytics.TrackLocation (loc, null);
      ```

* **TrackBeacon**

   사용자가 비콘 근접 위치에 들어오면 추적합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackBeacon (string uuid, string major, string minor,  Analytics.BEACON_PROXIMITY prox, IDictionary<string, Object> cdata); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.TrackBeacon ("UUID", "1", "2", 
      Analytics.BEACON_PROXIMITY.ProximityImmediate, null); 
      ```

* **ClearBeacon**

   사용자가 비콘 근접 위치를 떠난 후 비콘 데이터를 지웁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackingClearCurrentBeacon();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.ClearBeacon(); 
      ```

* **TrackLifetimeValueIncrease**

   사용자의 라이프타임 값에 양을 추가합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackLifetimeValueIncrease (double amount, IDictionary<string,Object> cdata); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.TrackLifetimeValueIncrease(5,null);
      ```

* **TrackTimedActionStart**

   이름 작업으로 시간 제한 작업을 시작합니다. 이미 시작한 작업에 대해 이 메서드를 호출하는 경우 이전 시간 제한 작업을 덮어씁니다.

   >[!TIP]
   >
   > 이 호출은 히트를 전송하지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackTimedActionStart(string action,IDictionary<string, Object> cdata); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   데이터를 전달하여 지정된 작업과 관련된 컨텍스트 데이터를 업데이트합니다. 전달된 데이터는 주어진 작업의 기존 데이터에 추가되며 작업에 대해 동일한 키가 이미 정의된 경우 데이터를 덮어씁니다.

   >[!TIP]
   >
   >이 호출은 히트를 전송하지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackTimedActionUpdate(string action, IDictionary<string, Object> cdata); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      var updatedData = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   시간 제한 작업을 종료합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackTimedActionEnd(string action,
        Analytics.ITimedActionBlock block);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.TrackTimedActionEnd ("level2", new TimedActionBlock()); 
           class TimedActionBlock: Java.Lang.Object, 
      Analytics.ITimedActionBlock{ 
           public Java.Lang.Object Call (long inAppDuration, long 
      totalDuration IDictionary<string, Java.Lang.Object> contextData){ 
           return Java.Lang.Boolean.True; 
        } 
      }
      ```

* **TrackingTimedActionExists**

   시간 작업이 진행 중인지 여부를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static bool TrackingTimedActionExists(string action); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      var level2InProgress = Analytics.TrackingTimedActionExists("level2"); 
      ```

* **SendQueuedHits**

   현재 큐에 있는 히트 수에 관계없이 라이브러리가 오프라인 큐의 모든 히트를 강제로 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void SendQueuedHits();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.SendQueuedHits(); 
      ```

* **ClearQueue**

   오프라인 큐에서 모든 히트를 지웁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void ClearQueue(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.ClearQueue(); 
      ```

* **QueueSize**

   현재 오프라인 큐에 있는 히트 수를 검색합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static long QueueSize(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      var queueSize = Analytics.QueueSize();
      ```

## Experience Cloud ID methods {#section_157919E46030443DBB5CED60D656AD9F}

* **MarketingCloudId**

   ID 서비스에서 Experience Cloud ID를 검색합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static string MarketingCloudId;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      var mcid = Visitor.MarketingCloudId;
      ```

* **SyncIdentifiers**

   Experience Cloud ID를 사용하여 각 방문자와 연결할 추가 고객 ID를 설정할 수 있습니다. 방문자 API는 여러 다른 고객 ID의 범위를 구분하기 위해 동일한 방문자의 여러 고객 ID와 고객 유형 식별자를 수락합니다. 이 메서드는 JavaScript 라이브러리의 `setCustomerIDs`에 해당합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void SyncIdentifiers((IDictionary<string> identifiers);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      IDictionary<string,string> ids = new Dictionary<string, string> ();
      ids.Add ("pushID", ;"value2");
      Visitor.SyncIdentifiers (ids);
      ```

## Target 메서드 {#section_C1E4121CAF9D43538511D857A1F549A7}

* **LoadRequest**

   Sends a request to your configured Target server and returns the string value of the offer generated in a `Action<NSDictionary>` callback.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void LoadRequest (TargetLocationRequest request, Target.ITargetCallback callback); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      class TargetBlock: Java.Lang.Object, Target.ITargetCallback{ 
          public void Call (Java.Lang.Object content) 
         { 
          Console.WriteLine (content.ToString()); 
         } 
      } 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
           Target.LoadRequest (req, new TargetBlock()); 
      ```

* **CreateRequest**

   Convenience constructor to create an `ADBTargetLocationRequest` object with the given parameters.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static TargetLocationRequest TargetCreateRequest(string name,string defaultContent,IDictionary<string,string> parameters); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      IDictionary<string, Java.Lang.Object> parameters = new Dictionary> string, Java.Lang.Object> (); 
          parameters.Add ("key1", "value2"); 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
      ```

* **CreateOrderConfirmRequest**

   `ADBTargetLocationRequest`를 생성합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static TargetLocationRequest TargetCreateRequest (string name, string defaultContent, IDictionary<;string, string> parameters);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      var orderConfirm = Target.CreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **ClearCookies**

   앱에서 Target 쿠키를 지웁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void ClearCookies(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Target.ClearCookies (); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **방문자 프로필**

   가장 최근 획득한 방문자 프로필을 반환합니다. 아직 신호가 전송되지 않은 경우 nil을 반환합니다. 방문자 프로필은 앱이 여러 번 시작되는 경우에도 쉽게 액세스할 수 있도록 `NSUserDefaults`에 저장됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static IDictionary<string, Object> VisitorProfile; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      NSDictionary profile = AudienceManager.VisitorProfile; 
      ```

* **Dpid**

   현재 값을 반환합니다 `DPID`.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static string Dpuuid; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      string currentDpid = AudienceManager.Dpid;
      ```

* **Dpuuid**

   현재 값을 반환합니다 `DPUUID`.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static string AudienceDpuuid; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      string currentDpuuid = AudienceManager.Dpuuid;
      ```

* **AudienceSetDpidAndDpuuid**

   and를 `dpid` 설정합니다 `dpuuid`. 그리고 `dpid` 가 설정된 경우 각 신호 `dpuuid` 로 전송됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void AudienceSetDpidAndDpuuid (string Dpid, String Dpuuid);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      AudienceManager.SetDpidAndDpuuid ("testDpid", "testDpuuid");
      ```

* **SignalWithData**

   Sends audience management a signal with traits and get the matching segments returned in a `Action<NSDictionary>` callback.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void SignalWithData (IDictionary<string, Object> audienceData, AudienceManager.IAudienceManagerCallback callback); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      class AudienceManagerCallback: Java.Lang.Object, 
       AudienceManager.IAudienceManagerCallback{ 
         public void Call (Java.Lang.Object content) 
        {
          Console.WriteLine (content.ToString()); 
        }
      }
      IDictionary<string, Java.Lang.Object> traits = new Dictionary<string, 
      Java.Lang.Object> (); 
         traits.Add ("trait", "b");
      AudienceManager.SignalWithData (traits, new AudienceManagerCallback());
      ```

* **재설정**

   Resets audience manager `UUID` and purges current visitor profile.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void Reset ();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
       AudienceManager.Reset ();
      ```

## 비디오 {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

비디오 분석에 대한 자세한 내용은 [비디오 분석을 참조하십시오](/help/android/analytics-main/video-qs.md).

* **미디어 설정**

   지정된 매개 변수와 함께 `MediaSettings` 개체를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static MediaSettings SettingsWith (string name, double length, string playerName, string playerID);  
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      MediaSettings settings = Media.SettingsWith("name1", 10, "playerName1", "playerID1");
      ```

* **AdSettingsWith**

   광고 비디오 추적에 사용할 `MediaSettings` 개체를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static MediaSettings AdSettingsWith ( string name, double length, 
        string playerName, string parentName, string parentPod, 
      double parentPodPosition, string CPM); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      MediaSettings adSettings = Media.AdSettingsWith ("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1"); 
      ```

* **열기**

   추적을 위해 `ADBMediaSettings` 개체를 엽니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void Open (MediaSettings settings, Media.IMediaCallback callback);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      MediaSettings settings = Media.SettingsWith ("name1", 10, "playerName1", "playerID1"); 
         Media.Open (settings, new MediaCallback()); 
         class MediaCallback: Java.Lang.Object, Media.IMediaCallback{ 
      public void Call (Java.Lang.Object content) 
      {
      }
      }
      ```

* **닫기**

   이름이 name인 미디어 항목을 닫습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void Close(string name);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Media.Close (settings.Name); 
      ```

* **재생**

   제공된 offset(초)에서 이름이 name인 미디어 항목을 재생합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void Play ( string name, double offset); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Media.Play (settings.Name, 0); 
      ```

* **전체**

   제공된 오프셋(초)에서 완료된 미디어 항목을 수동으로 표시합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void Complete (string name, double offset); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Media.Complete (settings.Name, 5); 
      ```

* **정지**

   제공된 오프셋에서 비디오가 중지 또는 일시 중지되었음을 미디어 모듈에 알립니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void Stop ( string name, double offset); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Media.Stop (settings.Name, 3);
      ```

* **클릭**

   미디어 항목이 클릭되었음을 미디어 모듈에 알립니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void Click ( string name, double offset); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Media.Click (settings.Name, 3); 
      ```

* **트랙**

   현재 미디어 상태에 대한 추적 작업 호출(페이지 보기 없음)을 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void Track ( string name, NSDictionary data); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Media.Track (settings.Name, null); 
      ```
