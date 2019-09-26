---
description: 다음은 Android 라이브러리에서 제공하는 Adobe Analytics 메서드 목록입니다.
keywords: android;library;mobile;sdk
seo-description: 다음은 Android 라이브러리에서 제공하는 Adobe Analytics 메서드 목록입니다.
seo-title: 분석 메서드
solution: Marketing Cloud,Analytics
title: 분석 메서드
topic: 개발자 및 구현
uuid: ac7c640e-9dcc-4724-b561-019cc025d5a7
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics methods {#analytics-methods}

다음은 Android 라이브러리에서 제공하는 Adobe Analytics 메서드 목록입니다.

SDK는 현재 Analytics], Target], Audience Manager] 및 Adobe Experience Platform Identity Service]를 비롯한 다양한 Adobe Experience Cloud Solutions]를 지원합니다. 메서드는 솔루션에 따라 접두사가 붙습니다. 예를 들어 Experience Cloud ID 메서드에는 `analytics` 접두사가 붙습니다.

다음 메서드를 사용하여 Adobe Analytics 보고서 세트에 데이터를 전송합니다.

* **trackState**

   선택적 컨텍스트 데이터로 앱 상태를 추적합니다. States are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on. 이 상태는 웹 사이트의 페이지와 유사하며 `trackState` 호출은 페이지 보기를 증가시킵니다.

   If  is empty,  is displayed in reports. `state``app name app version (build)` 보고서에 이 값이 표시되면 각각의 `state` 호출에서 `trackState`를 반드시 설정해야 합니다.

   >[!TIP]
   >
   >이것은 페이지 보기를 증가시키는 유일한 추적 호출입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public staticvoidtrackState(Stringstate, Map<String,Object> contextData);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.trackState("loginScreen",null);
      ```

* **trackAction**&#x200B;앱의 동작을 추적합니다.

   Actions that you want to measure, such as `logons`, `banner taps`, `feed subscriptions`, and other metrics, that occur in your app.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      publicstaticvoidtrackAction(Stringstate,Map<String,Object> contextData);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.trackAction("heroBannerTouched",null);
      ```

* **getTrackingIdentifier** Analytics에 대해 자동으로 생성된 방문자 식별자를 반환합니다.

   처음 실행할 때 생성된 후 저장되어 이후에 사용되는 앱별 고유 방문자 ID입니다. 이 ID는 앱 업그레이드 시에도 보존되며 앱을 제거하면 삭제됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static String getTrackingIdentifier(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      String trackingId = Analytics.getTrackingIdentifier(); 
      ```

* **trackLocation**

   현재 위도, 경도 및 위치를 정의된 관심 영역으로 전송합니다. For more information, see Geo-location and points of interest.[](/help/android/location/geo-poi.md)

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void trackLocation(Location location, Map<String,Object> contextData); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.trackLocation(userLocation, null);
      ```

* **trackLifetimeValueIncrease**

   사용자의 라이프타임 값에 `amount`를 추가합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      publicstaticvoidtrackLifetimeValueIncrease(BigDecimalamount,Map<String,Object>contextData);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.trackLifetimeValueIncrease(new BigDecimal(30), null);
      ```

* **trackTimedActionStart**

   `action` 이름으로 시간 작업을 시작합니다..

   이미 시작한 작업에 대해 이 메서드를 호출하는 경우 이전 시간 제한 작업을 덮어씁니다.

   >[!TIP]
   >
   >이 호출은 히트를 전송하지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.
   ```java
   publicstaticvoidtrackTimedActionStart(Stringaction,Map<String,Object>contextData);
   ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.trackTimedActionStart("cartToCheckout",null)
      ```


* **trackTimedActionUpdate**

   `contextData`를 전달하여 `action`과 관련된 컨텍스트 데이터를 업데이트합니다. 전달된 `data`는 기존 작업 데이터에 추가되며 동일한 키가 `action`에 이미 정의되어 있으면 데이터를 덮어씁니다.

   >[!TIP]
   >
   >이 호출은 히트를 전송하지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void trackTimedActionUpdate(Stringaction,Map <String,Object> contextData); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      HashMap cdata = new HashMap<String Object> (); 
      cdata.put("quantity",3); 
      Analytics.trackTimedActionUpdate("cartToCheckout", cdata);
      ```

* **trackTimedActionEnd**

   시간 제한 작업을 종료합니다. `block`을 지정하면 최종 시간 값에 액세스할 수 있고 최종 히트를 전송하기 전에 `data`를 조작할 수 있습니다.

   >[!TIP]
   >
   >If you provide `block`, you must return `true` to send a hit. Passing `null` for `block` sends the final hit.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void trackTimedActionEnd(Stringaction,TimedActionBlock<Boolean> logic); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.trackTimedActionEnd("cartToCheckout",new
      Analytics.TimedActionBlock<Boolean>(){
        @Override
        public Booleancall(long inAppDuration,long totalDuration, Map<String,
      Object> contextData) {
              contextData.put("price", 49.95);
              return true;
         }
      });
      ```

* **sendQueuedHits**

   **SDK 4.1 필요.**

   큐에 올라간 히트와 관계없이, 이 메서드는 라이브러리가 오프라인 큐의 모든 히트를 전송하도록 합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      voidsendQueuedHits()
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.sendQueuedHits();
      ```

* **getQueueSize**

   오프라인 큐에서 저장된 추적 호출 수를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      long getQueueSize()
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      long queueSize = Analytics.getQueueSize(); 
      ```

* **clearQueue**

   오프라인 큐에서 모든 히트를 지웁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      voidclearQueue()
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.clearQueue();
      ```

      >[!WARNING]
      >
      > 큐를 수동으로 지울 때는 주의하십시오. 이 프로세스는 되돌릴 수 없습니다.