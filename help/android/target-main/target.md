---
description: Android 애플리케이션에서 타깃팅된 콘텐츠를 제공할 수 있습니다.
keywords: android;라이브러리;모바일;sdk
seo-description: Android 애플리케이션에서 타깃팅된 콘텐츠를 제공할 수 있습니다.
seo-title: Target 구성
solution: Experience Cloud,Analytics
title: Target 구성
topic-fix: Developer and implementation
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
exl-id: dbcc3114-e76b-4b18-a418-ac46a21a593e
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '76'
ht-degree: 100%

---

# Target 구성 {#target-configuration}

Android 애플리케이션에서 타깃팅된 콘텐츠를 제공할 수 있습니다.

## 애플리케이션 컨텍스트 설정 {#section_37CAE496FF894FCA821F7760605574CA}

****(필수) `setContext()` 메서드는 기본 활동의 `onCreate()` 메서드에서 한 번 호출해야 합니다.

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
