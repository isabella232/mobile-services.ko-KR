---
description: BlackBerry 라이브러리에서 제공하는 클래스 및 메서드입니다.
seo-description: BlackBerry 라이브러리에서 제공하는 클래스 및 메서드입니다.
seo-title: Adobe Mobile class and method reference
title: Adobe Mobile class and method reference
uuid: 1e42d759-be43-4bb3-ac1a-c7d64133d61c
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Adobe Mobile class and method reference {#adobe-mobile-class-and-method-reference}

BlackBerry 라이브러리에서 제공하는 클래스 및 메서드입니다.

현재 SDK는 Adobe Analytics를 지원하고 메서드는 솔루션을 기반으로 별도의 클래스에 있습니다.

## SDK settings {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   현재 사용자에 대한 개인 정보 상태의 열거 표현을 반환합니다.

   * ADBMobilePrivacyStatusOptIn - 히트가 즉시 전송됩니다.
   * ADBMobilePrivacyStatusOptOut - 히트가 삭제됩니다.
   * ADBMobilePrivacyStatusUnknown - 보고서 세트에 타임스탬프가 사용되면 개인정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트가 삭제됨)으로 변경될 때까지 히트가 저장됩니다. 보고서 세트에 타임스탬프가 사용되지 않으면 개인정보 상태가 옵트인으로 변경될 때까지 히트가 삭제됩니다.

      기본값은 `ADBMobileConfig.json` 파일에서 설정되어 있습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```cpp
      static ADBMobilePrivacyStatus getPrivacyStatus();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```cpp
      ADBMobilePrivacyStatus privacyStatus = ADBMobile::getPrivacyStatus();
      ```

* **setPrivacyStatus**

   현재 사용자의 개인정보 상태를 `status`로 설정합니다. 다음 값 중 하나를 설정합니다.

   * `ADBMobilePrivacyStatusOptIn` - hits are sent immediately.
   * `ADBMobilePrivacyStatusOptOut` - hits are discarded.
   * `ADBMobilePrivacyStatusUnknown` - 보고서 세트에 타임스탬프가 사용되면 개인정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트가 삭제됨)으로 변경될 때까지 히트가 저장됩니다. 보고서 세트에 타임스탬프가 사용되지 않으면 개인정보 상태가 옵트인으로 변경될 때까지 히트가 삭제됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```cpp
      static void setPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```cpp
      ADBMobile::setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```

* **getUserIdentifier**

   사용자 지정 식별자가 설정된 경우 사용자 식별자를 반환합니다. Returns `null` if a custom identifier is not set. 기본값은 `null`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```cpp
      static QString getUserIdentifier();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```cpp
      QString userId = ADBMobile::getUserIdentifier(); 
      ```

* **setUserIdentifier**

   사용자 식별자를 `identifier`로 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```cpp
      static void setUserIdentifier(QString identifier);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```cpp
      ADBMobile::setUserIdentifier("billybob");
      ```

* **getDebugLogging**

   현재 디버그 로깅 기본 설정을 반환합니다. 기본값은 `false`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```cpp
      static bool getDebugLogging();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```cpp
       bool debugging = ADBMobile::getDebugLogging(); 
      ```

* **setDebugLogging**

   디버그 로깅 기본 설정을 `debugLogging`으로 설정합니다. 

   * 다음은 이 메서드에 대한 구문입니다.

      ```cpp
      static void setDebugLogging(bool debugLogging);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```cpp
        ADBMobile::setDebugLogging(true); 
      ```

