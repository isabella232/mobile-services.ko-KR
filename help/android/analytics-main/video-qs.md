---
description: 다음은 비디오 측정 솔루션으로 Android에서 비디오를 측정하는 방법에 대한 정보입니다.
keywords: android;라이브러리;모바일;sdk
solution: Experience Cloud,Analytics
title: Video Analytics
topic-fix: Developer and implementation
uuid: a137cc27-dc28-48c0-b08e-2ca17d2c7e1d
exl-id: 1b7f5523-767a-45e8-b2e7-ecf9984849e4
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 98%

---

# Video Analytics {#video-analytics}

다음은 비디오 측정 솔루션으로 Android에서 비디오를 측정하는 방법에 대한 정보입니다.

>[!TIP]
>
>비디오 재생 중 빈번한 &quot;하트비트&quot; 호출이 이 서비스로 전송되어 재생 시간이 측정됩니다. 이러한 하트비트 호출은 10초 간격으로 전송되므로 더 세부적인 비디오 참여 지표와 더 정확한 비디오 폴아웃 보고서를 얻을 수 있습니다. Adobe의 비디오 측정 솔루션에 대한 자세한 내용은 [Adobe Analytics에서 스트리밍 미디어 측정](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=ko-KR)을 참조하십시오.

비디오를 측정하는 일반적인 프로세스는 모든 플랫폼에서 유사합니다. 이 콘텐츠는 코드 샘플을 사용하는 개발자 작업에 대한 개요를 제공합니다. 다음 표에는 Analytics에 전송되는 미디어 데이터가 나열되어 있습니다. 처리 규칙은 컨텍스트 데이터를 Analytics 변수에 매핑하는 데 사용됩니다.

## 플레이어 이벤트를 Analytics 변수에 매핑 {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

* **a.media.name**
   * 변수 유형: eVar
      * 기본 만료: 방문
      * 사용자 지정 인사이트(s.prop, 비디오 경로 지정에 사용)
   * **필수** - 방문자가 특정 방식으로 비디오를 보는 경우, 이 컨텍스트 데이터 변수는 구현에 지정된 비디오 이름을 수집합니다. 이 변수에 대한 분류를 추가할 수 있습니다.
   * **선택 사항** - Custom Insight 변수는 비디오 경로 지정 정보를 제공합니다.

* **a.media.name**
   * 변수 유형: 사용자 지정 통찰력(s.prop)
   * (**선택 사항**) 비디오 경로 지정 정보를 제공합니다.

      >[!IMPORTANT]
      >
      >ExpCare에서 이 변수에 대해 경로 지정을 활성화해야 합니다.
   * 이벤트 유형: 사용자 지정 통찰력(s.prop)

* **a.media.segment**
   * 변수 유형: eVar
   * 기본 만료: 페이지 보기
   * **필수** - 세그먼트 이름 및 비디오에서 세그먼트가 발생하는 순서를 포함하여 비디오 세그먼트 데이터를 수집합니다.

      이 변수는 플레이어 이벤트를 자동으로 추적할 때 `segmentByMilestones` 변수를 활성화하거나, 플레이어 이벤트를 수동으로 추적할 때 사용자 지정 세그먼트 이름을 설정하여 채워집니다. 예를 들어 방문자가 비디오에서 첫 번째 세그먼트를 볼 경우 SiteCatalyst가 세그먼트 eVar에서 다음을 수집할 수 있습니다. `1:M:0-25`

      기본 비디오 데이터 수집 방법의 경우, 다음 시점에서 데이터를 수집합니다.

      * 비디오 시작(재생)
      * 세그먼트 시작
      * 비디오 종료(중지)

      Analytics에서는 방문자가 시청을 시작할 때 세그먼트 시작에서 첫 번째 세그먼트 보기를 계산합니다. 세그먼트가 시작될 때 표시되는 후속 세그먼트 보기.


* **a.contentType**
   * 변수 유형: eVar
   * 기본 만료: 페이지 보기
   * 방문자가 본 콘텐츠 유형에 대한 데이터를 수집합니다.

      비디오 측정에서 전송한 히트에는 `video` 콘텐츠 유형이 할당됩니다. 비디오 측정 관점에서 **콘텐츠 유형**&#x200B;을 사용하면 비디오 방문자를 식별할 수 있고 비디오 전환율을 계산할 수 있습니다.

* **a.media.timePlayed**
   * 변수 유형: 이벤트
   * 유형:카운터
   * 마지막 데이터 수집 처리(이미지 요청) 이후 비디오를 시청하는 데 걸린 시간(초)을 계산합니다.

* **a.media.view**
   * 변수 유형: 이벤트
   * 유형:카운터
   * 방문자가 비디오를 일정 부분 보았음을 나타냅니다.

      그러나 방문자가 비디오에서 본 내용이나 분량에 대한 정보는 제공하지 않습니다.

