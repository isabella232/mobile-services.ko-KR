---
description: 비디오를 측정하는 일반 프로세스는 모든 AppMeasurement 플랫폼에서 매우 유사합니다. 이 섹션에서는 코드 샘플과 함께 개발자 작업에 대한 기본 개요를 제공합니다.
seo-description: 비디오를 측정하는 일반 프로세스는 모든 AppMeasurement 플랫폼에서 매우 유사합니다. This section provides a basic overview of the developer tasks along with code samples.
seo-title: Video Analytics
title: Video Analytics
uuid: 0d2731f3-77a9-4db1-9a8c-1e56c212ecb4
translation-type: tm+mt
source-git-commit: 5fbba02eb61679344f638b6465e47b0d9ae5a988

---


# Video Analytics {#video-analytics}

비디오를 측정하는 일반 프로세스는 모든 AppMeasurement 플랫폼에서 매우 유사합니다. 이 섹션에서는 코드 샘플과 함께 개발자 작업에 대한 기본 개요를 제공합니다.

비디오 측정에 대한 자세한 내용은 Adobe Analytics [의 오디오 및 비디오 측정 안내서를 참조하십시오](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html) .  다음 표에는 Analytics에 전송되는 미디어 데이터가 나열되어 있습니다. 처리 규칙을 사용하여 컨텍스트 데이터 변수 열의 컨텍스트 데이터를 [변수 유형] 열에 설명된 Analytics 변수에 매핑하십시오.

## 플레이어 이벤트를 Analytics 변수에 매핑

* **a.media.name**

   (필수 사항) 방문자가 어떤 방식으로든 비디오를 볼 때 구현에 지정된 대로 비디오의 이름을 수집합니다. 이 변수에 분류를 추가할 수 있습니다.

   **(선택 사항)** 사용자 지정 인사이트 변수는 비디오 경로 지정 정보를 제공합니다.

   * 변수 이름:eVar
      * 기본 만료: 방문
      * Custom Insight(s.prop, 비디오 경로 지정에 사용됨)

* **a.media.name**

   (**선택 사항**) 비디오 경로 지정 정보를 제공합니다. ClientCare에서 이 변수에 대해 경로 지정을 활성화해야 합니다.

   * 이벤트 유형: 사용자 지정 통찰력(s.prop)
   * 사용자 지정 통찰력(s.Prop)

* **a.media.segment**

   (**필수**) 세그먼트 이름 및 비디오에서 세그먼트가 발생하는 순서를 포함하여 비디오 세그먼트 데이터를 수집합니다. 이 변수는 플레이어 이벤트를 자동으로 추적할 때 `segmentByMilestones` 변수를 활성화하거나, 플레이어 이벤트를 수동으로 추적할 때 사용자 지정 세그먼트 이름을 설정하여 채워집니다.

   For example, when a visitor views the first segment in a video, SiteCatalyst might collect `1:M:0-25` in the Segments eVar. 기본 비디오 데이터 수집 방법은 비디오 시작(재생), 세그먼트 시작 및 비디오 종료(중지) 지점에서 데이터를 수집합니다.

   Analytics에서는 방문자가 시청을 시작하면 세그먼트 시작 시 첫 번째 세그먼트 보기를 카운트합니다. 이후 세그먼트 보기는 세그먼트가 시작될 때 카운트됩니다.

   * 변수 유형:eVar
   * 기본 만료: 페이지 보기

* **a.contentType**

   방문자가 본 컨텐츠 유형에 대한 데이터를 수집합니다. 비디오 측정에서 전송한 조회수에는 "비디오" 컨텐츠 유형이 할당됩니다. 이 변수는 비디오 추적을 위해 배타적으로 예약하지 않아도 됩니다. 이와 동일한 변수를 사용하는 다른 컨텐츠 보고서 컨텐츠 유형이 있으면 여러 컨텐츠 유형에 대해 방문자 분포를 분석할 수 있습니다. 예를 들어 이 변수를 사용하여 "article" 또는 "product page"와 같은 값을 사용하는 다른 콘텐츠 유형에 태그를 지정할 수 있습니다. 비디오 측정 관점에서 컨텐츠 유형을 사용하면 비디오 방문자를 식별할 수 있고 비디오 전환율을 계산할 수 있습니다.

   * 변수 유형:eVar
   * 기본 만료: 페이지 보기

