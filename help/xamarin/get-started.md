---
description: 이번 주제에서는 Mobile solutions 4.x SDK용 Xamarin 구성 요소를 사용하여 시작하는 방법을 설명합니다.
keywords: Xamarin
seo-description: 이번 주제에서는 Mobile solutions 4.x SDK용 Xamarin 구성 요소를 사용하여 시작하는 방법을 설명합니다.
seo-title: Experience Cloud solutions 4. x SDK 용 Xamarin 구성 요소
solution: Marketing Cloud, 개발자
title: Experience Cloud solutions 4. x SDK 용 Xamarin 구성 요소
uuid: E 7 A 48107-BD 0 E -47 D 6-B 49 C-DFDAE 189 AC 37
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

이번 주제에서는 Mobile solutions 4.x SDK용 Xamarin 구성 요소를 사용하여 시작하는 방법을 설명합니다.

마지막 업데이트 날짜:**2019년 1월 10일**

## 시작하기 {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>Adobe Mobile SDK는 더 이상 Xamarin 구성 요소 스토어 또는 Nuget 갤러리에서 제공되지 않습니다. Xamarin 구성요소를 다운로드하려면 [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services)이로 이동하십시오.


## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

Adbmobile 구성 요소를 Xamarin. Android 프로젝트로 가져옵니다.

1. Xamarin 프로젝트 열기

1. **[!UICONTROL 참조]** 대화 상자를 열고. NET **[!UICONTROL 어셈블리]** 탭을 클릭합니다.

1. `ADBMobile.XamarinAndroidBinding.dll`**[!UICONTROL lib/android]** 폴더에서 선택합니다.

1. Add your `ADBMobileConfig.json` file to the **[!UICONTROL Assets]** folder of your project.

1. 다음에 대한 권한 추가:

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`

   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. 인앱 메시지를 사용하는 경우 다음 활동 및 수신기를 추가합니다.

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar" />
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. 획득을 사용하는 경우 다음 수신기를 추가합니다.

   ```java
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
   <intent-filter>
       <action android:name="com.android.vending.INSTALL_REFERRER" />
   </intent-filter>
   </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

Adbmobile 구성 요소를 Xamarin. iOS 프로젝트로 가져옵니다.

1. Xamarin 프로젝트를 엽니다.
1. **[!UICONTROL 참조]** 대화 상자를 열고. NET **[!UICONTROL 어셈블리]** 탭을 클릭합니다.

1. `ADBMobile.XamarinIOSBinding.dll`**[!UICONTROL lib/ios 통합]** 폴더에서 선택합니다.

1. `ADBMobileConfig.json` 파일을 프로젝트에 추가합니다.


