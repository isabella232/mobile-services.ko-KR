---
description: 다음은 Adobe Analytics에서 Windows 8.1 Universal App Store SDK를 사용하는 데 유용한 정보입니다.
seo-description: 다음은 Adobe Analytics에서 Windows 8.1 Universal App Store SDK를 사용하는 데 유용한 정보입니다.
seo-title: Analytics 메서드
solution: Marketing Cloud, Analytics
title: Analytics 메서드
topic: 개발자 및 구현
uuid: 79 DB 105 C -216 C -4061-97 F 3-A 55954995 E 67
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics methods {#analytics-methods}

다음은 Adobe Analytics에서 Windows 8.1 Universal App Store SDK를 사용하는 데 유용한 정보입니다.

SDK는 현재 여러 Adobe Experience Cloud 솔루션 (Analytics], Target] 및 Audience Manager) 를 지원합니다. 메서드에는 솔루션에 따라 접두사가 붙습니다. Analytics 메서드는 "Analytics"로 시작합니다.

이러한 각 메서드는 Adobe Analytics 보고서 세트로 데이터를 전송하는 데 사용됩니다.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **Trackstate (winjs: Trackstate)**

   선택적 컨텍스트 데이터로 앱 상태를 추적합니다. 상태는 'home dashboard', 'app settings', 'cart' 등과 같이 앱에서 사용할 수 있는 보기입니다. 이 상태는 웹 사이트의 페이지와 유사하며 `TrackState` 호출은 페이지 보기를 증가시킵니다. `state`가 비어 있는 경우 보고서에 'app name app version (build)'이 표시됩니다. If you see this value in reports, make sure you are setting `state` in each `TrackState` call.

   >[!TIP]
   >
   >페이지 보기를 증가시키는 유일한 추적 호출입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile;
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **Trackaction (winjs: Trackaction)**

   앱의 작업을 추적합니다. 작업은 'logons,' 'banner taps,' 'feed subscriptions' 및 기타 지표 등 앱에서 발생하여 측정하려는 작업입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap <Platform::String^, Platform::Object> ^contextData);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackAction("Button Click", null); 
      ```

* **Gettrackingidentifierasync (winjs: Gettrackingidentifierasync)**

   분석을 위해 자동으로 생성된 방문자 식별자를 반환합니다. 처음 실행할 때 생성된 후 저장되어 이후에 사용되는 앱별 고유 방문자 ID입니다. 이 ID는 앱을 업그레이드해도 유지되며 앱을 삭제하면 제거됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String^> ^GetTrackingIdentifierAsync(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var trackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function (trackingid) { 
         trackingIdentifier = trackingid; 
      });
      ```

* **Tracklocation (winjs: Tracklocation)**

   현재 xy 좌표를 보냅니다. 또한 `ADBMobileConfig.json` 파일에서 정의된 관심 영역을 사용하여 매개변수로 제공된 위치가 POI 내에 있는지 파악합니다. 현재 좌표가 정의된 POI 내에 있을 경우 컨텍스트 데이터 변수를 채워 `trackLocation` 호출로 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackLocation(47.60621, -122.33207, null);
      ```

* **Tracklifetimevalueincrease (winjs: Tracklifetimevalueincrease)**

   사용자의 라이프타임 값에 `amount`를 추가합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackLifetimeValueIncrease(10, null); 
      ```

* **Tracktimedactionstart (winjs: Tracktimedactionstart)**

   `action` 이름으로 시간 작업을 시작합니다.. 이미 시작한 작업에 대해 이 메서드를 호출하는 경우 이전 시간 제한 작업을 덮어씁니다.

   >[!TIP]
   >
   >이 호출은 히트를 전송하지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void TrackTimedActionStart(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackTimedActionStart("cartToCheckout", null); 
      ```

* **Tracktimedactionupdate (winjs: Tracktimedactionupdate)**

   `contextData`를 전달하여 제공된 `action`과 연관된 컨텍스트 데이터를 업데이트합니다. The `data` passed is appended to the existing data for the given action, and overwrites the data if the same key is already defined for `action`.

   >[!TIP]
   >
   >이 호출은 히트를 전송하지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile; 
      var contextData = new Windows.Foundation.Collections.PropertySet(); 
      contextData["quantity"] = 3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout", contextData); 
      ```

* **Tracktimedactionexistsasync (winjs: Tracktimedactionexistsasync)**

   지정된 시간 제한 작업이 있는 경우 true를 반환하고 그렇지 않은 경우 false를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function (exists) { 
          actionExists = exists; 
      });
      ```

* **Tracktimedactionend (winjs: Tracktimedactionend)**

   시간 제한 작업을 종료합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void TrackTimedActionEnd(Platform::String ^action);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **Cleartrackingqueue (winjs: Cleartrackingqueue)**

   Analytics 추적 큐에서 저장된 모든 히트를 지웁니다.

   * 다음은 이 메시지의 구문입니다.

      ```csharp
      static void ClearTrackingQueue();
      ```

   * 다음은 코드 샘플입니다.

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **Getqueuesizeasync (winjs: Getqueuesizeasync)**

   Analytics 큐에 현재 저장된 히트를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static Windows::Foundation::IAsyncOperation<int> ^GetQueueSizeAsync();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var queueSize; 
      ADBMobile.Analytics.getQueueSizeAsync().then(function (size) { 
          queueSize = size; 
      });
      ```
