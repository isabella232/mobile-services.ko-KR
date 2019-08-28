---
description: 다음 정보는 획득 테스트 문제를 해결하는 데 도움이 됩니다.
keywords: Android; 획득; 테스트
seo-description: 다음 정보는 획득 테스트 문제를 해결하는 데 도움이 됩니다.
seo-title: 획득 테스트 문제 해결
solution: Marketing Cloud, Analytics
title: 획득 테스트 문제 해결
translation-type: tm+mt
source-git-commit: da8798d7ee1f05dcade31cced5404d78c9cf360a

---


# 획득 테스트 문제 해결 {#aquistion-testing-troubleshooting}

다음은 테스트 확보 시 발생할 수 있는 몇 가지 문제와 일부 가능한 솔루션입니다.

* 다르게 지정하지 않으면 Adbmobileconfig. json 파일을 Assets 폴더에 넣어야 합니다.

* 이름은 대/소문자를 구분하므로 소문자로 이름을 제공하지 마십시오.

   주 활동에서 `Config.setContext(this.getApplicationContext())` 호출되도록 해야 합니다. 자세한 내용은 [구성 방법을](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)참조하십시오.

* 제공된 AndroidManifest.xml 파일에서 누락된 사용자 권한이 있습니다. 이러한 권한은 데이터를 전송하고 오프라인 추적 호출을 기록하는 데 필요합니다.

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* 구성에서 레퍼러 시간 초과가로 `referrerTimeout: 5`설정된 경우, 애플리케이션을 처음 설치 및 실행한 후 설치 히트에 추가된 레퍼러 정보를 보려면 설치 의도를 5 초 안에 보내야 합니다.

   수동 테스트의 경우, 설치 히트가 처리되기 전에 레퍼러 정보를 전송할 충분한 시간이 있도록 10-15 `referrerTimeout` 초 값을 늘립니다.

* 마케팅 링크 획득을 [순서대로 테스트하는 모든 단계를](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) 실행하고 셸을 실행하고 `adb` 다음을 수행해야 합니다.

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>레퍼러 의도를 제대로 처리하려면 이 두 명령을 독립적으로 실행해야 합니다. 그렇지 않으면, 두 번 레퍼러 정보가 `adb` 중복되고 브로드캐스트 수신기가 수신한 데이터가 불완전해집니다.
