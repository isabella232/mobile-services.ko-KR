---
description: 유니버설 Windows 플랫폼 라이브러리에서 제공하는 Audience Manager 메서드 목록입니다.
seo-description: 유니버설 Windows 플랫폼 라이브러리에서 제공하는 Audience Manager 메서드 목록입니다.
seo-title: Audience Manager 메서드
solution: Experience Cloud,Analytics
title: Audience Manager 메서드
topic-fix: Developer and implementation
uuid: efbe8f33-7f53-40a6-b7aa-a36ac718c047
exl-id: a7b4001d-d90f-4a8a-a801-d66e56ea43b5
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 43%

---

# Audience Manager 메서드{#audience-manager-methods}

유니버설 Windows 플랫폼 라이브러리에서 제공하는 Audience Manager 메서드 목록입니다.

SDK는 현재 Analytics, Target 및 Audience Manager을 비롯한 여러 Adobe Experience Cloud 솔루션을 지원합니다. 솔루션은 솔루션에 따라 접두사가 붙습니다.Audience Manager 메서드 앞에 `AudienceManager`이(가) 있습니다.

>[!TIP]
>
>winJS(JavaScript)에서 `winmd` 메서드를 사용하면 모든 메서드에서 첫 번째 문자가 자동으로 소문자로 바뀝니다.

audience manager가 JSON 파일에 구성된 경우 라이프사이클 지표가 포함된 신호가 라이프사이클 히트와 함께 전송됩니다.

* **GetVisitorProfile(winJS:getVisitorProfile)**

   가장 최근 획득한 방문자 프로필을 반환합니다. 아직 제출된 신호가 없는 경우 `null`을 반환합니다. 방문자 프로필은 `SharedPreferences`에 저장되므로 앱을 여러 번 실행할 때 쉽게 액세스할 수 있습니다.

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

   고객 관리에 트레이트와 함께 신호를 보내고 블록 콜백에서 반환된 일치 세그먼트를 받습니다.

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