* **a.media.segmentView**
   * 변수 유형: 이벤트
   * 유형:카운터
   * 방문자가 비디오 세그먼트의 일정 부분을 보았음을 나타냅니다.

      그러나 방문자가 비디오에서 본 내용이나 분량에 대한 정보는 제공하지 않습니다.

* **a.media.complete**
   * 변수 유형: 이벤트
   * 유형:카운터
   * 사용자가 비디오 전체를 보았음을 의미합니다.

      기본적으로 완료 이벤트는 비디오 종료 1초 전에 측정됩니다. 구현 중에 비디오 종료 몇 초 전을 보기 완료로 고려할 것인지 지정할 수 있습니다. 정의된 종료가 없는 라이브 비디오 및 기타 스트림의 경우, 예를 들어 특정 시간을 본 후 완료를 측정할 사용자 지정 지점을 지정할 수 있습니다.


## 미디어 설정 구성 {#section_929945D4183C428AAF3B983EFD3E2500}

비디오를 추적하는 데 사용할 설정으로 `MediaSettings` 객체를 구성합니다.

```java
MediaSettings mySettings = Media.settingsWith("name", 10, "playerName", "playerId");
```

## 플레이어 이벤트 추적 {#section_C7F43AECBC0D425390F7FCDF3035B65D}

비디오 재생을 측정하려면 적절한 시간에 `mediaPlay`, `mediaStop` 및 `mediaClose` 메서드를 호출해야 합니다. 예를 들어 플레이어가 일시 중지되면 `mediaStop`을 호출합니다. 재생이 시작되거나 다시 시작된 경우에는 `mediaPlay`를 호출합니다.

## 클래스 {#section_16838332727348F990305C0C6B0D795C}

**클래스: MediaSettings**

```java
public String name; 
public String playerName; 
public String playerID; 
public double length; 
public String channel; 
public String milestones; 
public String offsetMilestones; 
public boolean segmentByMilestones; 
public boolean segmentByOffsetMilestones; 
public int trackSeconds = 0; 
public int completeCloseOffsetThreshold = 1; 
 
// MediaAnalytics Ad settings 
public String parentName; 
public String parentPod; 
public String CPM; 
public double parentPodPosition; 
public boolean isMediaAd;
```

**클래스: MediaState**

```java
public Date openTime = new Date(); 
public String name; 
public String segment; 
public String playerName; 
public String mediaEvent; 
public int offsetMilestone; 
public int segmentNum; 
public int milestone; 
public double length; 
public double offset; 
public double percent; 
public double timePlayed; 
public double segmentLength; 
public boolean complete = false; 
public boolean clicked = false; 
public boolean ad; 
public boolean eventFirstTime;
```

## 미디어 측정 클래스 및 메서드 참조 {#section_50DF9359A7B14DF092634C8E913C77FE}

다음은 측정 클래스 클래스의 메서드입니다.

* **settingsWith**

   지정된 매개 변수와 함께 `MediaSettings` 개체를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      MediaSettingsmySettings = Media.settingsWith("name", 10, "playerName", "playerId");
      ```

* **adSettingsWith**

   광고 비디오 추적에 사용할 `MediaSettings` 개체를 반환합니다.
   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

* **open**

   추적을 위해 `MediaSettings` 개체를 엽니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void open(MediaSettings settings, MediaCallback callback); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Media.open(mySettings, new Media.MediaCallback() { 
        @Override 
        public void call(Object item)
        {//  monitor  callback  if  you  want  to  be  notified  every  second  the  media  is  playing  }
        }); 
      ```

   * **close**

      이름이 *name*&#x200B;인 미디어 항목을 닫습니다.

      * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void close(String name);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Media.close("name"); 
      ```


* **play**
   * 제공된 *offset*(초)에서 이름이 *name*&#x200B;인 미디어 항목을 재생합니다.
   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      publicstatic void play(String name, double offset); 
      ```

* **완료**

   제공된 *오프셋*(초)에서 완료된 미디어 항목을 수동으로 표시합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void complete(String name, double offset); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Media.complete("name", 0); 
      ```

* **stop**

   *제공된 오프셋에서 비디오가 중지 또는 일시 중지되었음을 미디어 모듈에 알립니다*.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void stop(String name, double offset); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Media.stop("name", 0);
      ```

* **click**

   미디어 항목이 클릭되었음을 미디어 모듈에 알립니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void click(String name double offset); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Media.click("name", 0);
      ```

* **track**

   현재 미디어 상태에 대한 추적 작업 호출(페이지 보기 없음)을 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      publicstatic void track(String name, Map<String, Object> data); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Media.track("name", null); 
      ```
