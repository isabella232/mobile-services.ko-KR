---
description: 다음 정보는 획득 테스트 문제를 해결하는 데 유용합니다.
keywords: android;Acquisition;testing
seo-description: 다음 정보는 획득 테스트 문제를 해결하는 데 유용합니다.
seo-title: 획득 테스트 문제 해결
solution: Experience Cloud,Analytics
title: 획득 테스트 문제 해결
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '251'
ht-degree: 100%

---


# 획득 테스트 문제 해결 {#aquistion-testing-troubleshooting}

다음은 획득 및 몇 가지 가능한 솔루션을 테스트할 때 발생할 수 있는 몇 가지 문제입니다.

* 별도로 지정하지 않는 경우 ADBMobileConfig.json 파일을 assets 폴더에 두어야 합니다.

* 이름은 대/소문자를 구분하므로 소문자를 이름을 지정하지 마십시오.

   `Config.setContext(this.getApplicationContext())`가 기본 활동에서 호출되는지 확인해야 합니다. 자세한 내용은 [구성 메서드](https://docs.adobe.com/content/help/ko-KR/mobile-services/android/configuration-android/methods.html)를 참조하십시오.

* 제공된 AndroidManifest.xml 파일에 몇 가지 사용자 권한이 누락되었습니다. 이러한 권한은 데이터를 보내고 오프라인 추적 호출을 기록하는 데 필요합니다.

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* 구성에서 레퍼러 제한 시간이 `referrerTimeout: 5`로 설정된 경우 설치 히트에 추가된 레퍼러 정보를 확인하려면 애플리케이션이 설치되고 처음 실행된 후 5초 이내에 설치 의도를 전달해야 함을 의미합니다.

   수동 테스트의 경우 설치 히트가 처리되기 전에 레퍼러 정보를 전송할 시간이 충분하도록 `referrerTimeout`을 10~15초로 늘리십시오.

* [마케팅 링크 획득 테스트](https://docs.adobe.com/content/help/ko-KR/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html)의 모든 단계를 순서대로 실행하고 `adb` 셸을 실행한 후 다음을 실행해야 합니다.

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>레퍼러 의도를 올바르게 처리하려면 이 두 명령을 독립적으로 실행해야 합니다. 독립적으로 실행하지 않으면 `adb`가 레퍼러 정보를 두 번 이스케이프하므로 브로드캐스트 수신기가 수신한 데이터가 불완전할 수 있습니다.
