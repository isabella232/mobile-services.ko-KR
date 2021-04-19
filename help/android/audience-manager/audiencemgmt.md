---
description: 고객 관리에서 신호를 전송하여 방문자 세그먼트를 검색할 수 있습니다.
keywords: android;라이브러리;모바일;sdk
seo-description: 고객 관리에서 신호를 전송하여 방문자 세그먼트를 검색할 수 있습니다.
seo-title: Audience Manager 구성
solution: Experience Cloud,Analytics
title: Audience Manager 구성
topic-fix: Developer and implementation
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
exl-id: 05033748-5461-482f-a01d-1ba73f64616a
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 100%

---

# Audience Manager 구성{#audience-manager-configuration}

Audience Manager에서 신호를 전송하여 방문자 세그먼트를 검색할 수 있습니다.

## 애플리케이션 컨텍스트 설정 {#section_37CAE496FF894FCA821F7760605574CA}

****(필수) `setContext()` 메서드는 기본 활동의 `onCreate()` 메서드에서 한 번 호출해야 합니다.

다음은 이 메서드의 코드 샘플입니다.

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Analytics 또는 Target을 구현할 때 이미 이 메서드 호출을 추가한 경우 다시 추가할 필요가 없습니다.
