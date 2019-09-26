---
description: 비콘 추적에서 iBeacon 및 Bluetooth 저전력을 사용하여 미세한 위치를 측정하고 타깃팅할 수 있습니다.
keywords: android;library;mobile;sdk
seo-description: 비콘 추적에서 iBeacon 및 Bluetooth 저전력을 사용하여 미세한 위치를 측정하고 타깃팅할 수 있습니다.
seo-title: 비콘 추적
solution: Marketing Cloud,Analytics
title: 비콘 추적
topic: 개발자 및 구현
uuid: 16c1d267-85f4-4a6a6d3-d6ffb0f80b29
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# 비콘 추적 {#beacon-tracking}

비콘 추적에서 iBeacon 및 Bluetooth 저전력을 사용하여 미세한 위치를 측정하고 타깃팅할 수 있습니다.

`trackBeacon`이 호출되면 다음 비콘 데이터가 Analytics 및 Target으로 전송됩니다.

* `a.beacon.uuid` - 비콘의 ProximityUUID
* `a.beacon.major` - 주 비콘 번호(예: 스토어 번호)
* `a.beacon.minor` - 부 비콘 번호(예 : 스토어 내 고유 번호)
* `a.beacon.prox` - 0-3 값은 사용자와 비콘이 얼마나 가까운지 나타냅니다.

이 값들의 의미는 다음과 같습니다.

* 0 = 알 수 없음
* 1 = 바로 인접함
* 2 = 가까움
* 3 = 멈

이러한 비콘 데이터는 모바일 솔루션 변수에 캡처됩니다.

## 비콘 추적 {#section_FC3F213545944A468B1E6D5D5C8E2F1F}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 코어 *구현 및 라이프사이클에서 IntelliJ IDEA 또는 Eclipse 프로젝트에* SDK 및 구성 파일 [추가를 참조하십시오](/help/android/getting-started/dev-qs.md).

1. 라이브러리를 가져옵니다:

   ```java
   import com.adobe.mobile.*;
   ```

1. 비콘 위치를 수집합니다.

   비콘 제조업체에 따라 여러 타사 라이브러리를 사용하여 블루투스 LE 비콘을 스캔할 수 있습니다.
1. 비콘 정보를 획득했으면 다음 호출을 사용하여 위치를 추적하십시오.

   ```java
   // assumed that the following variables will have been retrieved by the 3rd party beacon library 
   String beaconUUID; 
   String major; 
   String minor; 
   Analytics.BEACON_PROXIMITY proximity;  
   // BEACON_PROXIMITY is an enum available in the SDK. Number 0-3 representing how close the 
   // user is to the beacon. 0 unknown, 1 immediate, 2 near, 3 far.  
   Analytics.trackBeacon(beaconUUID, major, minor, proximity, null);
   ```

1. 사용자가 비콘 근접 위치를 벗어나면 현재 비콘을 지웁니다.

   ```java
   Analytics.clearBeacon();
   ```

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

비콘 데이터 외에도 각 `trackBeacon` 호출에서 추가 컨텍스트 데이터를 전송할 수 있습니다.

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackBeacon(beaconUUID, major, minor, proximity, cdata);
```

컨텍스트 데이터 값은 Adobe Mobile Services의 사용자 지정 변수에 매핑해야 합니다.

![](assets/map-variable-context-ltv.png)

