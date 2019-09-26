---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: ADBMobile.cs 메서드
solution: Marketing Cloud,개발자
title: ADBMobile.cs 메서드
uuid: af504934-febd-45d9-81e2-2a310f4c65dc
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# ADBMobile.cs methods {#adbmobile-cs-methods}

## 구성 방법

* **CollectLifecycleData**

   SDK의 솔루션 전체에서 사용하기 위해 라이프사이클 데이터를 수집해야 함을 SDK에 표시합니다. 자세한 내용은 [라이프사이클 지표](/help/ios/metrics.md)를 참조하십시오.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void CollectLifecycleData();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADBMobile.CollectLifecycleData(); 
      ```

* **EnableLocalNotifications(iOS만 해당)**

   앱의 로컬 알림을 활성화합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void EnableLocalNotifications();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADBMobile.EnableLocalNotifications(); 
      ```

* **GetDebugLogging**

   현재 디버그 로깅 기본 설정을 반환합니다. 기본값은 `false`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static bool GetDebugLogging();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      var debugEnabled = ADBMobile.GetDebugLogging();
      ```

* **GetLifetimeValue**

   현재 사용자의 수명 값을 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static double GetLifetimeValue();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      var lifetimeValuea = ADBMobile.GetLifetimeValue();
      ```

* **GetPrivacyStatus**

   현재 사용자에 대한 개인 정보 상태의 열거 표현을 반환합니다.
   * `MOBILE_PRIVACY_STATUS_OPT_IN`:히트가 즉시 전송됩니다.
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`:히트가 무시됩니다.
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: 오프라인 추적이 활성화되면 개인 정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트가 삭제됨)으로 변경될 때까지 히트가 저장됩니다.

      오프라인 추적이 비활성화되면 개인 정보 상태가 옵트인으로 변경될 때까지 히트가 무시됩니다. 기본값은 [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md) 파일에서 설정되어 있습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static ADBPrivacyStatus GetPrivacyStatus();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      var privacyStatus = ADBMobile.GetPrivacyStatus();
      ```

* **GetUserIdentifier**

   사용자 지정 식별자가 설정된 경우 사용자 지정 사용자 식별자를 반환합니다. 사용자 지정 식별자가 설정되지 않은 경우 null을 반환합니다. 기본값은 `null`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static string GetUserIdentifier();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      var userId = ADBMobile.GetUserIdentifier(); 
      ```

* **GetVersion**

   라이브러리 버전을 가져옵니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static string GetVersion();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      var version = ADBMobile.GetVersion();
      ```

* **KeepLifecycleSessionAlive(iOS만 해당)**

   구성 파일의 라이프사이클 세션 시간 제한 값과 상관없이 다음 번에 백그라운드에서 세션이 다시 시작할 때 새 세션이 시작하지 않아야 함을 SDK에 표시합니다.

   >[!TIP]
   >
   >이 메서드는 앱이 백그라운드에 있을 때 알림을 등록하는 앱에 사용되며 앱이 백그라운드에 있을 때 실행하는 코드에서만 호출되어야 합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void KeepLifecycleSessionAlive(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADBMobile.KeepLifecycleSessionAlive(); 
      ```

* **PauseCollectingLifecycleData(Android만 해당)**

   라이프사이클 지표를 정확히 계산하기 위해 앱이 일시 중지되었음을 SDK에 표시합니다. 예를 들어, OnPause에서 타임스탬프를 수집하여 기존 세션 길이를 파악합니다. 플래그를 설정하여 앱이 충돌하지 않았음을 라이프사이클에서 정확히 알도록 할 수도 있습니다. 자세한 내용은 [라이프사이클 지표](/help/android/metrics.md)를 참조하십시오.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void PauseCollectingLifecycleData();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADBMobile.PauseCollectingLifecycleData(); 
      ```

* **SetContext (Android만 해당)**

   UnityPlayer의 현재 활동에서 응용 프로그램 컨텍스트를 설정해야 함을 SDK에 표시합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void SetContext();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADBMobile.SetContext(); 
      ```

* **SetDebugLogging**

   디버그 로깅 기본 설정을 활성화됨으로 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void SetDebugLogging (bool enabled); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADBMobile.SetDebugLogging(true); 
      ```

* **SetPrivacyStatus**

   현재 사용자의 개인 정보 상태를 상태로 설정합니다. 다음 값 중 하나를 설정합니다.

   * `MOBILE_PRIVACY_STATUS_OPT_IN`:히트가 즉시 전송됩니다.
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`:히트가 무시됩니다.
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: 오프라인 추적이 활성화되면 개인 정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트가 삭제됨)으로 변경될 때까지 히트가 저장됩니다. 오프라인 추적이 비활성화되면 개인 정보 상태가 옵트인으로 변경될 때까지 히트가 무시됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void SetPrivacyStatus(ADBPrivacyStatusstatus); 
      ```

   * 다음은 이 구문에 대한 코드 샘플입니다.

      ```java
      ADBMobile.SetPrivacyStatus(ADBMobile.ADBPrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN);
      ```

* **SetUserIdentifier**

   사용자 식별자를 userId로 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void SetUserIdentifier(string userId); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADBMobile.SetUserIdentifier("myCustomUserId"); 
      ```

## 분석 방법

* **GetTrackingIdentifier**

   분석 추적 식별자를 검색합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static string GetTrackingIdentifier();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      var trackingId = ADBMobile.GetTrackingIdentifier(); 
      ```

* **TrackState**

   선택적 컨텍스트 데이터로 앱 상태를 추적합니다. 상태는 "제목 화면", "레벨 1", "일시 중지" 등 앱에서 사용할 수 있는 보기입니다. 이 상태는 웹 사이트의 페이지와 유사하며 `TrackState` 호출은 페이지 보기를 증가시킵니다.

   If state is empty, it displays as *`app name app version (build)`* in reports. 보고서에서 이 값이 표시되면 반드시 각각의 `TrackState` 호출에서 상태를 설정해야 합니다.

   >[!TIP]
   >
   >This is the only tracking call that increments page views.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackState(string state, Dictionary<string, object> cdata);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      var contextData = new Dictionary<string, object>); 
      contextData.Add ("user", "jim");
      ADBMobile.TrackState("title screen", contextData);
      ```

* **TrackAction**

   앱의 작업을 추적합니다. 작업은 "예기치 못한 종료", "획득 레벨", "피드 구독" 및 기타 지표 등 측정하려는 앱에서 발생하는 일을 의미합니다.

   >[!TIP]
   >
   >If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackAction(string action, Dictionary<string, object> cdata); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADBMobile.TrackAction("level gained", null); 
      ```

