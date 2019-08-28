---
description: 분석 데이터 또는 이벤트에서 트리거되는 인앱 메시지를 제공할 수 있습니다. 구현하고 나면 메시지가 앱에 동적으로 전달되므로 코드를 업데이트할 필요가 없습니다.
seo-description: 분석 데이터 또는 이벤트에서 트리거되는 인앱 메시지를 제공할 수 있습니다. 구현하고 나면 메시지가 앱에 동적으로 전달되므로 코드를 업데이트할 필요가 없습니다.
seo-title: 인앱 메시징
solution: Marketing Cloud, Analytics
title: 인앱 메시징
topic: 개발자 및 구현
uuid: 351 EE 3 D 2-80 B 9-4 F 2 D -9696-21 F 274 D 89 F 5 A
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# 인앱 메시징 {#in-app-messaging}

분석 데이터 또는 이벤트에서 트리거되는 인앱 메시지를 제공할 수 있습니다. 구현하고 나면 메시지가 앱에 동적으로 전달되므로 코드를 업데이트할 필요가 없습니다.

## 새 Adobe Experience Cloud SDK 릴리스

Adobe Experience Platform Mobile SDK와 관련된 정보 및 문서 찾기 최신 문서를 보려면 [여기](https://aep-sdks.gitbook.io/docs/)를 클릭하십시오.

>[!IMPORTANT]
>
>2018년 9월 일자로 SDK의 새로운 주요 버전을 릴리스하였습니다. 이러한 새로운 Adobe Experience Platform Mobile SDK는 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html)를 통해 구성할 수 있습니다.

* 시작하려면 [Launch](https://launch.adobe.com/)로 이동합니다.
* Experience Platform SDK 리포지토리의 항목을 보려면 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)로 이동하십시오.

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-app messaging and push notifications. 자세한 내용은 [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)를 참조하십시오. For more information about using push messaging and in-app messaging with the Experience Cloud SDKs, see [Set up push messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) and [Set up in-app messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

>[!IMPORTANT]
>
>인앱 메시지를 사용하려면 SDK 버전 4.2 이상이 **필요**&#x200B;합니다.

Adobe Mobile Services에서 메시지가 표시되는 시기를 정의하는 메시지와 규칙을 만들 수 있습니다. 자세한 내용은 [인앱 메시지 만들기](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md)를 참조하십시오. 인앱 메시지를 표시하려면 SDK를 업데이트해야 합니다. 메시지를 아직 정의하지 않은 경우에도 이 단계를 완료할 수 있습니다. 메시지를 정의하고 나면 앱 스토어 업데이트 없이 앱에 동적으로 전달되어 표시됩니다.

## Enabling in-app messaging {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 핵심 구현 *및* 라이프사이클에서 [Intellij 아이디어 또는 Eclipse 프로젝트에 SDK 및 구성 파일 추가를](/help/android/getting-started/dev-qs.md)참조하십시오.

1. `AndroidManifest.xml` 파일을 업데이트하여 전체 화면 활동을 선언하고 메시지 알림 핸들러를 활성화합니다.

   ```java
   <activity  
   android:name="com.adobe.mobile.MessageFullScreenActivity"  
   android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

   양식 레이아웃을 선택한 경우 메시지에 대해 다음 테마 중 하나를 선택하십시오.

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

1. 라이브러리를 가져옵니다:

   ```java
   import com.adobe.mobile.*;
   ```

1. 각 `collectLifecycleData` 호출에서 `this`를 전달하여 현재 활동에 대한 참조를 제공합니다.

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
   }
   ```

1. `ADBMobileConfig.json` 파일에 인앱 메시지에 대한 필수 설정이 포함되어 있는지 확인합니다.

   >[!IMPORTANT]
   >
   >`messages``remotes` 또는 필수입니다.

   시작 시 인앱 메시지를 동적으로 업데이트하려면 `remotes` 개체가 존재하고 올바르게 구성되어 있어야 합니다.

   ```js
   “messages”: [ 
       { 
           “messageId”: “de45c43c-37bf-441f-8cbd-cc3ba3469ebe”, 
           “template”: “fullscreen”, 
           “showOffline”: false, 
           “showRule”: “always”, 
           “endDate”: 2524730400, 
           “startDate”: 0, 
           “audiences”: [], 
           “triggers”: [], 
           “payload”: { // contents change depending on template 
               “html”: “<html>html code goes here</html>” 
           }, 
       }, 
       … 
   ] 
   “remotes” : { 
       “analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”, 
       “messages”: “https://assets.adobedtm.com/…/yourfile.json” 
   }
   ```

   If this object is not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. 자세한 내용은 [시작하기 전에](/help/android/getting-started/requirements.md)를 참조하십시오.

## Tracking in-app messages {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Android Mobile SDK는 in-app 메시지에 대한 다음 지표를 추적합니다.

* 전체 화면 및 경고 스타일 in-app 메시지에 대한 지표:

   * **노출 횟수**: 사용자가 in-app 메시지를 트리거할 때입니다.
   * **클릭스루**: 사용자가 클릭스루를 누를 **[!UICONTROL 때.]**
   * **취소**: 사용자가 취소를 누를 ****&#x200B;때.

* 사용자 지정 전체 화면 in-app 메시지의 경우 메시지에서 HTML 컨텐츠에 다음 단추에 대한 SDK 추적을 알리는 올바른 코드를 포함해야 합니다.

   * **클릭스루** (리디렉션) 예제 추적:

      `adbinapp://confirm/?url=https://www.yoursite.com`
   * **취소** (닫기) 예제 추적:

      `adbinapp://cancel`

## Local fallback image {#section_DEACC1CE549B4573B556A44A52409941}

전체 화면 메시지를 작성할 때 선택적으로 대체 이미지를 지정할 수 있습니다. 메시지가 웹에서 원하는 이미지를 검색할 수 없는 경우 SDK는 애플리케이션의 자산 폴더에서 이름이 같은 이미지를 로드합니다. 이렇게 하면 사용자가 오프라인 상태이거나 미리 설정된 이미지에 연결할 수 없는 경우에도 메시지를 원래 형식으로 표시할 수 있습니다.

>[!IMPORTANT]
>
>폴백 이미지 자산 이름은 Adobe Mobile Services에서 메시지를 구성할 때 지정되며, 지정된 리소스를 사용할 수 있도록 해야 합니다.

## Configuring notification icons {#section_DDA28BDBCBB748BCBECF3AB50A177D48}

다음 방법을 사용하면 알림 영역에 나타나는 크고 작은 아이콘과 알림 창에 알림이 표시될 때 나타나는 큰 아이콘을 구성할 수 있습니다.

* **Config.setSmallIconResourceId(int resourceId)**

   SDK로 만든 알림에 사용할 작은 아이콘을 설정합니다. 이 아이콘은 상태 표시줄에 나타나며 사용자가 알림 센터에서 전체 알림을 볼 때 표시되는 보조 이미지입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * 다음은 이 메서드의 코드 예제입니다.

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **Config.setLargeIconResourceId(int resourceId)**

   SDK로 만든 알림에 사용할 큰 아이콘을 설정합니다. 이 아이콘은 사용자가 알림 센터에서 전체 알림을 볼 때 표시되는 기본 이미지입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void setLargeIconResourceId(final int resourceId); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Config.setLargeIconResourceId(R.drawable.appIcon); 
      ```
