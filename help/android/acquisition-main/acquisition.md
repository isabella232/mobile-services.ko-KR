---
description: Adobe Mobile Services에서 고유한 추적 코드가 있는 획득 링크를 생성할 수 있습니다. 사용자가 생성된 링크를 클릭한 후 앱스토어에서 앱을 다운로드하여 실행하면 SDK에서 자동으로 획득 데이터를 수집하여 Adobe Mobile Services로 보냅니다.
keywords: android;library;mobile;sdk
seo-description: Adobe Mobile Services에서 고유한 추적 코드가 있는 획득 링크를 생성할 수 있습니다. 사용자가 생성된 링크를 클릭한 후 앱스토어에서 앱을 다운로드하여 실행하면 SDK에서 자동으로 획득 데이터를 수집하여 Adobe Mobile Services로 보냅니다.
seo-title: 모바일 앱 획득
solution: Marketing Cloud,Analytics
title: 모바일 앱 획득
topic: Developer and implementation
uuid: 4d32eae9-e856-4e40-8a29-2b5bccd106e0
translation-type: tm+mt
source-git-commit: 8a25259732a916f977f733cd22971b1d847aae5f

---


# 모바일 앱 획득 {#mobile-app-acquisition}

Adobe Mobile Services에서 고유한 추적 코드가 있는 획득 링크를 생성할 수 있습니다. 사용자가 생성된 링크를 클릭한 후 앱스토어에서 앱을 다운로드하여 실행하면 SDK에서 자동으로 획득 데이터를 수집하여 Adobe Mobile Services로 보냅니다.

## 새로운 Adobe Experience Platform Mobile SDK 릴리스

Adobe Experience Platform Mobile SDK와 관련된 정보 및 문서 찾기 최신 문서를 보려면 [여기](https://aep-sdks.gitbook.io/docs/)를 클릭하십시오.

2018년 9월 일자로 SDK의 새로운 주요 버전을 릴리스하였습니다. 이러한 새로운 Adobe Experience Platform Mobile SDK는 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html)를 통해 구성할 수 있습니다.

* 시작하려면 Adobe Experience Platform Launch로 이동합니다.
* Experience Platform SDK 리포지토리의 항목을 보려면 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)로 이동하십시오.

>[!IMPORTANT]
>
>획득을 사용하려면 **반드시** SDK 버전 4.1 이상이 있어야 합니다.

획득 링크는 Adobe Mobile Services에서 만들어야 합니다. 자세한 내용은 [획득](/help/using/acquisition-main/acquisition-main.md)을 참조하십시오.

**SDK 버전 4.18.0 이상**:

2020년 3월 1일부터 Google은 install_referrer intent broadcast 메커니즘을 더 이상 사용하지 않습니다. 자세한 내용은 InstallBroadcast [사용을 참조하십시오. 2020년 3월 1일까지 Play Referrer API로 전환](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html)을 참조하십시오. Google Play 스토어에서 설치 레퍼러 정보를 계속 수집하려면 SDK 버전 4.18.0 이상을 사용하도록 응용 프로그램을 업데이트하십시오.

사용 중단 시 SDK를 만드는 대신 새 Google API에서 설치 레퍼러 URL을 `BroadcastReceiver`수집하고 결과 URL을 SDK에 전달해야 합니다.

1. Google Play 설치 레퍼러 패키지를 일반 파일의 종속성에 추가합니다.

   `implementation 'com.android.installreferrer:installreferrer:1.1'`

