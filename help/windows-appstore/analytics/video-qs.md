---
description: 비디오 분석에 도움이 되는 정보입니다.
seo-description: 비디오 분석에 도움이 되는 정보입니다.
seo-title: Video Analytics
solution: Experience Cloud,Analytics
title: Video Analytics
topic: Developer and implementation
uuid: 7d4e6668-a1d9-41da-96c8-8baac860c5b0
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 72%

---


# Video Analytics {#video-analytics}

비디오 분석에 도움이 되는 정보입니다.

비디오 측정은 Adobe Analytics [에서 오디오 및 비디오 측정](https://docs.adobe.com/content/help/ko-KR/media-analytics/using/media-overview.html/) 안내서에 자세히 설명되어 있습니다. 비디오를 측정하는 일반적인 프로세스는 모든 AppMeasurement 플랫폼에서 매우 유사합니다. 이 빠른 시작 섹션은 코드 샘플과 함께 개발자 작업의 기본 개요를 제공합니다.

다음 표에는 Analytics에 전송되는 미디어 데이터가 나열되어 있습니다. 처리 규칙을 사용하여 컨텍스트 데이터를 Analytics 변수에 매핑합니다.

* **a.media.name**

   (필수) 방문자가 비디오를 보는 경우 구현에 지정된 대로 비디오의 이름을 수집합니다.이 변수에 대한 분류를 추가할 수 있습니다.

   **선택 사항** - Custom Insight 변수는 비디오 경로 지정 정보를 제공합니다.

   * 변수 유형: eVar
   * 기본 만료: 방문
   * 사용자 지정 인사이트(s.prop, 비디오 경로 지정에 사용)

* **a.media.name**

   (선택 사항) 비디오 경로 지정 정보를 제공합니다. 이 변수에 대해 ClientCare에서 경로 지정을 활성화해야 합니다.

   이벤트 유형: 사용자 지정 통찰력(s.prop)

   * 변수 유형: 사용자 지정 통찰력(s.prop)

* **a.media.segment**

   (필수) 세그먼트 이름 및 비디오에서 세그먼트가 발생하는 순서를 포함하여 비디오 세그먼트 데이터를 수집합니다. 이 변수는 플레이어 이벤트를 자동으로 추적할 때 `segmentByMilestones` 변수를 활성화하거나, 플레이어 이벤트를 수동으로 추적할 때 사용자 지정 세그먼트 이름을 설정하여 채워집니다. For example, when a visitor views the first segment in a video, SiteCatalyst might collect the following in the `1:M:0-25` segment eVar.

   기본 비디오 데이터 수집 방법의 경우, 다음 시점에서 데이터를 수집합니다.

   * 비디오 시작(재생)
   * 세그먼트 시작
   * 비디오 종료(중지)

   Analytics에서는 방문자가 시청을 시작할 때 세그먼트 시작에서 첫 번째 세그먼트 보기를 계산합니다. 세그먼트가 시작될 때 표시되는 후속 세그먼트 보기.

   * 변수 유형: eVar
   * 기본 만료: 페이지 보기


* **a.contentType**

   방문자가 본 컨텐츠 유형에 대한 데이터를 수집합니다. 비디오 측정에 의해 전송된 히트에 &quot;비디오&quot;의 컨텐츠 유형이 할당됩니다. 이 변수는 비디오 추적에만 예약할 필요가 없습니다. 동일한 변수를 사용하여 다른 컨텐츠 보고서 컨텐츠 유형을 갖는 경우 다양한 유형의 컨텐츠에 대한 방문자 분포를 분석할 수 있습니다. 예를 들어 이 변수를 사용하여 &quot;article&quot; 또는 &quot;product page&quot;와 같은 값을 사용하는 다른 콘텐츠 유형에 태그를 지정할 수 있습니다. 비디오 측정 관점에서 컨텐츠 유형을 사용하면 비디오 방문자를 식별하고 비디오 전환율을 계산할 수 있습니다.

   * 변수 유형: eVar
   * 기본 만료: 페이지 보기

* **a.media.timePlayed**

   마지막 데이터 컬렉션 처리(이미지 요청) 이후 비디오를 시청하는 데 걸린 시간(초)을 계산합니다.

   * 변수 유형: 이벤트
   * 유형:카운터

* **a.media.view**

   방문자가 비디오를 일정 부분 보았음을 나타냅니다. 그러나 방문자가 비디오에서 본 내용이나 분량에 대한 정보는 제공하지 않습니다.

   * 변수:이벤트
   * 유형:카운터

* **a.media.segmentView**

   방문자가 비디오 세그먼트의 일정 부분을 보았음을 나타냅니다. 그러나 방문자가 비디오에서 본 내용이나 분량에 대한 정보는 제공하지 않습니다.

   * 변수 유형: 이벤트
   * 유형:카운터

* **a.media.complete**

   사용자가 비디오 전체를 보았음을 의미합니다. 기본적으로 완료 이벤트는 비디오 종료 1초 전에 측정됩니다. 구현 중에 비디오 종료 몇 초 전을 보기 완료로 고려할 것인지 지정할 수 있습니다. 정의된 끝이 없는 라이브 비디오 및 기타 스트림의 경우 시청한 특정 시간 이후와 같이 사용자 지정 지점을 지정하여 완료를 측정할 수 있습니다.

   * 변수 유형: 이벤트
   * 유형:카운터


## 미디어 설정 구성 {#section_929945D4183C428AAF3B983EFD3E2500}

비디오를 추적하는 데 사용할 설정으로 `MediaSettings` 객체를 구성합니다.

```js
var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId");
```

## 플레이어 이벤트 추적 {#section_C7F43AECBC0D425390F7FCDF3035B65D}

비디오 재생을 측정하려면 적절한 시간에 `Play`, `Stop` 및 `Close` 메서드를 호출해야 합니다. 예를 들어 플레이어가 일시 중지된 경우에는 `Stop`입니다. 재생이 시작되거나 다시 시작된 경우에는 `Play`를 호출합니다.

## 클래스 {#section_16838332727348F990305C0C6B0D795C}

### 클래스: MediaSettings

```
property Platform::String ^name; 
property Platform::String ^playerName; 
property Platform::String ^playerID; 
property double length; 
property Platform::String ^channel; 
property Platform::String ^milestones; 
property Platform::String ^offsetMilestones; 
property bool segmentByMilestones; 
property bool segmentByOffsetMilestones; 
property int trackSeconds; 
property int completeCloseOffsetThreshold; 
 
// MediaAnalytics Ad settings 
property Platform::String ^parentName; 
property Platform::String ^parentPod; 
property Platform::String ^CPM; 
property double parentPodPosition; 
property bool isMediaAd;
```

## 미디어 측정 클래스 및 메서드 참조 {#section_50DF9359A7B14DF092634C8E913C77FE}

* **SettingsWith (winJS:settingsWith)**

   지정된 매개 변수와 함께 `MediaSetting` 개체를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^playerID); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId"); 
      ```

* **AdSettingsWith (winJS:adSettingsWith**

   광고 비디오 추적에 사용할 `MediaSettings` 개체를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^parentName, Platform::String ^parentPod, double parentPosition, Platform::String ^CPM); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var myAdSettings = ADB.Media.adSettingsWith("name", 10, "playerName", "parentName", "parentPod", 5, "myCPM"); 
      ```

