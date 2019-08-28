---
description: Android 애플리케이션에서 타깃팅된 콘텐츠를 제공할 수 있습니다.
keywords: Android; 라이브러리; 모바일; SDK
seo-description: Android 애플리케이션에서 타깃팅된 콘텐츠를 제공할 수 있습니다.
seo-title: Target 구성
solution: Marketing Cloud, Analytics
title: Target 구성
topic: 개발자 및 구현
uuid: 09 FE 2 C 9 C -7 B 60-49 C 3-BB 9 D -36 A 30 CE 7 C 350
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Target configuration {#target-configuration}

Android 애플리케이션에서 타깃팅된 콘텐츠를 제공할 수 있습니다.

## Set the application context {#section_37CAE496FF894FCA821F7760605574CA}

**(필수)** `setContext()` 메서드는 주 활동의 `onCreate()` 메서드에서 한 번 호출해야 합니다.

예:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Analytics 또는 Audience Management를 구현할 때 이미 이 메서드 호출을 추가한 경우 다시 추가할 필요는 없습니다.
