---
description: 다음은 Android 라이브러리에서 제공하는 메서드 목록입니다.
keywords: android;library;mobile;sdk
seo-description: 다음은 Android 라이브러리에서 제공하는 메서드 목록입니다.
seo-title: 구성 메서드
solution: Marketing Cloud,Analytics
title: 구성 메서드
topic: Developer and implementation
uuid: 663aeb6c-1b97-4a3a-8c0e-dd4c2ec28c01
translation-type: ht
source-git-commit: dae60a21286edc28c84b7638da214b824abf0cd3

---


# 구성 메서드 {#configuration-methods}

다음은 Android 라이브러리에서 제공하는 메서드 목록입니다.

## 초기 구성 {#section_9169243ECC4744A899A8271F92090ECD}

다음 메서드는 기본 활동의 `onCreate` 메서드에서 한 번은 호출해야 합니다.

* `setContext`다음은 이 메서드의 코드 샘플입니다.

   ```java
    @Override
    public void onCreate(BundlesavedInstanceState){
      super.onCreate(savedInstanceState)
      setContentView(R.layout.main);
      Config.setContext(this.getApplicationContext());
    }
   ```

## SDK 설정(구성 클래스) {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **registerAdobeDataCallback**

   * `AdobeDataCallback` 인터페이스를 구현하는 개체를 등록합니다. 덮어쓴 &quot;call&quot; 메서드는 `Config.MobileDataEvent` 값 및 트리거링 이벤트에 대한 `Map<String, Object>`의 관련 데이터와 함께 호출됩니다. 이 콜백을 트리거할 이벤트에 대한 자세한 내용은 이 항목 하단에 있는 *MobileDataEventEnum*&#x200B;을 참조하십시오.

      >[!TIP]
      >
      >이 메서드를 사용하려면 버전 4.9.0 이상이 필요합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void registerAdobeDataCallback(final AdobeDataCallback&amp;nbsp;callback);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
        Config.registerAdobeDataCallback(new Config.AdobeDataCallback() {
          @Override
          public void call(Config.MobileDataEvent event, Map<String, Object> contextData) {
              // handle each event type accordingly 
              if (event == Config.MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL) {
                   // do something with acquisition data found in contextData parameter
                   HashMap<String, Object> acquisitionData = new HashMap<String, Object>(contextData);
              }
          }
      });
      ```

* **getVersion**

   * Adobe Mobile 라이브러리의 현재 버전을 반환합니다.
   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static String getVersion();
      ```

   * 다음은 이 메서드의 코드 예입니다.

      ```java
      String libraryVersion = Config.getVersion(); 
      ```

* **getPrivacyStatus**

   * 현재 사용자에 대한 개인 정보 상태의 열거 표현을 반환합니다.

      다음은 개인 정보 상태 값입니다.

      * `MOBILE_PRIVACY_STATUS_OPT_IN`: 히트를 즉시 보냅니다.
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`: 히트가 삭제됩니다.
      * `MOBILE_PRIVACY_STATUS_UNKNOWN`: 보고서 세트에 타임스탬프가 사용되는 경우 개인정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트가 삭제됨)으로 변경될 때까지 히트가 저장됩니다.

         보고서 세트에 타임스탬프가 활성화되어 있지 않을 경우 개인정보 상태가 옵트인으로 변경될 때까지 히트가 삭제됩니다. 기본값은 `ADBMobileConfig.json` 파일에서 설정되어 있습니다.
   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static MobilePrivacyStatus getPrivacyStatus(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      MobilePrivacyStatus privacyStatus Config.getPrivacyStatus();
      ```


* **setPrivacyStatus**

   * 현재 사용자의 개인정보 상태를 `status`로 설정합니다.

      개인정보 상태를 다음 값 중 하나로 설정할 수 있습니다.
      * `MOBILE_PRIVACY_STATUS_OPT_IN`: 히트를 즉시 보냅니다. 이 히트는 즉시 전송됩니다.
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`: 히트가 삭제됩니다. 이 히트는 삭제됩니다.
      * `MOBILE_PRIVACY_STATUS_UNKNOWN`: 보고서 세트에 타임스탬프가 사용되는 경우 개인정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트가 삭제됨)으로 변경될 때까지 히트가 저장됩니다.
보고서 세트에 타임스탬프가 활성화되어 있지 않을 경우 개인정보 상태가 옵트인으로 변경될 때까지 히트가 삭제됩니다.
   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void setPrivacyStatus(MobilePrivacyStatus status); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
      ```


