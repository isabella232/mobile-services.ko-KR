---
description: 이 항목에서는 Mobile solutions 4.x SDK용 Xamarin 구성 요소를 사용하여 시작하는 방법에 대해 설명합니다.
keywords: Xamarin
seo-description: 이 항목에서는 Mobile solutions 4.x SDK용 Xamarin 구성 요소를 사용하여 시작하는 방법에 대해 설명합니다.
seo-title: Experience Cloud 솔루션 4.x SDK용 Xamarin 구성 요소
solution: Marketing Cloud,Developer
title: Experience Cloud 솔루션 4.x SDK용 Xamarin 구성 요소
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 5%

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

이 항목에서는 Mobile solutions 4.x SDK용 Xamarin 구성 요소를 사용하여 시작하는 방법에 대해 설명합니다.

Last Updated: **January 10, 2019**

## 시작하기 {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>Adobe Mobile SDK는 Xamarin 구성 요소 스토어 또는 NuGet 갤러리에서 더 이상 사용할 수 없습니다. Xamarin 구성 요소를 다운로드하려면 [GitHub로 이동합니다](https://github.com/Adobe-Marketing-Cloud/mobile-services).

## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

ADBMobile 구성 요소를 Xamarin.Android 프로젝트로 가져옵니다.

1. Xamarin 프로젝트 열기
1. 참조( **[!UICONTROL References]** ) 대화 상자를 열고 **[!UICONTROL .Net 어셈블리]** 탭을 클릭합니다.
1. lib/ `ADBMobile.XamarinAndroidBinding.dll` Android **** 폴더에서 선택합니다.
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

ADBMobile 구성 요소를 Xamarin.iOS 프로젝트로 가져옵니다.

1. Xamarin 프로젝트를 엽니다.
1. 참조( **[!UICONTROL References]** ) 대화 상자를 열고 **[!UICONTROL .Net 어셈블리]** 탭을 클릭합니다.
1. lib/ios-unified `ADBMobile.XamarinIOSBinding.dll` 폴더 **** 에서 선택합니다.
1. 프로젝트에 `ADBMobileConfig.json` 파일 추가
