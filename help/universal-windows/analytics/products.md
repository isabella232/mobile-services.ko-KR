---
description: 처리 규칙을 사용하여 제품 변수를 설정할 수 없습니다. 모바일 SDK에서는 컨텍스트 데이터 매개 변수 내의 특수 구문을 사용하여 서버 호출에서 직접 제품을 설정해야 합니다.
seo-description: 처리 규칙을 사용하여 제품 변수를 설정할 수 없습니다. 모바일 SDK에서는 컨텍스트 데이터 매개 변수 내의 특수 구문을 사용하여 서버 호출에서 직접 제품을 설정해야 합니다.
seo-title: Products 변수
solution: Experience Cloud,Analytics
title: Products 변수
topic: Developer and implementation
uuid: 607983d6-48ac-4274-bfc8-b1ca4e5dad1b
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 7%

---


# Products 변수 {#products-variable}

처리 규칙을 사용하여 제품 변수를 설정할 수 없습니다. 모바일 SDK에서는 컨텍스트 데이터 매개 변수 내의 특수 구문을 사용하여 서버 호출에서 직접 제품을 설정해야 합니다.

To set the *`products`* variable, set a context data key to `"&&products"`, and set the value using the syntax defined for the *`products` variable:

```js
cdata["&&products"] = "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]";
```

예:

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&products"] = ";Running Shoes;1;69.95,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

The *`products`* is set directly on the image request, and the other variables are set as context data. 모든 컨텍스트 데이터 변수는 처리 규칙을 사용하여 매핑해야 합니다.

![](assets/products-procrules.png)

SDK에서 이미지 요청에 직접 설정되므로 처리 규칙을 사용하여 *`products`* 변수를 매핑할 필요가 없습니다.

## 머천다이징 eVar 및 제품별 이벤트가 포함된 Products 변수 {#section_685D53AD3D064F9A8E225F995A9BA545}

An example of the *`products`* variable with Merchandising eVars and product-specific events.

```
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&events"] = "event1 "; 
cdata["&&products"] = ";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
  
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

>[!TIP]
>
>변수를 사용하여 제품별 이벤트를 트리거하는 경우 *`&&products`* *`&&events`* 변수에서 해당 이벤트도 설정해야 하며, 그렇지 않으면 처리 중에 이벤트가 필터링됩니다.

