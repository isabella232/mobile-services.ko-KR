---
description: 이 항목에서는 획득 테스트 중에 발생할 수 있는 문제를 해결하는 방법에 대해 설명합니다.
keywords: android;라이브러리;모바일;sdk
seo-description: 이 항목에서는 획득 테스트 중에 발생할 수 있는 문제를 해결하는 방법에 대해 설명합니다.
seo-title: 획득 테스트 문제 해결
solution: Marketing Cloud,Analytics
title: 획득 테스트 문제 해결
topic: 개발자 및 구현
translation-type: ht
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# 획득 테스트 문제 해결 {#troubleshoot-acquisition-testing}

이 항목에서는 획득 테스트 중에 발생할 수 있는 문제를 해결하는 방법에 대해 설명합니다.

* 별도로 지정하지 않는 경우 ADBMobileConfig.json 파일을 `assets` 폴더에 두어야 합니다.

   이름은 대/소문자를 구분하므로 대문자나 소문자는 사용하지 마십시오.

* 기본 활동에서 `Config.setContext(this.getApplicationContext())`가 호출되는지 확인합니다.

   자세한 내용은 [구성 메서드](https://docs.adobe.com/content/help/ko-KR/mobile-services/android/configuration-android/methods.html)를 참조하십시오.

* Mobile SDK에 필요한 권한이 `AndroidManifest.xml` 파일에 있는지 확인합니다.

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* ADMobileConfig.json 파일에서 `referrerTimeout`이 5로 설정된 경우 애플리케이션이 설치되고 처음 실행된 후 5초 이내에 설치 의도를 전달하여 설치 히트에 추가된 레퍼러 정보를 확인해야 합니다.

   수동 테스트의 경우 설치 히트가 처리되기 전에 레퍼러 정보를 전송할 시간이 충분하도록 `referrerTimeout`을 10~15초로 늘리는 것이 좋습니다. 

* [마케팅 링크 획득 테스트](https://docs.adobe.com/content/help/ko-KR/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html)의 모든 단계를 실행하고 `adb shell` 명령을 먼저 실행한 후 다음을 확인합니다.

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>레퍼러 의도를 올바르게 처리하려면 이 두 명령을 독립적으로 실행해야 합니다. 독립적으로 실행하지 않으면 `adb`가 레퍼러 정보를 두 번 이스케이프하므로 브로드캐스트 수신기가 수신한 데이터가 불완전할 수 있습니다.

