---
description: 다음은 Android 라이브러리에서 제공하는 Audience Manager 메서드 목록입니다.
keywords: Android; 라이브러리; 모바일; SDK
seo-description: 다음은 Android 라이브러리에서 제공하는 Audience Manager 메서드 목록입니다.
seo-title: Audience Manager 메서드
solution: Marketing Cloud, Analytics
title: Audience Manager 메서드
topic: 개발자 및 구현
uuid: 2 F 6 E 4664-1306-41 D 4-9 FA 7-E 3 A 99 F 1 DF 4 AB
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Audience Manager methods{#audience-manager-methods}

다음은 Android 라이브러리에서 제공하는 Audience Manager 메서드 목록입니다.

현재 SDK는 Analytics, Target, Audience Manager 및 Adobe Experience Platform Identity Service를 비롯한 다양한 Adobe Experience Cloud 솔루션을 지원합니다. Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `audience manager`.

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

   이 메서드에 전달되는 dpuuid 값에 URL-safe가 아닌 문자가 포함되어 있으면 고객은 SDK에 전달하기 전에 매개 변수를 인코딩해야 합니다.

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