1. Install Referrer API에서 레퍼러 URL을 검색하려면 설치 레퍼러 [가져오기의 단계를 완료하십시오](https://developer.android.com/google/play/installreferrer/library#install-referrer).

1. 레퍼러 URL을 SDK에 전달합니다.

   `Analytics.processGooglePlayInstallReferrerUrl(referrerUrl);`

>[!IMPORTANT]
>
>앱에서 불필요한 API 호출을 방지하려면 설치 후 바로 API를 한 번만 호출하는 것이 좋습니다.

앱에서 Google Play 설치 레퍼러 API를 사용하는 최상의 방법을 결정하려면 Google 설명서를 참조하십시오. 다음은 Google Play Install Referrer API와 함께 Adobe SDK를 사용하는 방법의 예입니다.

```java
void handleGooglePlayReferrer() {
    // Google recommends only calling this API the first time you need it:
    // https://developer.android.com/google/play/installreferrer/library#install-referrer

    // Store a boolean in SharedPreferences to ensure we only call it once.
    final SharedPreferences prefs = getSharedPreferences("acquisition", 0);
    if (prefs != null) {
        if (prefs.getBoolean("referrerHasBeenProcessed", false)) {
            return;
        }
    }

    final InstallReferrerClient referrerClient = InstallReferrerClient.newBuilder(getApplicationContext()).build();
    referrerClient.startConnection(new InstallReferrerStateListener() {
        private boolean complete = false;

        @Override
        public void onInstallReferrerSetupFinished(int responseCode) {
            switch (responseCode) {
                case InstallReferrerClient.InstallReferrerResponse.OK:
                    // connection is established
                    complete();
                    try {
                        final ReferrerDetails details = referrerClient.getInstallReferrer();                        

                        // pass the install referrer url to the SDK
                        Analytics.processGooglePlayInstallReferrerUrl(details.getInstallReferrer());

                    } catch (final RemoteException ex) {
                        Log.w("Acquisition - RemoteException while retrieving referrer information (%s)", ex.getLocalizedMessage() == null ? "unknown" : ex.getLocalizedMessage());
                    } finally {
                        referrerClient.endConnection();
                    }
                    break;
                case InstallReferrerClient.InstallReferrerResponse.FEATURE_NOT_SUPPORTED:
                case InstallReferrerClient.InstallReferrerResponse.SERVICE_UNAVAILABLE:
                default:
                    // API not available in the Play Store app - nothing to do here
                    complete();
                    referrerClient.endConnection();
                    break;
            }
        }

        @Override
        public void onInstallReferrerServiceDisconnected() {
            if (!complete) {
                // something went wrong trying to get a connection, try again
                referrerClient.startConnection(this);
            }
        }

        void complete() {
            complete = true;
            SharedPreferences.Editor editor = getSharedPreferences("acquisition", 0).edit();
            editor.putBoolean("referrerHasBeenProcessed", true);
            editor.apply();
        }
    });
}
```

**SDK 버전 4.13.1 이상**:

Adobe Mobile Services에서 생성된 획득 링크를 사용할 수 없는 경우 Google Play 획득을 사용하여 획득 데이터를 수집할 수 있고 SDK에서 보낼 수 있습니다.

표준 Google Play 획득 캠페인에서 획득 데이터를 수집하는 방법은 다음과 같습니다.

* 표준 Google Play 스토어 획득 메서드를 사용합니다.

   사용자 지정 획득 데이터는 표준 Google Play Acquisition 키 값 쌍과 함께 사용할 수 있습니다.

* 사용자가 Google Play 스토어를 통해 앱을 다운로드하고 실행하면 레퍼러의 데이터가 획득되어 Adobe Mobile Services로 전송됩니다.

   * 데이터는 저장되고 SDK와 함께 이전에 등록된 `AdobeDataCallback` 인스턴스에서 사용할 수 있습니다.

      자세한 내용은 [구성 메서드](/help/android/configuration/methods.md)를 참조하십시오.

   * `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` 또는 `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` 이벤트 유형이 사용됩니다.

   * Google Play에서 획득한 데이터의 일부인 사용자 지정 키의 이름은 &quot;`a.acquisition.custom.`&quot;.&quot;으로 지정됩니다.

Adobe Mobile Services에서 만든 획득 링크를 사용하는 경우 다음 작업을 완료하여 획득 링크에 사용자 지정 데이터를 추가하십시오.

1. 획득 변수 접두사로 &quot;`adb`&quot;를 사용합니다.

   SDK가 처음 실행 시 Adobe Mobile Services로부터 획득 데이터를 받으면 데이터가 저장되고 SDK에 이전에 등록한 `AdobeDataCallback` 인스턴스에서 사용할 수 있습니다. 자세한 내용은 [구성 메서드](/help/android/configuration/methods.md)를 참조하십시오.

1. `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` 또는 `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` 이벤트 유형이 사용됩니다.

1. 사용자 지정 데이터 키의 접두사로 &quot;`a.acquisition.custom.`&quot;이 사용됩니다.

>[!TIP]
>
>여러 보고서 세트로 데이터를 보내는 경우 보고서 세트 ID 목록의 첫 번째 보고서 세트와 연결된 앱의 획득 데이터를 사용하십시오.

이 섹션의 업데이트를 통해 SDK는 획득 링크에서 획득 데이터를 전송할 수 있습니다.

## 모바일 획득 추적 {#section_CEA30C652AC8470784B8054E299B80FA}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 [핵심 구현 및 라이프사이클](/help/android/getting-started/dev-qs.md)에서 *IntelliJ IDEA 또는 Eclipse 프로젝트에 SDK 및 구성 파일 추가*&#x200B;를 참조하십시오.

1. 라이브러리를 가져옵니다:

   ```java
   import com.adobe.mobile.*;
   ```

1. 레퍼러에 대해 `BroadcastReceiver`를 구현합니다.

   ```java
   package com.your.package.name;  // replace with your app package name
   
   import android.content.BroadcastReceiver;
   import android.content.Context;
   import android.content.Intent;
   
   public class GPBroadcastReceiver extends BroadcastReceiver {
     @Override
     public void onReceive(Context c, Intent i) {
      com.adobe.mobile.Analytics.processReferrer(c, i);
     }
   }
   ```

1. `AndroidManifest.xml`을 업데이트하여 이전 단계에서 생성된 `BroadcastReceiver`를 사용하도록 설정합니다.

   ```xml
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
    <intent-filter>
     <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
   </receiver>
   ```

1. `ADBMobileConfig.json` 파일에 필요한 획득 설정이 포함되어 있는지 확인합니다.

   ```xml
   "acquisition": {
      "server": "c00.adobe.com",
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f"
   },
   "analytics": {
     "referrerTimeout": 5,
     ...
   ```

   >[!IMPORTANT]
   >
   > 여러 보고서 세트로 데이터를 보내는 경우 보고서 세트 ID 목록의 첫 번째 보고서 세트와 연결된 앱의 획득 설정(획득 서버 및 appid)을 사용하십시오.

   `acquisition` 설정은 Adobe Mobile Services에 의해 생성되므로 변경해서는 안 됩니다. `acquisition` 설정이 미리 구성된 사용자 지정 `ADBMobileConfig.json` 파일을 다운로드하는 방법에 대한 자세한 내용은 [시작하기 전에](/help/android/getting-started/requirements.md)를 참조하십시오.

이 설정을 사용하면 첫 번째 앱 시작 이후 초기 라이프사이클 호출과 함께 획득 데이터가 자동으로 전송됩니다.

>[!CAUTION]
>
>`referrerTimeout`  앱 획득을 사용하려면 을 0보다 큰 값으로 설정해야 합니다.