* **TrackActionFromBackground(iOS만 해당)**

   백그라운드에서 발생된 작업을 추적합니다. 특정 시나리오에서 라이프사이클 이벤트의 시작을 억제합니다.

   >[!TIP]
   >
   >이 메서드는 앱이 백그라운드에 있을 때 실행되는 코드에서만 호출되어야 합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackActionFromBackground(string action, Dictionary<string,object> cdata); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   현재 위도 및 경도 좌표를 보냅니다. 또한 `ADBMobileConfig.json` 파일에서 정의된 관심 영역을 사용하여 매개변수로 제공된 위치가 POI 내에 있는지 파악합니다. 현재 좌표가 정의된 POI 내에 있는 경우 컨텍스트 데이터 변수를 채워 TrackLocation 호출로 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackLocation(float latValue, float lonValue, Dictionary<string, object> cdata); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADBMobile.TrackLocation(28.418649, -81.581324, null); 
      ```

* **TrackBeacon**

   사용자가 비콘 근접 위치에 들어오면 추적합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackBeacon(int major, int minor, string uuid, ADBBeaconProximity proximity, Dictionary<string, object> cdata); 
      ```

* **TrackingClearCurrentBeacon**

   사용자가 비콘 근접 위치를 떠난 후 비콘 데이터를 지웁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackingClearCurrentBeacon(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   사용자의 라이프타임 값에 양을 추가합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackLifetimeValueIncrease(double amount, Dictionary<string, object> cdata);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADBMobile.TrackLifetimeValueIncrease(5, null); 
      ```

* **TrackTimedActionStart**

   이름 작업으로 시간 제한 작업을 시작합니다. 이미 시작한 작업에 대해 이 메서드를 호출하는 경우 이전 시간 제한 작업을 덮어씁니다.

   >[!TIP]
   >
   >이 호출은 히트를 전송하지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackTimedActionStart(string action, Dictionary<string,object> cdata); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   주어진 작업과 연관된 컨텍스트 데이터를 업데이트하기 위해 데이터를 전달합니다. 전달한 데이터는 주어진 작업의 기존 데이터에 추가되며 작업에 대해 동일한 키가 이미 정의된 경우 데이터를 덮어씁니다.

   >[!TIP]
   >
   >이 호출은 히트를 전송하지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackTimedActionUpdate(string action, Dictionary<string, object> cdata); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      var contextData = new Dictionary<string, object>; 
      contextData.Add("checkpoint", "1:32"); 
         ADBMobile.TrackTimedActionUpdate("level2", contextData);
      ```

* **TrackTimedActionEnd**

   시간 제한 작업을 종료합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackTimedActionEnd(string action); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADBMobile.TrackTimedActionEnd("level2"); 
      ```

* **TrackingTimedActionExists**

   시간 제한 작업이 진행 중인지 여부를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static bool TrackingTimedActionExists(string action); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
       var level2InProgress = ADBMobile.TrackingTimedActionExists("level2"); 
      ```

* **TrackingSendQueuedHits**

   현재 큐에 올라가 있는 히트 개수와 상관없이 라이브러리에서 오프라인 큐의 모든 히트를 강제로 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackingSendQueuedHits();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADBMobile.TrackingSendQueuedHits(); 
      ```

* **TrackingClearQueue**

   오프라인 큐에서 모든 히트를 지웁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void TrackingClearQueue();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ADBMobile.TrackingClearQueue(); 
      ```

* **TrackingGetQueueSize**

   현재 오프라인 큐에 올라가 있는 히트 수를 검색합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static int TrackingGetQueueSize();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      var queueSize = ADBMobile.TrackingGetQueueSize();
      ```

## Experience Cloud ID 메서드

* **GetMarketingCloudID**

   ID 서비스에서 Experience Cloud ID를 검색합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static string GetMarketingCloudID(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   Experience Cloud ID를 사용하면 각 방문자에 연결할 추가 고객 ID를 설정할 수 있습니다. 방문자 API는 여러 다른 고객 ID의 범위를 구분하기 위해 동일한 방문자의 여러 고객 ID와 고객 유형 식별자를 수락합니다. 이 메서드는 JavaScript 라이브러리의 setCustomerID에 해당합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void VisitorSyncIdentifiers(Dictionary<string, object> identifiers); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      var ids = new Dictionary<string, object> (); 
      ids.Add ("player1", "jimbob"); 
      ADBMobile.VisitorSyncIdentifiers(ids);
      ```