* **a.media.timePlayed**

   마지막 데이터 컬렉션 처리(이미지 요청) 이후 비디오를 시청하는 데 걸린 시간(초)을 계산합니다.

   * 변수 유형:이벤트
   * 유형:카운터

* **a.media.view**

   방문자가 비디오를 일정 부분 보았음을 나타냅니다. 그러나 방문자가 비디오에서 본 내용이나 분량에 대한 정보는 제공하지 않습니다.

   * 변수 유형:이벤트
   * 유형:카운터

* **a.media.segmentView**

   방문자가 비디오 세그먼트의 일정 부분을 보았음을 나타냅니다. 그러나 방문자가 비디오에서 본 내용이나 분량에 대한 정보는 제공하지 않습니다.

   * 변수 유형:이벤트
   * 유형:카운터

* **a.media.complete**

   사용자가 비디오 전체를 보았음을 의미합니다. 기본적으로 완료 이벤트는 비디오 종료 1초 전에 측정됩니다. 구현 중에 비디오 종료 몇 초 전을 보기 완료로 고려할 것인지 지정할 수 있습니다. 정의된 끝이 없는 라이브 비디오 및 기타 스트림의 경우 완료를 측정할 사용자 지정 지점을 지정할 수 있습니다. 예를 들어 특정 시간을 시청한 후로 지정할 수 있습니다.

   * 변수 유형:이벤트
   * 유형:카운터

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, The `mediaPlay`, `mediaStop`, and `mediaClose` methods need to be called at the appropriate times. 예를 들어 플레이어가 일시 중지된 경우에는 `mediaStop`입니다. 재생이 시작되거나 다시 시작된 경우에는 `mediaPlay`를 호출합니다.

## Media measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

* **open**

   추적을 위해 비디오를 엽니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```cpp
      void open(QString name, double length, QString playerName, QString playerID = QString()); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```cpp
        ADBMediaAnalytics::sharedInstance()->open("name", 10.0, "playerName", "playerID"); 
      ```

* **openAd**

   추적을 위해 `MediaSettings` 개체를 엽니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```cpp
      void openAd(QString name, double length, QString playerName, QString parentName, QString parentPod, double parentPodPosition, QString CPM); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```cpp
      ADBMediaAnalytics::sharedInstance()->openAd("name", 10, "playerName", "parentName", "podName", 0, "CPM"); 
      ```

* **close**

   Closes the media item named *`name`*.

   * 다음은 이 메서드에 대한 구문입니다.

      ```cpp
      void close(QString name);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name");
      ```

* **play**

   Plays the media item named *`name`* at the given *`offset`* (in seconds).

   * 다음은 이 메서드에 대한 구문입니다.

      ```cpp
      void play(QString name, double offset);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```cpp
      ADBMediaAnalytics::sharedInstance()->play("name", 0); 
      ```

* **완료**

   Manually mark the media item as complete at the *`offset`* provided (in seconds).

   * 다음은 이 메서드에 대한 구문입니다.

      ```cpp
      void complete(QString name, double offset);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```cpp
      ADBMediaAnalytics::sharedInstance()->complete("name", 0);
      ```

* **stop**

   *제공된 오프셋에서 비디오가 중지 또는 일시 중지되었음을 미디어 모듈에 알립니다*.

   * 다음은 이 메서드에 대한 구문입니다.

      ```cpp
      stop(QString name, double offset);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```cpp
      ADBMediaAnalytics::sharedInstance()->stop("name", 0);
      ```

* **click**

   미디어 항목이 클릭되었음을 미디어 모듈에 알립니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```cpp
      void click(QString name, double offset);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name", 0);
      ```

* **track**

   현재 미디어 상태에 대한 추적 작업 호출(페이지 보기 없음)을 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```cpp
      track(QString name, QHash<QString, QString> additionalData = QHash<QString, QString>()); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```cpp
      ADBMediaAnalytics::sharedInstance()->track("name", null);
      ```
