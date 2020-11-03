---
description: 다음은 Android 라이브러리에서 제공하는 Audience Manager 메서드 목록입니다.
keywords: android;library;mobile;sdk
seo-description: 다음은 Android 라이브러리에서 제공하는 Audience Manager 메서드 목록입니다.
seo-title: Audience Manager 메서드
solution: Experience Cloud,Analytics
title: Audience Manager 메서드
topic: Developer and implementation
uuid: 2f6e4664-1306-41d4-9fa7-e3a99f1df4ab
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '292'
ht-degree: 100%

---


# Audience Manager 메서드{#audience-manager-methods}

다음은 Android 라이브러리에서 제공하는 Audience Manager 메서드 목록입니다.

현재 SDK는 Analytics, Target, Audience Manager 및 Adobe Experience Platform ID 서비스 등 여러 Adobe Experience Cloud 솔루션을 지원합니다. 메서드에는 솔루션에 따라 접두사가 추가됩니다. 예를 들면 Experience Cloud ID 메서드에는 `audience manager` 접두사가 추가됩니다.

Audience Manager가 JSON 파일에 구성되어 있으면 라이프사이클 지표가 포함된 신호가 라이프사이클 히트와 함께 전송됩니다.

* **getVisitorProfile**

   가장 최근에 얻은 방문자 프로필을 반환하고, 전송된 신호가 없는 경우에는 `null`을 반환합니다. 방문자 프로필은 앱이 여러 번 시작되는 경우에도 쉽게 액세스할 수 있도록 `SharedPreferences`에 저장됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static HashMap<String, Object> getVisitorProfile(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      HashMap<String, Object> visitorProfile = AudienceManager.getVisitorProfile(); 
      ```

* **getDpid**

   현재 DPID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void getDpid(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      String dpid = AudienceManager.getDpid(); 
      ```

* **getDpuuid**

   현재 DPUUID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void getDpuuid(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      String dpuuid = AudienceManager.getDpuuid(); 
      ```

* **setDpidAndDpuuid**

   DPID 및 DPUUID를 설정하며 이 값들은 각 신호와 함께 전송됩니다.

   이 메서드에 전달된 DPUUID 값에 URL에 안전하지 않은 문자가 포함된 경우 고객이 매개 변수를 인코딩한 후에 SDK에 전달해야 합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void setDpidAndDpuuid(String dpid, String dpuuid); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      AudienceManager.setDpidAndDpuuid("myDpid", "myDpuuid"); 
      ```

* **signalWithData**

   트레이트를 포함한 신호를 고객 관리에 보내고 차단 콜백에서 반환된 일치 세그먼트를 받습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void signalWithData(Map<String, Object> data, AudienceManagerCallback<Map<String, Object>> callback);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      HashMap Traits = new HashMap<String, Object>();
      aamTraits.put("trait", "b");
      AudienceManager.signalWithData(aamTraits, new AudienceManager.AudienceManagerCallback<Map<String, Object>> () {
        @Override
         public void call(Map<String, Object> item) { 
              // segments come back here normally found in the segs object of your json 
         }
      });
      ```
