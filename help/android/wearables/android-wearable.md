---
description: Android SDK 버전 4.5부터 새 Android 확장 기능을 추가하여 Android 웨어러블 앱의 데이터를 수집할 수 있도록 했습니다.
seo-description: Android SDK 버전 4.5부터 새 Android 확장 기능을 추가하여 Android 웨어러블 앱의 데이터를 수집할 수 있도록 했습니다.
seo-title: Android Wearable 시작하기
solution: Marketing Cloud, Analytics
title: Android Wearable 시작하기
topic: 개발자 및 구현
uuid: BFE 5 D 41 E-B 17 C -4634-80 AC -7 A 38671 ECB 81
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Android Wearables: getting started{#android-wearables-getting-started}

Android SDK 버전 4.5부터 새 Android 확장 기능을 추가하여 Android 웨어러블 앱의 데이터를 수집할 수 있도록 했습니다.

## Configuring the SDK for a handheld app (Android Studio) {#section_262237484EC44C58953891B105F0D000}

SDK를 프로젝트로 가져오는 방법에 대한 자세한 내용은 [핵심 구현 및 라이프사이클을 참조하십시오](/help/android/getting-started/dev-qs.md).

1. 프로젝트의 assets 폴더에 `ADBMobileConfig.json` 파일을 추가합니다.
1. `adobeMobileLibrary-*.jar` 파일을 libs 폴더에 추가하거나 프로젝트가 이 파일을 참조하도록 합니다.

   >[!TIP]
   >
   >You might need to sync the gradle project after adding the `.jar` file.

1. `onCreate` 메서드에서 `Config.setContext`를 사용하여 SDK가 애플리케이션 컨텍스트에 액세스할 수 있도록 합니다.

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext()); 
   }
   ```

1. 파일에 다음 코드를 `AndroidManifest.xml` 추가합니다.

   ```java
       <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" /> 
       <uses-permission android:name="android.permission.INTERNET" /> 
       <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
   
   <application> 
   ....... 
   <meta-data android:name="com.google.android.gms.version" 
               android:value="@integer/google_play_services_version" /> 
   </application>
   ```

1. 프로젝트가 Google Play 서비스 라이브러리를 포함하는지 확인합니다.
1. Implement `WearableListenerService` or add the corresponding code to your `WearableListenerService`:

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onMessageReceived(MessageEvent messageEvent) { 
           super.onMessageReceived(messageEvent); 
       } 
   
       private GoogleApiClient mGoogleApiClient; 
   
       @Override 
       public void onCreate() { 
           super.onCreate(); 
           mGoogleApiClient = new GoogleApiClient.Builder(this) 
                   .addApi(Wearable.API) 
                   .build(); 
           mGoogleApiClient.connect(); 
       } 
       @Override 
       public void onDestroy() { 
           super.onDestroy(); 
           mGoogleApiClient.disconnect(); 
       } 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerHandheld.onDataChanged(dataEvents, mGoogleApiClient, this); 
       } 
   }
   ```

1. 파일에 `WearListenerService``AndroidManifest.xml` 추가합니다.

   ```java
   If you are using Google Play Services  < 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                   <action android:name="com.google.android.gms.wearable.BIND_LISTENER" /> 
               </intent-filter> 
       </service> 
   </application> 
   If you are using Google Play Services >= 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                     <action android:name="com.google.android.gms.wearable.DATA_CHANGED" /> 
                    <data android:scheme="wear" android:host="*" android:pathPrefix="/abdmobile" /> 
               </intent-filter> 
       </service> 
   </application> 
   
   Please find more information from google's blog https://android-developers.googleblog.com/2016/04/deprecation-of-bindlistener.html. 
   Permalink Edit
   ```

## Configuring the SDK for a Wearable app (Android Studio) {#section_2268EC03E20B4A228A28BDCFEA2E9AE4}

1. 다음 작업 중 하나를 완료하십시오.

   * 웨어러블 프로젝트의 assets 폴더에 동일한 `ADBMobileConfig.json` 파일을 추가합니다.
   * 휴대폰 앱의 assets 폴더에서 `ADBMobileConfig.json`을 사용하도록 gradle 구성을 변경합니다.

      ```java
      android { 
      
          sourceSets { 
              main { 
                  assets.srcDirs = ['src/main/assets','../mobile/src/main/assets'] 
              } 
         } 
      }
      ```

1. `adobeMobileLibrary-*.jar` 파일을 libs 폴더에 추가하거나 프로젝트가 참조되었는지 확인합니다.

   jar 파일을 추가한 후 gradle 프로젝트를 동기화해야 할 수도 있습니다.

1. `onCreate` 메서드에서 `Config.setContext`를 사용하여 SDK가 애플리케이션 컨텍스트에 액세스할 수 있게 합니다.

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main);      
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext(), Config.ApplicationType.APPLICATION_TYPE_WEARABLE); 
   }
   ```

1. `AndroidManifest.xml`에 다음 코드를 추가합니다.

   ```java
   <application> 
   ....... 
   <meta-data android:name="com.google.android.gms.version" 
               android:value="@integer/google_play_services_version" /> 
   </application>
   ```

1. 프로젝트가 Google Play 서비스 라이브러리를 포함하는지 확인합니다.
1. Implement `WearableListenerService` or add the corresponding code to your `WearableListenerService`:

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerWearable.onDataChanged(dataEvents); 
       } 
   
   }
   ```

1. 파일에 `WearListenerService``AndroidManifest.xml` 추가합니다.

   ```java
   If you are using Google Play Services  < 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                   <action android:name="com.google.android.gms.wearable.BIND_LISTENER" /> 
               </intent-filter> 
       </service> 
   </application> 
   If you are using Google Play Services >= 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                     <action android:name="com.google.android.gms.wearable.DATA_CHANGED" /> 
                    <data android:scheme="wear" android:host="*" android:pathPrefix="/abdmobile" /> 
               </intent-filter> 
       </service> 
   </application> 
   Please find more information from google's blog https://android-developers.googleblog.com/2016/04/deprecation-of-bindlistener.html. 
   Permalink Edit
   ```

