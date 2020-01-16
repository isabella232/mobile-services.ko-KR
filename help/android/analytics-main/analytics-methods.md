---
description: 다음은 Android 라이브러리에서 제공하는 Adobe Analytics 메서드 목록입니다.
keywords: android;library;mobile;sdk
seo-description: 다음은 Android 라이브러리에서 제공하는 Adobe Analytics 메서드 목록입니다.
seo-title: Analytics 메서드
solution: Marketing Cloud,Analytics
title: Analytics 메서드
topic: Developer and implementation
uuid: ac7c640e-9dcc-4724-b561-019cc025d5a7
translation-type: tm+mt
source-git-commit: 657e8b93d1516690ad21d6cf504f9c8f611747b6

---


# Analytics 메서드 {#analytics-methods}

다음은 Android 라이브러리에서 제공하는 Adobe Analytics 메서드 목록입니다.

현재 SDK는 Analytics, Target, Audience Manager 및 Adobe Experience Platform ID 서비스 등 여러 Adobe Experience Cloud 솔루션을 지원합니다. 메서드는 솔루션에 따라 접두사가 붙습니다. 예를 들어 Experience Cloud ID 메서드에는 `analytics` 접두사가 붙습니다.

다음 메서드를 사용하여 Adobe Analytics 보고서 세트에 데이터를 전송합니다.

* **trackState**

   선택적 컨텍스트 데이터로 앱 상태를 추적합니다. 상태는 `home dashboard`, `app settings`, `cart` 등과 같이 앱에서 사용할 수 있는 보기입니다. 이 상태는 웹 사이트의 페이지와 유사하며 `trackState` 호출은 페이지 보기를 증가시킵니다.

   `state`가 비어 있으면 `app name app version (build)`이 보고서에 표시됩니다. 보고서에 이 값이 표시되면 각각의 `state` 호출에서 `trackState`를 반드시 설정해야 합니다.

   >[!TIP]
   >
   >페이지 보기 횟수를 늘리는 유일한 추적 호출입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void trackState(String state, Map<String, Object> contextData);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.trackState("loginScreen", null);
      ```

* **trackAction**
앱의 작업을 추적합니다.

   `logons`, `banner taps`, `feed subscriptions` 및 기타 지표 등 앱에서 발생하여 측정하려는 작업입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void trackAction(String state, Map<String, Object> contextData);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.trackAction("heroBannerTouched", null);
      ```

* **getTrackingIdentifier**
Analytics에 대해 자동으로 생성된 방문자 식별자를 반환합니다.

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

   정의된 관심 영역의 현재 위도와 경도 및 위치를 보냅니다. 자세한 내용은 [지리적 위치 및 관심 영역](/help/android/location/geo-poi.md)을 참조하십시오.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void trackLocation(Location location, Map<String, Object> contextData);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.trackLocation(userLocation, null);
      ```

* **trackLifetimeValueIncrease**

   사용자의 라이프타임 값에 `amount`를 추가합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void trackLifetimeValueIncrease(BigDecimal amount, Map<String, Object> contextData);
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
   public static void trackTimedActionStart(String action, Map<String, Object> contextData);
   ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.trackTimedActionStart("cartToCheckout", null)
      ```


* **trackTimedActionUpdate**

   `contextData`를 전달하여 `action`과 관련된 컨텍스트 데이터를 업데이트합니다. 전달된 `data`는 기존 작업 데이터에 추가되며 동일한 키가 `action`에 이미 정의되어 있으면 데이터를 덮어씁니다.

   >[!TIP]
   >
   >이 호출은 히트를 전송하지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void trackTimedActionUpdate(String action, Map<String, Object> contextData);
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
   >`block`을 지정하는 경우 히트를 전송하려면 `true`를 반환해야 합니다. `block`에 대해 `null`을 전달하면 최종 히트를 전송합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void trackTimedActionEnd(String action, TimedActionBlock<Boolean> logic);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.trackTimedActionEnd("cartToCheckout",new
      Analytics.TimedActionBlock<Boolean>(){
          @Override
          public Boolean call(long inAppDuration, long totalDuration, Map<String, Object> contextData) {
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
      public static void sendQueuedHits();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.sendQueuedHits();
      ```

* **getQueueSize**

   오프라인 큐에서 저장된 추적 호출 수를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static long getQueueSize();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      long queueSize = Analytics.getQueueSize();
      ```

* **clearQueue**

   오프라인 큐에서 모든 히트를 지웁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void clearQueue();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.clearQueue();
      ```

      >[!WARNING]
      >
      > 큐를 수동으로 지울 때는 주의하십시오. 이 프로세스는 되돌릴 수 없습니다.

* **processReferrer**

   나중에 사용하기 위해 Google Play Store의 레퍼러 캠페인 데이터를 처리합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void processReferrer(final Context context, final Intent intent);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.processReferrer(getApplicationContext(), intent);
      ```

* **processGooglePlayInstallReferrerUrl**

   >[!IMPORTANT]
   >
   > 이 API는 SDK 버전 4.18.0부터 사용할 수 있습니다

   제공된 Google Play 설치 레퍼러 URL에서 획득 데이터를 검색합니다.

   이 API에서 수집된 데이터는 Analytics로 전송된 설치 히트 시 전송되며 Adobe 데이터 콜백에서 사용할 수 있습니다.

   SDK에서 레퍼러 데이터를 이미 수집한 경우 이 메서드를 호출하면 작업이 수행되지 않습니다.

   레퍼러 URL을 검색하는 방법에 대한 자세한 내용은 Google 설명서를 참조하십시오.https://developer.android.com/google/play/installreferrer/library.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void processGooglePlayInstallReferrerUrl(final String referrerUrl);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Analytics.processGooglePlayInstallReferrerUrl(referrerUrl);
      ```
