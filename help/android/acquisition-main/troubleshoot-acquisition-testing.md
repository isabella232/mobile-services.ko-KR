---
description: 이 항목에서는 획득 테스트 중에 발생할 수 있는 문제를 해결하는 방법에 대한 정보를 제공합니다.
keywords: Android; 라이브러리; 모바일; SDK
seo-description: 이 항목에서는 획득 테스트 중에 발생할 수 있는 문제를 해결하는 방법에 대한 정보를 제공합니다.
seo-title: 고객 확보 테스트 문제 해결
solution: Marketing Cloud, Analytics
title: 고객 확보 테스트 문제 해결
topic: 개발자 및 구현
translation-type: tm+mt
source-git-commit: 97202c672d7349496f83b9ac0c365dd8b3e13eda

---


# 고객 확보 테스트 문제 해결 {#troubleshoot-acquisition-testing}

이 항목에서는 획득 테스트 중에 발생할 수 있는 문제를 해결하는 방법에 대한 정보를 제공합니다.

* 다르게 지정하지 않으면 Adbmobileconfig. json 파일을 `assets` 폴더에 넣어야 합니다.

   이름은 대/소문자를 구분하므로 대/소문자를 구분하지 마십시오.

* 주 활동에서 `Config.setContext(this.getApplicationContext())` 호출되었는지 확인합니다.

   자세한 내용은 [구성 방법을](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)참조하십시오.

* Mobile SDK에 필요한 권한이 `AndroidManifest.xml` 파일에 있는지 확인합니다.

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Admobileconfig. json 파일에서를 `referrerTimeout` 5로 설정하면 응용 프로그램이 처음 설치 및 실행된 후 설치 히트에 추가된 레퍼러 정보를 볼 수 있도록 5 초 기간의 설치 의도를 보내야 합니다.

   수동 테스트의 경우, 설치 히트가 처리되기 전에 레퍼러 정보를 전송할 충분한 시간이 있도록 10-15 `referrerTimeout` 초 간격을 늘리는 것이 좋습니다.

* 마케팅 링크 [획득의](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) 모든 단계를 실행하고 `adb shell` 먼저 명령을 실행하고 다음을 수행합니다.

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>레퍼러 의도를 올바로 처리하려면 이 두 명령을 독립적으로 실행해야 합니다. 그렇지 `adb` 않으면 레퍼러 정보를 두 번 이스케이프 처리하면 브로드캐스트 수신기가 수신한 데이터가 불완전해집니다.

