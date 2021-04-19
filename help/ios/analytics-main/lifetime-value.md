---
description: 라이프타임 값을 통해 각 사용자의 라이프타임 값을 측정하고 타깃팅할 수 있습니다.
seo-description: 라이프타임 값을 통해 각 사용자의 라이프타임 값을 측정하고 타깃팅할 수 있습니다.
seo-title: 방문자 라이프타임 값
solution: Experience Cloud,Analytics
title: 방문자 라이프타임 값
topic-fix: Developer and implementation
uuid: d830d18b-4313-43bb-8d75-3789869d0f1d
exl-id: f1b684b1-9919-400d-a88a-6d4a0809d9e1
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 100%

---

# 방문자 라이프타임 값 {#visitor-lifetime-value}

라이프타임 값을 통해 각 사용자의 라이프타임 값을 측정하고 타깃팅할 수 있습니다.

`trackLifetimeValueIncrease`를 사용하여 값을 보낼 때마다 값이 기존 값에 추가됩니다. 라이프타임 값은 장치에 저장되며 `lifetimeValue`를 호출하여 언제든지 검색할 수 있습니다. 이 값은 라이프타임 구매, 광고 보기, 비디오 전체 보기, 소셜 네트워크 공유, 사진 업로드 등을 저장하는 데 사용할 수 있습니다.

## 방문자 라이프타임 값 추적 {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 [핵심 구현 및 라이프사이클](/help/ios/getting-started/dev-qs.md)에서 *프로젝트에 SDK 및 구성 파일 추가*&#x200B;를 참조하십시오.
1. 라이브러리를 가져옵니다:

   ```objective-c
   import com.adobe.mobile.*;
   ```

1. 값과 함께 `trackLifetimeValueIncrease`를 호출하여 값을 늘립니다.

   ```objective-c
   [ADBMobile trackLifetimeValueIncrease:increaseAmount data:nil];
   ```

## 추가 데이터 보내기 {#section_3EBE813E54A24F6FB669B2478B5661F9}

라이프타임 값 외에, 각 작업 추적 호출로 추가 컨텍스트 데이터를 전송할 수 있습니다.

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:imageName forKey:@"myapp.ImageLiked"]; 
[ADBMobile trackLifetimeValueIncrease:increaseAmount data:contextData];
```

컨텍스트 데이터 사용자 지정 변수에 매핑해야 합니다.

![](assets/map-variable-context-ltv.png)
