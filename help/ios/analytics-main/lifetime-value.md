---
description: 라이프타임 값을 통해 각 사용자의 라이프타임 값을 측정하고 타깃팅할 수 있습니다.
seo-description: 라이프타임 값을 통해 각 사용자의 라이프타임 값을 측정하고 타깃팅할 수 있습니다.
seo-title: 방문자 라이프타임 값
solution: Marketing Cloud,Analytics
title: Visitor lifetime value
topic: 개발자 및 구현
uuid: d830d18b-4313-43bb-8d75-3789869d0f1d
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Visitor lifetime value {#visitor-lifetime-value}

라이프타임 값을 통해 각 사용자의 라이프타임 값을 측정하고 타깃팅할 수 있습니다.

`trackLifetimeValueIncrease`를 사용하여 값을 보낼 때마다 값이 기존 값에 추가됩니다. 라이프타임 값은 장치에 저장되며 `lifetimeValue`를 호출하여 언제든지 검색할 수 있습니다. 이 값은 라이프타임 구매, 광고 보기, 비디오 전체 보기, 소셜 네트워크 공유, 사진 업로드 등을 저장하는 데 사용할 수 있습니다.

## Track the visitor lifetime value {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 핵심 구현 *및 라이프사이클에서 SDK 및 구성* 파일을 프로젝트에 [추가를 참조하십시오](/help/ios/getting-started/dev-qs.md).
1. 라이브러리를 가져옵니다:

   ```objective-c
   import com.adobe.mobile.*;
   ```

1. 값과 함께 `trackLifetimeValueIncrease`를 호출하여 값을 늘립니다.

   ```objective-c
   [ADBMobile trackLifetimeValueIncrease:increaseAmount data:nil];
   ```

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

라이프타임 값 외에, 각 작업 추적 호출로 추가 컨텍스트 데이터를 전송할 수 있습니다.

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:imageName forKey:@"myapp.ImageLiked"]; 
[ADBMobile trackLifetimeValueIncrease:increaseAmount data:contextData];
```

Context data values must be mapped to custom variables:

![](assets/map-variable-context-ltv.png)

