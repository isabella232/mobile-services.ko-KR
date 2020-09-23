---
description: 유니버설 Windows 플랫폼 라이브러리에서 제공하는 Audience Manager 메서드 목록입니다.
seo-description: 유니버설 Windows 플랫폼 라이브러리에서 제공하는 Audience Manager 메서드 목록입니다.
seo-title: Audience Manager 메서드
solution: Experience Cloud,Analytics
title: Audience Manager 메서드
topic: Developer and implementation
uuid: efbe8f33-7f53-40a6-b7aa-a36ac718c047
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 43%

---


# Audience Manager 메서드{#audience-manager-methods}

유니버설 Windows 플랫폼 라이브러리에서 제공하는 Audience Manager 메서드 목록입니다.

SDK는 현재 분석, Target 및 Audience Manager을 비롯한 여러 Adobe Experience Cloud 솔루션을 지원합니다. Methods are prefixed according to the solution. Audience Manager methods are prefixed with `AudienceManager`.

>[!TIP]
>
>winJS(JavaScript)의 `winmd` 메서드를 사용하면 모든 메서드에서 첫 번째 문자가 자동으로 소문자로 바뀝니다.

JSON 파일에 audience manager가 구성된 경우 라이프사이클 지표가 포함된 신호가 라이프사이클 히트와 함께 전송됩니다.

* **GetVisitorProfile(winJS:getVisitorProfile)**

   가장 최근 획득한 방문자 프로필을 반환합니다. Returns `null` if no signal has been submitted yet. Visitor profile is saved in `SharedPreferences` for easy access across multiple launches of your app.

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

   DPID 및 DPUUID를 설정합니다. DPID 및 DPUUID가 설정되면 이 값들이 각 신호와 함께 전송됩니다.

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

   고객 관리에서 트레이트와 함께 신호를 보내고 블록 콜백에서 반환된 일치 세그먼트를 받습니다.

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
      ```
