---
description: Universal Windows Platform 라이브러리에서 제공하는 Audience Manager 목록 메서드입니다.
seo-description: Universal Windows Platform 라이브러리에서 제공하는 Audience Manager 목록 메서드입니다.
seo-title: Audience Manager methods
solution: Marketing Cloud,Analytics
title: Audience Manager 메서드
topic: 개발자 및 구현
uuid: efbe8f33-7f53-40a6-b7aa-a36ac718c047
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Audience Manager methods{#audience-manager-methods}

Universal Windows Platform 라이브러리에서 제공하는 Audience Manager 목록 메서드입니다.

현재 SDK는 Analytics, Target 및 Audience Manager을 포함하여 여러 Adobe Experience Cloud 솔루션을 지원합니다. 메서드에는 솔루션에 따라 접두사가 붙습니다. Audience Manager methods are prefixed with `AudienceManager`.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

Audience Manager가 JSON 파일에 구성된 경우 라이프사이클 지표가 포함된 신호가 라이프사이클 히트와 함께 전송됩니다.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   가장 최근 획득한 방문자 프로필을 반환합니다. Returns `null` if no signal has been submitted yet. 방문자 프로필은 앱이 여러 번 시작되는 경우에도 쉽게 액세스할 수 있도록 `SharedPreferences`에 저장됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^GetVisitorProfile();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile; 
      var profile = ADB.AudienceManager.getVisitorProfile();
      ```

* **GetDpid(winJS:getDpid)**

   현재 DPID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static Platform::String ^GetDpid();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile;
      var dpid = ADB.AudienceManager.getDpid(); 
      ```

* **GetDpuuid(winJS:getDpuuid)**

   현재 DPUUID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static Platform::String ^GetDpuuid();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile; 
      var dpuuid = ADB.AudienceManager.getDpuuid();
      ```

* **SetDpidAndDpuuid(winJS:setDpidAndDpuuid)**

   DPID 및 DPUUID를 설정합니다. DPID 및 DPUUID가 설정되면 각 신호와 함께 전송됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void SetDpidAndDpuuid(Platform::String ^dpid, Platform::String ^dpuuid);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile; 
      ADB.AudienceManager.setDpidAndDpuuid("newDpid", "newDpuuid");
      ```

* **SignalWithData(winJS:signalWithData)**

   트레이트를 포함한 신호를 고객 관리에 보내고 차단 콜백에서 반환된 일치 세그먼트를 받습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static 
      Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^> ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object> ^data);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile;
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b";
      ADB.AudienceManager.signalWithData(traits).then(function (visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      }); 
      
