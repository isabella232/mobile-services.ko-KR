---
description: The following information helps you troubleshoot Acquisition testing issues.
keywords: android;Acquisition;testing
seo-description: The following information helps you troubleshoot Acquisition testing issues.
seo-title: Troubleshooting Acquisition testing
solution: Marketing Cloud,Analytics
title: Troubleshooting Acquisition testing
translation-type: tm+mt
source-git-commit: da8798d7ee1f05dcade31cced5404d78c9cf360a

---


# Troubleshooting Acquisition testing {#aquistion-testing-troubleshooting}

다음은 고객 확보 및 일부 가능한 솔루션을 테스트할 때 발생할 수 있는 몇 가지 문제입니다.

* 별도로 지정하지 않는 경우 ADBMobileConfig.json 파일을 assets 폴더에 저장해야 합니다.

* 이름은 대/소문자를 구분하므로 소문자를 구분하지 않습니다.

   주 활동에서 `Config.setContext(this.getApplicationContext())` 호출되도록 해야 합니다. 자세한 내용은 구성 [방법을](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)참조하십시오.

* 제공된 AndroidManifest.xml 파일에서 몇 가지 사용자 권한이 없습니다. 이러한 권한은 데이터를 보내고 오프라인 추적 호출을 기록하는 데 필요합니다.

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* 구성에서 레퍼러 시간 초과가 설정된 `referrerTimeout: 5`경우, 이것은 애플리케이션이 설치 및 시작된 후 5초 내에 설치 의도를 전송해야 설치 히트에 추가된 레퍼러 정보를 볼 수 있음을 의미합니다.

   수동 테스트의 경우 설치 히트가 처리되기 전에 레퍼러 정보를 전송할 충분한 시간이 있도록 10-15 `referrerTimeout` 초로 늘리십시오.

* Marketing Link 획득의 모든 단계를 순서대로 [실행하고](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) `adb` 셸을 실행한 다음 다음을 수행해야 합니다.

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>레퍼러 의도를 올바르게 처리하려면 이 두 명령을 독립적으로 실행해야 합니다.  그렇지 않으면 레퍼러 정보가 두 번 이스케이프되고 `adb` 브로드캐스트 수신자가 받은 데이터가 불완전합니다.
