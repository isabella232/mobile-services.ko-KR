---
description: 다음은 Adobe Mobile Android SDK를 사용하여 모바일 앱에서 딥링크와 지연된 딥링크를 추적하는 데 유용한 정보입니다.
keywords: Android; 라이브러리; 모바일; SDK
seo-description: 다음은 Adobe Mobile Android SDK를 사용하여 모바일 앱에서 딥링크와 지연된 딥링크를 추적하는 데 유용한 정보입니다.
seo-title: Adobe Mobile Services의 딥 링크 추적
solution: Marketing Cloud, Analytics
title: 딥링크 추적
topic: 개발자 및 구현
uuid: EBB 1 C 08 C-A 246-40 B 3-9 AC 6-4606 A 14 B 4 C 5 A
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Tracking deep links {#tracking-deep-links}

다음은 Adobe Mobile Android SDK를 사용하여 모바일 앱에서 딥링크와 지연된 딥링크를 추적하는 데 유용한 정보입니다.

## 딥 링크 추적

1. SDK를 프로젝트에 추가하고 라이프사이클 지표를 구현합니다.

   자세한 내용은 *SDK 및 구성 파일을 핵심 구현 및 라이프사이클에서 intellij 아이디어 또는 Eclipse 프로젝트에* [추가할 수 있습니다.](/help/android/getting-started/dev-qs.md)

1. URL을 처리할 애플리케이션을 등록합니다.

   자세한 내용은 [URL](https://developer.android.com/training/basics/intents/filters.html)를 참조하십시오.
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

The Adobe Mobile] SDK can parse key and value pairs of data that is appended to any Deep or Universal Link as long as the link contains a key with the `a.deeplink.id` label and a corresponding non-null and user-generated value. All key and value pairs of data that are appended to the link will be parsed, attached to a lifecycle hit, and sent to Adobe Analytics] as long as the link contains the `a.deeplink.id` key and value.

또한, 다음 예약 키 중 하나 이상을 딥 또는 범용 링크에 사용자 생성 값으로 추가할 수 있습니다.

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

이 키는 Adobe Analytics에 보고하기 위해 사전에 매핑된 변수입니다. 매핑 및 처리 규칙에 대한 자세한 내용은 [처리 규칙 및 컨텍스트 데이터](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)를 참조하십시오.

## 지연된 딥 링크 추적 (마케팅 링크에서 사용하기 위해)

지연 딥링크가 있으면 Adobe SDK에서는 딥링크가 포함된 새로운 인텐트가 인텐트 데이터로 열립니다. 이 프로세스는 위의 코드를 사용하여 외부 딥링크로 처리됩니다.

## Deep link public information {#section_1815396353614DA8A63D8D92112217E7}

### 상수

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```

