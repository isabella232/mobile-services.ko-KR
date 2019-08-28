---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: 프로젝트 빌드
solution: Marketing Cloud, 개발자
title: 프로젝트 빌드
uuid: 5550 A 394-6 F 3 F -4 B 87-B 840-89621 D 8 A 0 C 1 E
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Building your project{#building-your-project}

## iOS

iOS용을 빌드할 경우 Xcode 프로젝트가 생성됩니다. 기본적으로 `ADBMobileWrapper.mm` 및 `AdobeMobileLibrary.a` 파일이 새 프로젝트 라이브러리 그룹에 생깁니다. 앱을 빌드하기 위해 요구되는 다음 수동 단계를 수행하십시오.

1. `ADBMobileConfig.json` 파일을 프로젝트에 추가합니다.

   어떤 타겟에서도 필요한 빌드의 구성원인지 확인합니다.

1. In the **[!UICONTROL Build Phases]** tab of your project, add a link to the following libraries:

   * `SystemConfiguration.framework`(이 라이브러리는 이미 연결되어 있을 수 있습니다.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>To use Local Notification In-App messages from the SDK, you must call `ADBMobile.EnableLocalNotifications();` from the Start method in your first Unity Scene.

## Android

Android용을 빌드할 경우 `apk` 파일에는 이미 `ADBMobileConfig.json` 파일이 올바른 위치에 포함되어 있습니다. By default, the `AndroidManifest.xml` file in your `/Plugins/Android` folder is also used.

고유한 사용자 지정 매니페스트 파일을 사용해야 할 경우 다음 변경 사항을 추가해야 합니다.

다음에 대한 권한 추가:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

인앱 메시지를 사용하는 경우 다음 활동 및 수신기를 추가합니다.

```java
<activity android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" /> 
```

획득을 사용하는 경우 다음 수신기를 추가합니다.

```java
<receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true"> 
   <intent-filter> 
      <action android:name="com.android.vending.INSTALL_REFERRER" /> 
   </intent-filter> 
</receiver>
```
