---
description: Android 애플리케이션에서 타깃팅된 콘텐츠를 제공할 수 있습니다.
keywords: android;library;mobile;sdk
seo-description: Android 애플리케이션에서 타깃팅된 콘텐츠를 제공할 수 있습니다.
seo-title: 타겟 구성
solution: Marketing Cloud,Analytics
title: Target configuration
topic: 개발자 및 구현
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Target configuration {#target-configuration}

Android 애플리케이션에서 타깃팅된 콘텐츠를 제공할 수 있습니다.

## Set the application context {#section_37CAE496FF894FCA821F7760605574CA}

**(Required) The  method must be called once in the  method of your main activity.**`setContext()``onCreate()`

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
