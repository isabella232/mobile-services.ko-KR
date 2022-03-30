---
description: iOS 프로젝트 빌드
keywords: Unity
solution: Experience Cloud Services
title: 프로젝트 빌드
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
exl-id: 9da99392-b34e-4e36-b255-f3787e26015c
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 18%

---

# 프로젝트 빌드{#building-your-project}

## iOS

iOS용으로 빌드하면 Xcode 프로젝트가 만들어집니다. 기본적으로 `ADBMobileWrapper.mm` 및  `AdobeMobileLibrary.a` 파일은 새 프로젝트의 라이브러리 그룹에 있습니다. 앱을 빌드하려면 다음 수동 단계를 수행하십시오.

1. 프로젝트에 `ADBMobileConfig.json` 파일을 추가합니다.

   필요한 모든 타겟이 빌드의 구성원인지 확인합니다.

1. 에서 **[!UICONTROL 빌드 단계]** 프로젝트의 탭에서 다음 라이브러리에 링크를 추가합니다.

   * `SystemConfiguration.framework`
(이 라이브러리는 이미 연결되어 있을 수 있습니다.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>SDK에서 로컬 알림 인앱 메시지를 사용하려면 를 호출해야 합니다 `ADBMobile.EnableLocalNotifications();` 첫 번째 Unity 장면의 시작 메서드에서 사용할 수 있습니다.

## Android

Android용 빌드를 만들 때 `apk` 파일에 이미 포함되어 있습니다. `ADBMobileConfig.json` 올바른 위치에 있는 파일입니다. 기본적으로 `AndroidManifest.xml` 파일의 `/Plugins/Android` 폴더도 사용됩니다.

고유한 사용자 지정 매니페스트 파일을 사용해야 하는 경우 다음 변경 사항을 추가해야 합니다.

다음에 대한 권한 추가:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

```java
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

인앱 메시징을 사용하는 경우, 다음 활동 및 수신기를 추가합니다.

```java
<activity android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" />
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```