* **열기(winJS:open)**

   에 정의된 설정을 사용하여 열린 미디어를 추적합니다 `settings`.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADB.Media.open(mySettings); 
      ```

* **닫기(winJS:닫기)**

   이름이 *명명된 미디어 항목에 대한 미디어 닫기를 추적합니다*.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void Close(Platform::String ^name);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADB.Media.close("mediaName");
      ```

* **재생(winJS:play)**

   지정된 오프셋 *`name`* (초)에서 이름이 지정된 미디어 항목 *의 미디어 재생* 을 추적합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void Play(Platform::String ^name, double offset);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADB.Media.play("mediaName", 0);
      ```

* **완료(winJS:complete)**

   제공된 *오프셋*(초)에서 완료된 미디어 항목을 수동으로 표시합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void Complete(Platform::String ^name, double offset);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADB.Media.complete("mediaName", 8); 
      ```

* **중지(winJS:stop)**

   *제공된 오프셋에서 비디오가 중지 또는 일시 중지되었음을 미디어 모듈에 알립니다*.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void Stop(Platform::String ^name, double offset);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADB.Media.stop("mediaName", 4);
      ```

* **클릭(winJS:클릭)**

   미디어 항목이 클릭되었음을 미디어 모듈에 알립니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void Click(Platform::String ^name, double offset);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADB.Media.click("mediaName", 3);
      ```

* **트랙(winJS:추적)**

   현재 미디어 상태에 대한 추적 작업 호출(페이지 보기 없음)을 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADB.Media.track("mediaName", null);
      ```