* **collectLifecycleData**

   SDK의 솔루션 전체에서 사용하기 위해 라이프사이클 데이터를 수집해야 함을 SDK에 표시합니다. 자세한 내용은 [라이프사이클 지표](/help/blackberry/metrics.md)를 참조하십시오.

   * 다음은 이 메서드에 대한 구문입니다.

      ```cpp
      static void collectLifecycleData();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```cpp
      ApplicationUI::ApplicationUI(bb::cascades::Application *app):  QObject(app)  { 
      //... 
      ADBMobile::collectLifecycleData(); 
      }
      ```

## Analytics methods {#section_91F4AD0A045D4E4E8F9A93450503E49E}

이러한 각 메서드는 Adobe Analytics 보고서 세트로 데이터를 전송하는 데 사용됩니다.

* **trackState**

   선택적 컨텍스트 데이터로 앱 상태를 추적합니다. 상태는 'home dashboard', 'app settings', 'cart' 등과 같이 앱에서 사용할 수 있는 보기입니다. 이 상태는 웹 사이트의 페이지와 유사하며 `trackState` 호출은 페이지 보기를 증가시킵니다.

   >[!TIP]
   >
   >이것은 페이지 보기를 증가시키는 유일한 추적 호출입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```cpp
      static void trackState(QString state, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```cpp
         ADBMobile::trackState("loginScreen", null);
      ```

* **trackAction**

   앱의 작업을 추적합니다. 작업은 'logons,' 'banner taps,' 'feed subscriptions' 및 기타 지표 등 앱에서 발생하여 측정하려는 작업입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   현재 xy 좌표를 보냅니다. 이벤트를 구독자에서 BPS로 수신되는 이벤트로 바꾸십시오.

   * 다음은 이 메서드에 대한 구문입니다.

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` 구성 파일 참조 {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

The `ADBMobileConfig.json` file must be placed in the *assets* folder.

* **rsids**

   (필수) Analytics 데이터를 수신할 하나 이상의 보고서 세트입니다. 여러 보고서 세트 ID는 공백 없이 쉼표로 구분해야 합니다.

   다음은 이 변수의 코드 샘플입니다.

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (필수 여부). Analytics 서버입니다. This variable should be populated with the server domain, without an `https://` or `https://` protocol prefix. 프로토콜 접두사는 `ssl` 변수를 기반으로 하여 라이브러리에서 자동으로 처리합니다. `ssl`이 `true`이면 이 서버에 보안 연결이 설정됩니다. `ssl`이 `false`이면 이 서버에 비보안 연결이 설정됩니다.

* **charset**

   Analytics로 전송되는 데이터에 사용하는 문자 세트를 정의합니다. charset은 들어오는 데이터를 저장 및 보고용으로 UTF-8로 변환하는 데 사용됩니다.

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (HTTPS). 기본값은 `false`입니다.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. 오프라인 추적을 사용하려면 보고서 세트에 타임스탬프가 설정되어 있어야 합니다.

   >[!TIP]
   >
   >If timestamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. 보고서 세트에서 타임스탬프가 사용되지 않는 경우에는 `offlineEnabled` 구성 속성이 *반드시* false여야 합니다. 이 속성이 제대로 구성되지 않으면 데이터가 손실됩니다. 보고서 세트 타임 스탬프 활성화 여부가 확실치 않으면 엔터프라이즈 [지원에 문의하십시오](https://helpx.adobe.com/contact/enterprise-support.ec.html).

   현재 JavaScript의 데이터도 수집하는 보고서 세트에 AppMeasurement 데이터를 보고하는 경우, 모바일 데이터에 별도의 보고서 세트를 설정하거나 `s.timestamp` 변수를 사용하는 모든 JavaScript 히트에 사용자 지정 타임스탬프를 포함해야 할 수도 있습니다.

   기본값은 `false`입니다.

* **lifecycleTimeout**

   앱 시작이 새 세션으로 간주되기 전에 다음 앱이 시작되기까지 경과되어야 하는 시간(초)을 지정합니다. 이 시간 초과는 응용 프로그램이 백그라운드로 전송되고 다시 활성화될 때도 적용됩니다. 앱이 백그라운드에서 소요하는 시간은 세션 길이에 포함되지 않습니다.

   The default value is 300 seconds.

* **batchLimit**

   큐에 저장되는 최대 오프라인 히트 수입니다. 기본값은 0(제한 없음)입니다.

* **privacyDefault**

   * `optedin` - hits are sent immediately.
   * `optedout` - 히트가 무시됩니다.
   * `optunknown` - 보고서 세트에 타임스탬프가 사용되면 개인정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트가 삭제됨)으로 변경될 때까지 히트가 저장됩니다. 

      보고서 세트에 타임스탬프가 사용되지 않으면 개인정보 상태가 옵트인으로 변경될 때까지 히트가 삭제됩니다.
   이 변수는 초기 값만 설정합니다. 코드에서 이 값을 설정하거나 변경하고 나면 해당 값을 변경하거나 앱을 제거하고 다시 설치할 때까지 새 값이 사용됩니다.

   기본값은 `optedin`입니다.

다음은 `ADBMobileConfig.json` 파일 예제입니다.

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 5, 
        "privacyDefault" : "optedin", 
    } 
}
```
