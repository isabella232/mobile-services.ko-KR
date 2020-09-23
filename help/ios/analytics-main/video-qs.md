---
description: 다음은 마일스톤 비디오 측정을 사용하여 iOS에서 비디오를 측정하는 방법에 대한 정보입니다.
seo-description: 다음은 마일스톤 비디오 측정을 사용하여 iOS에서 비디오를 측정하는 방법에 대한 정보입니다.
seo-title: Video Analytics
solution: Experience Cloud,Analytics
title: Video Analytics
topic: Developer and implementation
uuid: d75fa415-78f6-4f50-a563-76949f040138
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 100%

---


# Video Analytics {#video-analytics}

다음은 마일스톤 비디오 측정을 사용하여 iOS에서 비디오를 측정하는 방법에 대한 정보입니다.

>[!TIP]
>
>비디오 재생 중 빈번한 &quot;하트비트&quot; 호출이 이 서비스로 전송되어 재생 시간이 측정됩니다. 이러한 하트비트 호출은 10초 간격으로 전송되므로 더 세부적인 비디오 참여 지표와 더 정확한 비디오 폴아웃 보고서를 얻을 수 있습니다. 자세한 내용은 [Adobe Analytics에서 오디오 및 비디오 측정](https://docs.adobe.com/content/help/ko-KR/media-analytics/using/media-overview.html)을 참조하십시오.

비디오를 측정하는 일반 프로세스는 모든 플랫폼에서 유사합니다. 이 컨텐츠는 코드 샘플을 사용하는 개발자 작업에 대한 기본적인 개요를 제공합니다.

## 플레이어 이벤트를 Analytics 변수에 매핑 {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

다음 표에는 Analytics에 전송되는 미디어 데이터가 나열되어 있습니다. 처리 규칙을 사용하여 컨텍스트 데이터를 Analytics 변수에 매핑합니다.

* **a.media.name**

   (필수) 구현에 지정된 대로 방문자가 특정 방식으로 비디오를 볼 때 비디오의 이름을 수집합니다. 이 변수에 대한 분류를 추가할 수 있습니다.

   (선택 사항) Custom Insight 변수는 비디오 경로 지정 정보를 제공합니다.

   * 변수 유형: eVar
   * 기본 만료: 방문
   * 사용자 지정 인사이트(s.prop, 비디오 경로 지정에 사용)

* **a.media.name**

   (선택 사항) 비디오 경로 지정 정보를 제공합니다. 고객 지원에 따라 이 변수에 경로 지정을 사용해야 합니다.

   * 변수 유형: 사용자 지정 통찰력(s.prop)
   * 이벤트 유형: 사용자 지정 통찰력(s.prop)

* **a.media.segment**

   (필수) 세그먼트 이름 및 비디오에서 세그먼트가 발생하는 순서를 포함하여 비디오 세그먼트 데이터를 수집합니다. 이 변수는 플레이어 이벤트를 자동으로 추적할 때 `segmentByMilestones` 변수를 활성화하거나, 플레이어 이벤트를 수동으로 추적할 때 사용자 지정 세그먼트 이름을 설정하여 채워집니다. 예를 들어 방문자가 비디오에서 첫 번째 세그먼트를 볼 경우 SiteCatalyst가 `1:M:0-25` 세그먼트 eVar에서 다음을 수집할 수 있습니다. 

   기본 비디오 데이터 수집 방법의 경우, 다음 시점에서 데이터를 수집합니다.

   * 비디오 시작(재생)
   * 세그먼트 시작
   * 비디오 종료(중지)

   Analytics에서는 방문자가 시청을 시작할 때 세그먼트 시작에서 첫 번째 세그먼트 보기를 계산합니다. 세그먼트가 시작될 때 표시되는 후속 세그먼트 보기.

   * 변수 유형: eVar
   * 기본 만료: 페이지 보기


* **a.contentType**

   방문자가 본 콘텐츠 유형에 대한 데이터를 수집합니다. 비디오 측정에 의해 전송된 히트에 `video` 컨텐츠 유형이 할당됩니다. 이 변수는 비디오 추적에 대해서만 예약할 필요가 없습니다. 이와 동일한 변수를 사용하는 다른 컨텐츠 보고서 컨텐츠 유형이 있으면 다른 컨텐츠 유형에 대해 방문자 분포를 분석할 수 있습니다. 예를 들어 이 변수를 사용하여 &quot;article&quot; 또는 &quot;product page&quot;와 같은 값을 사용하는 다른 콘텐츠 유형에 태그를 지정할 수 있습니다. 비디오 측정 관점에서 콘텐츠 유형을 사용하면 비디오 방문자를 식별할 수 있고 비디오 전환율을 계산할 수 있습니다.

   * 변수 유형: eVar
   * 기본 만료: 페이지 보기

* **a.media.timePlayed**

   마지막 데이터 컬렉션 처리(이미지 요청) 이후 비디오를 시청하는 데 걸린 시간(초)을 계산합니다.

   * 변수 유형: 이벤트
   * 유형:카운터

* **a.media.view**

   방문자가 비디오를 일정 부분 보았음을 나타냅니다. 그러나 방문자가 비디오에서 본 내용이나 분량에 대한 정보는 제공하지 않습니다.

   * 변수 유형: 이벤트
   * 유형:카운터

* **a.media.segmentView**

   방문자가 비디오 세그먼트의 일정 부분을 보았음을 나타냅니다. 그러나 방문자가 비디오에서 본 내용이나 분량에 대한 정보는 제공하지 않습니다.

   * 변수 유형: 이벤트
   * 유형:카운터

* **a.media.complete**

   사용자가 비디오 전체를 보았음을 의미합니다. 기본적으로 완료 이벤트는 비디오 종료 1초 전에 측정됩니다. 구현 중에 비디오 종료 몇 초 전을 보기 완료로 고려할 것인지 지정할 수 있습니다. 정의된 종료가 없는 라이브 비디오 및 기타 스트림의 경우, 예를 들어 특정 시간을 본 후 완료를 측정할 사용자 지정 지점을 지정할 수 있습니다.

   * 변수 유형: 이벤트
   * 유형:카운터

## 미디어 설정 구성 {#section_929945D4183C428AAF3B983EFD3E2500}

비디오를 추적하는 데 사용할 설정으로 `ADBMediaSettings` 객체를 구성합니다.

```objective-c
ADBMediaSettings *mediaSettings = [ADBMobile mediaCreateSettingsWithName:MEDIA_NAME  
length:MEDIA_LENGTH playerName:PLAYER_NAME playerID:PLAYER_ID]; 
 
// milestone tracking. Use either standard milestones (percentage of total length) 
// or offset milestones (seconds elapsed from the beginning of the video) 
mediaSettings.milestones = @"25,50,75"; 
mediaSettings.segmentByMilestones = YES; 
 
mediaSettings.offsetMilestones = @"60,120"; 
mediaSettings.segmentByOffsetMilestones = YES; 
 
// seconds tracking - sends a hit every x seconds 
mediaSettings.trackSeconds = 30; // sends a hit every 30 seconds 
 
// open the video 
[ADBMobile mediaOpenWithSettings:mediaSettings callback:nil]; 
 
// You are now ready to play the video, for example, [movieViewController.moviePlayer play]; 
// Note the mediaPlay, mediaStop and mediaClose methods are called in the 
// event handlers described in the next section
```

## 플레이어 이벤트 추적 {#section_C7F43AECBC0D425390F7FCDF3035B65D}

비디오 재생을 측정하려면 적절한 시간에 `mediaPlay`, `mediaStop` 및 `mediaClose` 메서드를 호출해야 합니다. 예를 들어 플레이어가 일시 중지된 경우에는 `mediaStop`입니다. 재생이 시작되거나 다시 시작된 경우에는 `mediaPlay`를 호출합니다.

다음 예에서는 알림을 구성하고 미디어 메서드를 호출하여 비디오를 측정하는 방법을 보여줍니다.

```objective-c
// configure notifications for when the video is finished, and when the 
media playback state changes 
 
- (void) configureNotifications:(MPMoviePlayerController *) movieController { 
 [[NSNotificationCenter defaultCenter] 
  addObserver: self 
  selector: @selector(mediaFinishedCallback:) 
  name: MPMoviePlayerPlaybackDidFinishNotification 
  object: movieController]; 
  
 [[NSNotificationCenter defaultCenter] 
  addObserver: self 
  selector: @selector(mediaPlaybackChangedCallback:) 
  name: MPMoviePlayerPlaybackStateDidChangeNotification 
  object: movieController]; 
} 
 
// define your notification callbacks. 
 
- (void) mediaFinishedCallback: (NSNotification*) notification { [ADBMobile mediaClose:MEDIA_NAME];} 
 
- (void) mediaPlaybackChangedCallback: (NSNotification*) notification { 
 MPMoviePlayerController *mediaController = notification.object; 
 if (mediaController.playbackState == MPMoviePlaybackStatePlaying) { 
  [ADBMobile mediaPlay:MEDIA_NAME offset: isnan(mediaController.currentPlaybackTime) ? 0.0 : mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateSeekingBackward) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateSeekingForward) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStatePaused) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateInterrupted) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateStopped) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
}
```

## 클래스 {#section_16838332727348F990305C0C6B0D795C}

### 클래스: ADBMediaSettings

```objective-c
bool segmentByMilestones; 
bool segmentByOffsetMilestones; 
double length; 
NSString *channel; 
NSString *name; 
NSString *playerName; 
NSString *playerID; 
NSString *milestones; 
NSString *offsetMilestones; 
NSUInteger trackSeconds; 
NSUInteger completeCloseOffsetThreshold; 
// settings used for ad tracking. For  
bool isMediaAd; 
double parentPodPosition; 
NSString *CPM; 
NSString *parentName; 
NSString *parentPod; 
```

### 클래스: ADBMediaState

```objective-c
bool ad; 
bool clicked; 
bool complete; 
bool eventFirstTime; 
double length; 
double offset; 
double percent; 
double segmentLength; 
double timePlayed; 
double timePlayedSinceTrack; 
double timestamp; 
NSDate *openTime  
NSString *name 
NSString *playerName 
NSString *mediaEvent 
NSString *segment 
NSUInteger milestone 
NSUInteger offsetMilestone 
NSUInteger segmentNum 
NSUInteger eventType
```

## 미디어 측정 클래스 및 메서드 참조 {#section_50DF9359A7B14DF092634C8E913C77FE}

* **mediaCreateSettings&#x200B;WithName:&#x200B;length:&#x200B;playerName:&#x200B;playerID:**

   지정된 매개 변수와 함께 `ADBMediaSettings` 개체를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      +(ADBMediaSettings *) mediaCreateSettingsWithName:(NSString *)name
                                                 length:(double)length
                                              playerName:(NSString *)playerName
                                               playerID:(NSString *)playerID;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBMediaSettings *myCatSettings =
            [ADBMobile mediaCreateSettingsWithName:@"catVideo"                                               length:85
                                        playerName:@"catVideoPlayer"
                                          playerID:@"catPlayerId"]; 
      ```

* **mediaAdCreateSettings&#x200B;WithName:&#x200B;length:&#x200B;playerName:&#x200B;parentName:&#x200B;parentPod:&#x200B;parentPodPosition:&#x200B;CPM:**

   광고 비디오 추적에 사용할 `ADBMediaSettings` 개체를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (ADBMediaSettings *) mediaAdCreateSettingsWithName:(NSString *)name
                                                    length:(double)length   
                                                playerName:(NSString *)playerName
                                                parentName:(NSString *)parentName
                                                 parentPod:(NSString *)parentPod
                                        parentPodPosition:(double)parentPodPosition
                                                      CPM:(NSString *)CPM; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
        ADBMediaSettings *mySettings = 
             [ADBMobile mediaAdCreateSettingsWithName:@"ad"                                       length:30
                                           playerName:@"adPlayer"
                                           parentName:@"catVideo"
                                           parentPod:@"catCollection"
                                           parentPodPosition:2
                                                        CPM:nil];
      ```

* **mediaOpenWithSettings:&#x200B;callback:**

   추적을 위해 `ADBMediaSettings` 개체를 엽니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) mediaOpenWithSettings:(ADBMediaSettings *)settings
                            callback:(void (^)(ADBMediaState *mediaState))callback; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile mediaOpenWithSettings:mySettings callback:^(ADBMediaState *mediaState) {
           // do something with media state if you want}];
      ```

* **mediaClose:**

   이름이 *name*&#x200B;인 미디어 항목을 닫습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
       + (void) mediaClose:(NSString *)name; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile mediaClose:@"kittiesPlaying"];
      ```

* **mediaPlay:&#x200B;offset:**

   제공된 *offset*(초)에서 이름이 *name*&#x200B;인 미디어 항목을 재생합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
       + (void) mediaPlay:(NSString *)name offset:(double)offset;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile mediaPlay:@"cats" offset:25];
      ```

* **mediaComplete:&#x200B;offset:**

   제공된 *오프셋*(초)에서 완료된 미디어 항목을 수동으로 표시합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
       + (void) mediaComplete:(NSString *)name offset:(double)offset;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
       [ADBMobile mediaComplete:@"meowzah" offset:90]; 
      ```

* **mediaStop:&#x200B;offset:**

   *제공된 오프셋에서 비디오가 중지 또는 일시 중지되었음을 미디어 모듈에 알립니다*.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) mediaStop:(NSString *)name offset:(double)offset; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile mediaStop:@"toonses" offset:30]; 
      ```

* **mediaClick:&#x200B;offset:**

   미디어 항목이 클릭되었음을 미디어 모듈에 알립니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) mediaClick:(NSString *)name offset:(double)offset;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile mediaClick:@"soManyCats" offset:47];
      ```

* **mediaTrack:&#x200B;withData:**

   현재 미디어 상태에 대한 추적 작업 호출(페이지 보기 없음)을 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) mediaTrack:(NSString *)name withData:(NSDictionary *)data;
      ```

