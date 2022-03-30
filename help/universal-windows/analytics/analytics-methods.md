---
description: Adobe Analytics에서 Universal Windows Platform SDK를 사용하는 데 도움이 되는 정보입니다.
solution: Experience Cloud Services,Analytics
title: Analytics 메서드
topic-fix: Developer and implementation
uuid: cc299bb5-ec61-49bf-869a-f3c3bc83359f
exl-id: 3ceaedfa-274f-4dc7-9e4c-15233d09f935
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Analytics 메서드 {#analytics-methods}

Adobe Analytics에서 Universal Windows Platform SDK를 사용하는 데 도움이 되는 정보입니다.

현재 SDK는 Analytics, Target 및 Audience Manager 등 여러 Adobe Experience Cloud 솔루션을 지원합니다. 메서드에는 솔루션에 따라 접두사가 붙습니다. Analytics 메서드 앞에는 &quot;Analytics&quot;가 붙습니다.

이러한 각 메서드는 Adobe Analytics 보고서 세트로 데이터를 전송하는 데 사용됩니다.

>[!TIP]
>
>소비할 때 `winmd` winJS(JavaScript)의 메서드를 사용하면 모든 메서드가 자동으로 첫 번째 문자를 소문자로 바꿉니다.

* **TrackState(winJS: trackState)**

   선택적 컨텍스트 데이터로 앱 상태를 추적합니다. 상태는 &quot;홈 대시보드&quot;, &quot;앱 설정&quot;, &quot;장바구니&quot; 등과 같이 앱에서 사용할 수 있는 보기입니다. 이 상태는 웹 사이트의 페이지와 유사하며 `TrackState` 호출은 페이지 보기를 증가시킵니다.
If `state` 가 비어 있으면 보고서에 &quot;앱 이름 앱 버전(빌드)으로 표시됩니다. 보고서에 이 값이 표시되면 다음을 설정해야 합니다 `state` 각각 `TrackState` 호출.

   >[!TIP]
   >
   >페이지 보기 횟수를 늘리는 유일한 추적 호출입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **TrackAction (winJS: trackAction)**

   앱의 작업을 추적합니다. 작업은 &quot;logons&quot;, &quot;banner taps&quot;, &quot;feed subscriptions&quot; 및 기타 지표 등 앱에서 발생하여 측정하려는 작업입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackAction("ButtonClick",null); 
      ```

* **GetTrackingIdentifierAsync(winJS: getTrackingIdentifierAsync)**

   Analytics에 대해 자동으로 생성된 방문자 ID를 반환합니다. 이 ID는 앱별 고유 방문자 ID이며 처음 실행 시 생성되어 저장되고 이후에 계속 사용됩니다. 이 ID는 앱 업그레이드 사이에 유지되며 설치 제거 시 제거됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String> ^GetTrackingIdentifierAsync(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      vartrackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function(trackingid){
      trackingIdentifier=trackingid;
      });
      ```

* **TrackLocation(winJS: trackLocation)**

   현재 xy 좌표를 보냅니다. 또한 `ADBMobileConfig.json` 파일에서 정의된 관심 영역을 사용하여 매개변수로 제공된 위치가 POI 내에 있는지 파악합니다. 현재 좌표가 정의된 POI 내에 있을 경우 컨텍스트 데이터 변수를 채워 `trackLocation` 호출로 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackLocation(47.60621,-122.33207,null);
      ```

* **TrackLifetime &#x200B; ValueIncrease(winJS: trackLifetime &#x200B; ValueIncrease)**

   사용자의 라이프타임 값에 `amount`를 추가합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      varADB=ADBMobile;
      ADB.Analytics.trackLifetimeValueIncrease(10,null);
      ```

* **TrackTimed &#x200B; ActionStart (winJS: trackTimed &#x200B; ActionStart)**

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
      varADB=ADBMobile;
      ADB.Analytics.trackTimedActionStart("cartToCheckout",null); 
      ```

* **TrackTimed &#x200B; ActionUpdate(winJS: trackTimed &#x200B; ActionUpdate)**

   `contextData`를 전달하여 제공된 `action`과 연관된 컨텍스트 데이터를 업데이트합니다. 전달한 `data`는 지정된 작업의 기존 데이터에 추가되며 `action`에 대해 동일한 키가 이미 정의된 경우 데이터를 덮어씁니다.

   >[!TIP]
   >
   >이 호출은 히트를 전송하지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      varADB = ADBMobile;
      varcontextData = newWindows.Foundation.Collections.PropertySet();
      contextData["quantity"]=3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout",contextData);
      ```

* **TrackTimedActionExistsAsync(winJS: trackTimedActionExistsAsync)**

   지정된 시간 작업이 있으면 true를 반환하고, 없는 경우 false를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function(exists){ 
          actionExists = exists; 
      });
      ```

* **TrackTimed &#x200B; ActionEnd(winJS: trackTimed &#x200B; ActionEnd)**

   시간 제한 작업을 종료합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void TrackTimedActionEnd(Platform::String ^action);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      varADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **ClearTrackingQueue(winJS: clearTrackingQueue)**

   Analytics 추적 큐에서 저장된 모든 히트를 지웁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void ClearTrackingQueue();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **GetQueueSizeAsync(winJS: getQueueSizeAsync)**

   현재 Analytics 큐에 저장된 히트 수를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static Windows::Foundation::IAsyncOperation<int> ^GetQueueSizeAsync();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      varqueueSize;
      ADBMobile.Analytics.getQueueSizeAsync().then(function(size){ 
          queueSize=size;
      });
      ```
