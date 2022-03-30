---
description: 유니버설 Windows 플랫폼 라이브러리에서 제공하는 클래스 및 메서드입니다.
solution: Experience Cloud Services,Analytics
title: SDK 메서드
topic-fix: Developer and implementation
uuid: e3aa41d6-7bc0-4208-a662-12907c209a77
exl-id: 0aac477c-074d-457c-b117-bb205119c475
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 64%

---

# SDK 메서드 {#sdk-methods}

유니버설 Windows 플랫폼 라이브러리에서 제공하는 클래스 및 메서드입니다.

>[!TIP]
>
>소비할 때 `winmd` winJS(JavaScript)의 메서드를 사용하면 모든 메서드가 자동으로 첫 번째 문자를 소문자로 바꿉니다.

* **GetVersion (winJS: getVersion)**

   Adobe Mobile 라이브러리의 현재 버전을 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile;var libVersion = ADB.Config.getVersion();
      ```

* **GetPrivacyStatusAsync(winJS: getPrivacyStatusAsync)**

   현재 사용자에 대한 개인 정보 상태의 열거 표현을 반환합니다.

   * `ADBMobilePrivacyStatusOptIn` - 히트가 즉시 전송됩니다.
   * `ADBMobilePrivacyStatusOptOut` - 히트가 삭제됩니다.
   * `ADBMobilePrivacyStatusUnknown`: 보고서 세트에 타임스탬프가 활성화되어 있을 경우 개인정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트가 삭제됨)으로 변경될 때까지 히트가 저장됩니다. 보고서 세트에 타임스탬프가 활성화되어 있지 않을 경우 개인정보 상태가 옵트인으로 변경될 때까지 히트가 삭제됩니다.

      기본값은 `ADBMobileConfig.json` 구성 파일. 자세한 내용은 [ADBMobileConfig.json 구성 파일](/help/universal-windows/c-configuration/c.json.md).

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus>
      ^getPrivacyStatusAsync();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      **C 샤프**

      ```csharp
      public enum class ADBMobilePrivacyStatus : int { ADBMobilePrivacyStatusOptIn = 1, 
      ADBMobilePrivacyStatusOptOut = 2, 
      ADBMobilePrivacyStatusUnknown = 3};
      ```

      **JavaScript**

      ```javascript
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
        status = privacyStatus;}
      );
      ```

* **SetPrivacyStatus(winJS: setPrivacyStatus)**

   현재 사용자의 개인정보 상태를 `status`로 설정합니다. 다음 값 중 하나를 설정합니다.
   * `ADBMobilePrivacyStatusOptIn` - 히트가 즉시 전송됩니다.
   * `ADBMobilePrivacyStatusOptOut` - 히트가 삭제됩니다.
   * `DBMobilePrivacyStatusUnknown` - 보고서 세트에 타임스탬프가 활성화되어 있을 경우 개인정보 상태가 옵트인(히트가 전송됨) 또는 옵트아웃(히트가 삭제됨)으로 변경될 때까지 히트가 저장됩니다. 보고서 세트에 타임스탬프가 활성화되어 있지 않을 경우 개인정보 상태가 옵트인으로 변경될 때까지 히트가 삭제됩니다.

      * 다음은 이 메서드에 대한 구문입니다.

         ```csharp
         static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
         ```

      * 다음은 이 메서드의 코드 샘플입니다.

         **C-sharp**

         ```csharp
         public enum class ADBMobilePrivacyStatus : int { 
           ADBMobilePrivacyStatusOptIn = 1, 
           ADBMobilePrivacyStatusOptOut = 2
           ADBMobilePrivacyStatusUnknown = 3
         };
         ```

         **JavaScript**

         ```js
         var ADB = ADBMobile;
         ADB.Config.setPrivacyStatus (ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn
         );
         ```

* **GetLifetimeValue(winJS: getLifetimeValue)**

   현재 사용자의 수명 값을 반환합니다. 기본값은 `0`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static float GetLifetimeValue(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile;
      var ltv = ADB.Config.getLifetimeValue();
      ```

* **GetUserIdentifier (winJS: getUserIdentifier)**

   사용자 지정 식별자가 설정된 경우 사용자 지정 사용자 식별자를 반환합니다. 반환 `null` 사용자 지정 ID가 설정되지 않은 경우.
기본값은 `null`입니다.

   >[!IMPORTANT]
   >
   >앱을 Experience Cloud 3.x에서 4.x SDK로 업그레이드할 경우 이전 ID 서비스(사용자 지정 또는 자동 생성)가 검색되어 사용자 지정 사용자 식별자로 저장됩니다. 이렇게 하면 SDK 업그레이드 시에도 방문자 데이터가 보존됩니다. 4.x SDK에 새로 설치하는 경우 사용자 식별자는 설정될 때까지 `null`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static Platform::String ^GetUserIdentifier(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```csharp
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **SetUserIdentifier (winJS: setUserIdentifier)**

   사용자 식별자를 `identifier`로 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      var ADB = ADBMobile;
      ADB.Config.setUserIdentifier("someUserId");
      ```

* **GetDebugLogging(winJS: getDebugLogging)**

   현재 디버그 로깅 기본 설정을 반환합니다. 기본값은 `false`입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static bool GetDebugLogging();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```javascript
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging();
      ```

* **SetDebugLogging(winJS: setDebugLogging)**

   디버그 로깅 기본 설정을 `debugLogging`으로 설정합니다. 디버그 로깅은 라이브러리의 디버그 버전을 사용할 때만 작동하며 릴리스 버전에서는 이 설정을 무시합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void SetDebugLogging(bool debugLogging);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile;
      ADB.Config.setDebugLogging(true);
      ```

* **CollectLifecycleData (winJS: collectLifecycleData)**

   SDK의 솔루션 전체에서 사용하기 위해 라이프사이클 데이터를 수집해야 함을 SDK에 표시합니다. 자세한 내용은 [라이프사이클 지표](/help/universal-windows/metrics.md)를 참조하십시오.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void CollectLifecycleData();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData();
      ```

* **일시 중지라이프사이클 &#x200B; 데이터 수집(winJS: pauseLifecycleData &#x200B; 수집)**

   라이프사이클 지표를 정확히 계산하기 위해 앱이 일시 중지되었음을 SDK에 표시합니다. 예를 들어 일시 중지 시 타임스탬프를 수집하여 이전 세션 길이를 파악합니다. 플래그를 설정하여 앱이 충돌하지 않았음을 라이프사이클에서 올바르게 알도록 할 수도 있습니다. 자세한 내용은 [라이프사이클 지표](/help/universal-windows/metrics.md)를 참조하십시오.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData(); 
      ```
