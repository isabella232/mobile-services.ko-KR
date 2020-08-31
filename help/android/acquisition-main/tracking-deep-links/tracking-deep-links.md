---
description: 다음은 Adobe Mobile Android SDK를 사용하여 모바일 앱에서 딥링크와 지연된 딥링크를 추적하는 데 유용한 정보입니다.
keywords: android;library;mobile;sdk
seo-description: 다음은 Adobe Mobile Android SDK를 사용하여 모바일 앱에서 딥링크와 지연된 딥링크를 추적하는 데 유용한 정보입니다.
seo-title: Adobe Mobile Services의 딥링크 추적
solution: Marketing Cloud,Analytics
title: 딥링크 추적
topic: Developer and implementation
uuid: ebb1c08c-a246-40b3-9ac6-4606a14b4c5a
translation-type: ht
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: ht
source-wordcount: '330'
ht-degree: 100%

---


# 딥링크 추적 {#tracking-deep-links}

다음은 Adobe Mobile Android SDK를 사용하여 모바일 앱에서 딥링크와 지연된 딥링크를 추적하는 데 유용한 정보입니다.

## 딥링크 추적

1. SDK를 프로젝트에 추가하고 라이프사이클 지표를 구현합니다.

   자세한 내용은 [핵심 구현 및 라이프사이클](/help/android/getting-started/dev-qs.md)에서 *IntelliJ IDEA 또는 Eclipse 프로젝트에 SDK 및 구성 파일 추가*&#x200B;를 참조하십시오.

1. URL을 처리할 애플리케이션을 등록합니다.

   자세한 내용은 [URL](https://developer.android.com/training/basics/intents/filters.html)을 참조하십시오.
1. `collectLifecycleData`를 사용하여 Adobe SDK에 대한 딥링크 목적이 있는 활동을 전달합니다.

   딥링크 추적 샘플은 다음과 같습니다.

   ```java
   public class ParseDeepLinkActivity extends Activity { 
       @Override 
       protected void onCreate(Bundle savedInstanceState) { 
           super.onCreate(savedInstanceState); 
   
           Config.collectLifecycleData(this); 
           ... 
       } 
   }
   ```

Adobe Mobile SDK는 임의의 딥링크 또는 범용 링크에 `a.deeplink.id` 레이블과 해당하는 null이 아닌 사용자 생성 값이 포함된 키가 있을 경우 링크에 추가된 데이터의 키 및 값 쌍을 구문 분석할 수 있습니다. 링크에 키 및 값이 포함되어 있는 한 해당 링크에 추가된 모든 키 및 값 쌍은 구문 분석하여 라이프사이클 히트에 추가된 다음 `a.deeplink.id`Adobe Analytics로 전송됩니다.

또한 사용자 생성 값을 포함한 다음 예약 키 중 하나 이상을 딥링크 또는 범용 링크에 추가할 수도 있습니다.

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

이 키는 Adobe Analytics에 보고하기 위해 사전에 매핑된 변수입니다. 매핑 및 처리 규칙에 대한 자세한 내용은 [처리 규칙 및 컨텍스트 데이터](https://docs.adobe.com/content/help/ko-KR/analytics/admin/admin-tools/processing-rules/processing-rules.html)를 참조하십시오.

## 지연된 딥링크 추적(마케팅 링크용)

지연된 딥링크를 사용하면 Adobe SDK에서 의도 데이터로 딥링크가 있는 새 의도 링크를 엽니다. 이 프로세스는 위의 코드를 사용하여 외부 딥링크로 처리됩니다.

## 딥링크 공개 정보 {#section_1815396353614DA8A63D8D92112217E7}

### 상수

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```

