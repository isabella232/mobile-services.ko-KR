---
description: 다음은 머천다이징 eVar 및 제품별 이벤트의 products 변수의 예입니다.
seo-description: 다음은 머천다이징 eVar 및 제품별 이벤트의 products 변수의 예입니다.
seo-title: 머천다이징 eVar 및 제품별 이벤트가 포함된 Products 변수
solution: Experience Cloud,Analytics
title: 머천다이징 eVar 및 제품별 이벤트가 포함된 Products 변수
topic: Developer and implementation
uuid: f913211e-97ad-4237-bfe4-7ded01295caf
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 100%

---


# 머천다이징 eVar 및 제품별 이벤트가 포함된 Products 변수 {#products-variable-with-merchandising-evars-and-product-specific-events}

다음은 머천다이징 eVar 및 제품별 이벤트의 products 변수의 예입니다.

```
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
[contextData setObject:@"event1" forKey:@"&&events"]; 
[contextData setObject:@";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99" forKey:@"&&products"]; 
[contextData setObject:@"1234567890" forKey:@"m.purchaseid"]; 
[contextData setObject:@"1" forKey:@"m.purchase"]; 
  
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"purchase" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"Order Confirmation" data:contextData];
```

>[!TIP]
>
>*`&&products`* 변수를 사용하여 제품별 이벤트를 트리거하는 경우 *`&&events`* 변수에서도 해당 이벤트를 설정해야 합니다. 이 이벤트를 설정하지 않으면 처리하는 동안 필터링됩니다.

