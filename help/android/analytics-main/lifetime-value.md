---
description: 라이프타임 값을 사용하면 각 Android 사용자에 대한 라이프타임 값을 측정하고 타깃팅할 수 있습니다. 이 값을 사용하여 라이프타임 구매, 광고 보기, 비디오 완료, 소셜 공유, 사진 업로드 등을 저장할 수 있습니다.
seo-description: 라이프타임 값을 사용하면 각 Android 사용자에 대한 라이프타임 값을 측정하고 타깃팅할 수 있습니다. 이 값을 사용하여 라이프타임 구매, 광고 보기, 비디오 완료, 소셜 공유, 사진 업로드 등을 저장할 수 있습니다.
seo-title: 방문자 라이프타임 값
solution: Marketing Cloud,Analytics
title: 방문자 라이프타임 값
topic: Developer and implementation
uuid: ba0308de-282e-46f9-a14c-19fb6d5c363e
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 52%

---


# 방문자 라이프타임 값 {#visitor-lifetime-value}

라이프타임 값을 사용하면 각 Android 사용자에 대한 라이프타임 값을 측정하고 타깃팅할 수 있습니다. 이 값을 사용하여 라이프타임 구매, 광고 보기, 비디오 완료, 소셜 공유, 사진 업로드 등을 저장할 수 있습니다.

`trackLifetimeValueIncrease`를 사용하여 값을 보낼 때마다 값이 기존 값에 추가됩니다. 라이프타임 값은 장치에 저장되며 `lifetimeValue`를 호출하여 언제든지 검색할 수 있습니다. 

## 방문자 라이프타임 값 추적 {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 [핵심 구현 및 라이프사이클](/help/android/getting-started/dev-qs.md)에서 *IntelliJ IDEA 또는 Eclipse 프로젝트에 SDK 및 구성 파일 추가*&#x200B;를 참조하십시오.
1. 라이브러리를 가져옵니다:

   ```java
   import com.adobe.mobile.*;
   ```

1. 값과 함께 `trackLifetimeValueIncrease`를 호출하여 값을 늘립니다.

   ```java
   Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), null);
   ```

## 추가 데이터 보내기 {#section_3EBE813E54A24F6FB669B2478B5661F9}

라이프타임 값 외에, 각 작업 추적 호출로 추가 컨텍스트 데이터를 전송할 수 있습니다.

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), cdata);
```

컨텍스트 데이터 값은 Adobe Mobile Services에서 사용자 지정 변수에 매핑되어야 합니다.

![](assets/map-variable-context-ltv.png)

