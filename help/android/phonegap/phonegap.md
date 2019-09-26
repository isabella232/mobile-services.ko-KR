---
description: 이 플러그인을 사용하여 PhoneGap 프로젝트에서 Android AppMeasurement 호출을 전송할 수 있습니다.
keywords: android;library;mobile;sdk
seo-description: 이 플러그인을 사용하여 PhoneGap 프로젝트에서 Android AppMeasurement 호출을 전송할 수 있습니다.
seo-title: PhoneGap 플러그인 개요
solution: Marketing Cloud,Analytics
title: PhoneGap 플러그인 개요
topic: 개발자 및 구현
uuid: c5c32357-d8df-458a-b0e8-e0c56040241d
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# PhoneGap 플러그인 개요 {#phonegap-plug-in}

이 플러그인을 사용하여 PhoneGap 프로젝트에서 Android AppMeasurement 호출을 전송할 수 있습니다. PhoneGap 프로젝트를 만들려면 PhoneGap [을 참조하십시오](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html).

## 새 Adobe Experience Cloud SDK 릴리스

Adobe Experience Platform Mobile SDK와 관련된 정보 및 문서 찾기 최신 문서를 보려면 [여기](https://aep-sdks.gitbook.io/docs/)를 클릭하십시오.

>[!IMPORTANT]
>
>2018년 9월 일자로 SDK의 새로운 주요 버전을 릴리스하였습니다. 이러한 새로운 Adobe Experience Platform Mobile SDK는 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html)를 통해 구성할 수 있습니다.

* 시작하려면 [Launch](https://launch.adobe.com/)로 이동합니다.
* Experience Platform SDK 리포지토리의 항목을 보려면 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)로 이동하십시오.


## npm으로 플러그인 설치 {#section_43229E57C16944C0B51531CB92089189}

다음 명령을 실행합니다.

```java
cordova plugin add adobe-mobile-services
```

## 수동으로 플러그인 설치 {#section_EA1FD59C484D44878AB509954DEE6037}

## 플러그인 포함

1. 파일을 `ADBMobile_PhoneGap.java` 폴더로 `src` 드래그합니다.

   이 파일을 이동하려면 **[!UICONTROL 확인을 클릭하십시오]**.

1. 파일을 `ADB_Helper.js` 포함하는 폴더로 `index.html` 드래그합니다

   이 파일을 이동하려면 **[!UICONTROL 확인을 클릭하십시오]**.

1. In the `res/xml` folder, open the `config.xml` file and register an new plugin by adding the following:

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   예를 들어 패키지의 이름이 `com.example.phonegaptest`인 경우 `android-package` 값은 다음과 같습니다.

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## Include the AppMeasurement library

1. To download the AppMeasurement library, see [Get the SDK](/help/android/getting-started/dev-qs.md).
1. 파일을 `adobeMobileLibrary.jar` 폴더로 `src` 드래그합니다.

   이 파일을 이동하려면 **[!UICONTROL 확인을 클릭하십시오]**.

1. Right-click the `adobeMobileLibrary.jar file and select **[!UICONTROL Add as Library]**.
1. 프로젝트의 요구 사항에 따라 라이브러리의 이름, 수준 및 위치를 입력하십시오.
1. Drag the `ADBMobileConfig.json` file to your `assets` folder in the application root.
1. 애플리케이션 내의 애플리케이션이 **아니라** 루트 애플리케이션을 선택했는지 확인합니다.

   이 파일을 이동하려면 **[!UICONTROL 확인을 클릭하십시오]**.

## 앱 권한 추가

AppMeasurement 라이브러리를 사용하려면 데이터를 전송하고 오프라인 추적 호출을 기록할 다음 권한이 필요합니다.

* `INTERNET`
* `ACCESS_NETWORK_STATE`

이러한 권한을 추가하려면 애플리케이션 프로젝트 디렉터리의 `AndroidManifest.xml` 파일에 다음 줄을 추가하십시오.

```xml
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

인앱 메시지를 활성화하려면

AndroidManifest.xml을 업데이트하여 전체 화면 활동을 선언하고 메시지 알림 핸들러를 사용하도록 설정합니다.

```java
<activity  
android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

Adobe Mobile Services에서 메시지를 생성할 때 양식 레이아웃을 선택하는 경우 다음 테마 중 하나를 선택하십시오.

* `Theme.Translucent.NoTitleBar.Fullscreen`
* `Theme.Translucent.NoTitleBar`
* `Theme.Translucent`

예:

```java
<activity 
android:name="com.adobe.mobile.MessageFullScreenActivity" 
android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

## Implement custom tracking {#section_FD102B3CDAA4492FB04E56BF17E28663}

In `html` files, add the following to the `<head>` tag where you want to use tracking:

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