* **getLifetimeValue**

   * 현재 사용자의 수명 값을 반환합니다. 기본값은 `0`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static BigDecimal getLifetimeValue();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      BigDecimal currentLifetimeValue Config.getLifetimeValue(); 
      ```

* **getUserIdentifier**

   * 사용자 지정 ID가 설정된 경우 사용자 지정 사용자 ID가 반환됩니다. 사용자 지정 ID가 설정되지 않은 경우에는 `null`을 반환합니다. 기본값은 `null`입니다.

      >[!TIP]
      >
      >앱을 Experience Cloud 3.x에서 4.x SDK로 업그레이드할 경우 이전 사용자 지정 또는 자동 생성된 방문자 ID가 검색되어 사용자 지정 사용자 식별자로 저장됩니다. 이렇게 하면 SDK 업그레이드 시에도 방문자 데이터가 보존됩니다. 4.x SDK에 새로 설치하는 경우 사용자 ID는 `null`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static String&amp getUserIdentifier();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      String userId = Config.getUserIdentifier();
      ```

* **setUserIdentifier**

   * 사용자 식별자를 `identifier`로 설정합니다.
   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void setUserIdentifer(String identifier);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Config.setUserIdentifier("billybob"); 
      ```

* **getDebugLogging**

   * 현재 디버그 로깅 기본 설정을 반환합니다. 기본값은 `false`입니다.
   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static Boolean getDebugLogging(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Boolean debugging = Config.getDebugLogging(); 
      ```

* **setDebugLogging**
   * 디버그 로깅 기본 설정을 `debugLogging`으로 설정합니다. 
   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void setDebugLogging(Boolea debugLogging);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Config.setDebugLogging(true);
      ```

* **collectLifecycleData**
   * SDK의 솔루션 전체에서 사용하기 위해 라이프사이클 데이터를 수집해야 함을 SDK에 표시합니다. 자세한 내용은 [라이프사이클 지표](/help/android/configuration/methods.md)를 참조하십시오.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void collectLifecycleData(final Activity activity,final Map<String, Object>contextData); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      @Override
      protectedvoid  onResume()  {
        super.onResume();
        Config.collectLifecycleData(this);
        } 
      ```

      추가 컨텍스트 데이터가 있는 경우:

      ```java
      @Override
      public  void  onResume()  {
        HashMap<String, Object> contextData = new HashMap<String, Object>();
        contextData.put("myapp.category", "Game");        Config.collectLifecycleData(this, contextData);} 
      ```

* **collectLifecycleData (Activity activity)**

   * (**버전 4.2 이상**) SDK의 솔루션 전체에서 사용하기 위해 라이프사이클 데이터를 수집해야 함을 SDK에 표시합니다. 자세한 내용은 [라이프사이클 지표](/help/android/metrics.md)를 참조하십시오.
   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void collectLifecycleData(final Activity activity);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      @Overrideprotected void onResume() {
        super.onResume()
        // assume being called in an Activity class Config.collectLifecycleData(this);
        } 
        ```
      
* **pauseCollecting&#x200B;LifecycleData**

   * 라이프사이클 지표를 정확히 계산하기 위해 앱이 일시 중지되었음을 SDK에 표시합니다. 예를 들어 `onPause`에서 타임스탬프를 수집하여 기존 세션 길이를 파악합니다. 플래그를 설정하여 앱이 충돌하지 않았음을 라이프사이클에서 알도록 할 수도 있습니다. 자세한 내용은 [라이프사이클 지표](/help/android/metrics.md)를 참조하십시오.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void pauseCollectingLifecycleData(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      @Override
      protected void onPause() {
        super.onPause();
        Config.pauseCollectingLifecycleData();
      } 
      ```

