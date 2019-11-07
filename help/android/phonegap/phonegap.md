---
description: 이 플러그인을 사용하여 PhoneGap 프로젝트에서 Android AppMeasurement 호출을 전송할 수 있습니다.
keywords: android;라이브러리;모바일;sdk
seo-description: 이 플러그인을 사용하여 PhoneGap 프로젝트에서 Android AppMeasurement 호출을 전송할 수 있습니다.
seo-title: PhoneGap 플러그인 개요
solution: Marketing Cloud,Analytics
title: PhoneGap 플러그인 개요
topic: 개발자 및 구현
uuid: c5c32357-d8df-458a-b0e8-e0c56040241d
translation-type: ht
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# PhoneGap 플러그인 개요 {#phonegap-plug-in}

이 플러그인을 사용하여 PhoneGap 프로젝트에서 Android AppMeasurement 호출을 전송할 수 있습니다. PhoneGap 프로젝트를 만들려면 [PhoneGap](https://helpx.adobe.com/kr/experience-manager/6-4/mobile/using/phonegap.html)을 참조하십시오.

## 새로운 Adobe Experience Platform Mobile SDK 릴리스

Adobe Experience Platform Mobile SDK와 관련된 정보 및 문서 찾기 최신 문서를 보려면 [여기](https://aep-sdks.gitbook.io/docs/)를 클릭하십시오.

2018년 9월 일자로 SDK의 새로운 주요 버전을 릴리스하였습니다. 이러한 새로운 Adobe Experience Platform Mobile SDK는 [Experience Platform Launch](https://www.adobe.com/kr/experience-platform/launch.html)를 통해 구성할 수 있습니다.

* 시작하려면 Adobe Experience Platform Launch로 이동합니다.
* Experience Platform SDK 리포지토리의 항목을 보려면 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)로 이동하십시오.


## npm으로 플러그인 설치 {#section_43229E57C16944C0B51531CB92089189}

다음 명령을 실행합니다.

```java
cordova plugin add adobe-mobile-services
```

## 수동으로 플러그인 설치 {#section_EA1FD59C484D44878AB509954DEE6037}

## 플러그인 포함

1. `ADBMobile_PhoneGap.java` 파일을 `src` 폴더로 드래그합니다.

   이 파일을 이동하려면 **[!UICONTROL 확인을 클릭하십시오]**.

1. `ADB_Helper.js` 파일을 `index.html` 파일이 포함된 폴더로 드래그합니다.

   이 파일을 이동하려면 **[!UICONTROL 확인을 클릭하십시오]**.

1. `res/xml` 폴더에서 `config.xml` 파일을 열고 다음을 추가하여 새 플러그인을 등록합니다.

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   예를 들어 패키지의 이름이 `com.example.phonegaptest`인 경우 `android-package` 값은 다음과 같습니다.

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## AppMeasurement 라이브러리 포함

1. AppMeasurement 라이브러리를 다운로드하려면 [SDK 가져오기](/help/android/getting-started/dev-qs.md)를 참조하십시오.
1. `adobeMobileLibrary.jar` 파일을 `src` 폴더로 드래그합니다.

   이 파일을 이동하려면 **[!UICONTROL 확인을 클릭하십시오]**.

1. adobeMobileLibrary.jar 파일을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 라이브러리로 추가]**&#x200B;를 선택합니다.
1. 프로젝트의 요구 사항에 따라 라이브러리의 이름, 수준 및 위치를 입력하십시오.
1. `ADBMobileConfig.json` 파일을 애플리케이션 루트의 `assets` 폴더로 드래그합니다.
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

## 사용자 지정 추적 구현 {#section_FD102B3CDAA4492FB04E56BF17E28663}

`html` 파일에서 추적을 사용할 `<head>` 태그에 다음을 추가하십시오.

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

