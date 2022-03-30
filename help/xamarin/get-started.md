---
description: 이 항목에서는 모바일 솔루션 4.x SDK용 Xamarin 구성 요소를 사용하여 시작하는 방법에 대해 설명합니다.
keywords: Xamarin
solution: Experience Cloud Services
title: Experience Cloud 솔루션 4.x SDK용 Xamarin 구성 요소
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
exl-id: 39628548-5787-4022-8792-86b78214a1c0
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 99%

---

# Experience Cloud 솔루션 4.x SDK용 Xamarin 구성 요소 {#xamarin-components-for-experience-cloud-solutions-x-sdk}

이 항목에서는 모바일 솔루션 4.x SDK용 Xamarin 구성 요소를 사용하여 시작하는 방법에 대해 설명합니다.

마지막 업데이트 날짜: **2019년 1월 10일**

## 시작하기 {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>Adobe Mobile SDK는 Xamarin 구성 요소 스토어 또는 NuGet 갤러리에서 더 이상 사용할 수 없습니다. Xamarin 구성 요소를 다운로드하려면 [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services)로 이동합니다.

## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

ADBMobile 구성 요소를 Xamarin.Android 프로젝트로 가져오기:

1. Xamarin 프로젝트를 엽니다.
1. **[!UICONTROL 참조]** 대화 상자를 열고 **[!UICONTROL .Net 어셈블리]** 탭을 클릭합니다.
1. **[!UICONTROL lib/Android]** 폴더에서 `ADBMobile.XamarinAndroidBinding.dll`을(를) 선택합니다.
1. 프로젝트의 **[!UICONTROL Assets]** 폴더에 `ADBMobileConfig.json` 파일을 추가합니다.
1. 다음에 대한 권한 추가:

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`

   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. 인앱 메시징을 사용하는 경우, 다음 활동 및 수신기를 추가합니다.

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

ADBMobile 구성 요소를 Xamarin.iOS 프로젝트로 가져오기:

1. Xamarin 프로젝트를 엽니다.
1. **[!UICONTROL 참조]** 대화 상자를 열고 **[!UICONTROL .Net 어셈블리]** 탭을 클릭합니다.
1. **[!UICONTROL lib/ios-unified]** 폴더에서 `ADBMobile.XamarinIOSBinding.dll`을(를) 선택합니다.
1. 프로젝트에 `ADBMobileConfig.json` 파일을 추가합니다.