* **setSmallIconResourceId(int resourceId)**

   * (**버전 4.2 이상**) SDK에서 만든 알림에 사용할 작은 아이콘을 설정합니다. 이 아이콘은 상태 표시줄에 표시되며, 사용자가 알림 센터에서 전체 알림을 볼 때 표시되는 보조 이미지가 됩니다.
   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **setLargeIconResourceId(int resourceId)**

   * (**버전 4.2 이상**) SDK에서 만든 알림에 사용할 큰 아이콘을 설정합니다. 이 아이콘이 사용자가 알림 센터에서 전체 알림을 볼 때 표시되는 기본 이미지가 됩니다.
   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void setLargeIconResourceId(final int  resourceId);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```Java
      Config.setLargeIconResourceId(R.drawable.appIcon);
      ```

* **overrideConfigStream(InputStream configInput)**

   * (**버전 4.2 이상**) 애플리케이션이 시작될 때 다른 ADBMobile JSON 구성 파일을 로드할 수 있습니다. 애플리케이션이 닫힐 때까지 다른 구성을 사용합니다.
   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void overrideConfigStream(final InputStream configInput);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
       try {
          InputStream configInput = getAssets().open("ExampleJSONFile.json") 
          Config.overrideConfigStream(configInput)
          } catch (IOException ex) { 
          //do something with the exception if needed
      }
      ```

* **setPushIdentifier**

   * 푸시 알림용 장치 토큰을 설정합니다.
   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void setPushIdentifier(final String registrationId); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      ...// note the code to retreive the push token must run in the background
      InstanceID instanceID= InstanceID.getInstance(getApplicationContext());String token=instanceID.getToken("835015092242", GoogleCloudMessaging.INSTANCE_ID_SCOPE null);Config.setPushIdentifier(token);
      ...
      ```

* **submitAdvertisingIdentifierTask**

   * Google Play 서비스에서 반환되는 광고 식별자의 문자열을 반환하는 호출 가능 항목을 SDK에 제공합니다. SDK는 백그라운드 스레드에서 이 작업을 실행하고 호출 가능 항목에서 반환된 값을 기반으로 하는 광고 식별자의 내부 변수를 설정합니다.

      >[!IMPORTANT]
      > 
      >획득 또는 라이프사이클에서 광고 식별자를 사용하려면 `Config.collectLifecycleData`를 호출하기 전에 먼저 광고 식별자를 호출하십시오.

      * 다음은 이 메서드에 대한 구문입니다.

         ```java
         public static void submitAdvertisingIdentifierTask(final Callable<String> task); 
         ```

      * 다음은 이 메서드의 코드 샘플입니다.

         ```java
         @Override
         public void  onResume() {
             super.onResume();
             final  Callable<String>; task = new Callable<String>(){
                 @Override
                 public String call() throws Exception {
                    AdvertisingIdClient.Info idInfo;
                    String adid = null;
                    Context appContext = CLASSNAME.this.getApplicationContext();
                    try {
                         idInfo = AdvertisingIdClient.getAdvertisingIdInfo(appContext);
                         if (idInfo != null) { 
                             adid = idInfo.getId();
                         } 
                    } catch  (Exception ex) {
                        Log.e("Error",  ex.getLocalizedMessage());
                    }
                    return  adid;
                 }
           };
           Config.submitAdvertisingIdentifierTask(task); 
           Config.collectLifecycleData(this);
         }
         ```


## AdobeDataCallback Interface {#section_600A63B3136F47DCB928071485C5117C}

```java
public interface AdobeDataCallback {  
    void call(MobileDataEvent event, Map<String, Object> contextData);  
} 
```

## MobileDataEvent Enum {#section_92732814141646E294782BC9020367EB}

```java
public enum MobileDataEvent {  
    MobileDataEvent.MOBILE_EVENT_LIFECYCLE, // triggers on a lifecycle hit  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL, // triggers on a app install that has acquisition data  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH // triggers on launch when the device previously installed via acquisition  
}
```
