---
description: 처리 규칙을 사용하여 제품 변수를 설정할 수 없습니다. 모바일 SDK에서는 서버 호출 시 제품을 직접 설정하려면 컨텍스트 데이터 매개 변수 내의 특수 구문을 사용해야 합니다.
solution: Experience Cloud,Analytics
title: Products 변수
topic-fix: Developer and implementation
uuid: 2057a564-06ae-4171-bbe7-0baffa71608b
exl-id: b731e794-7134-4c6d-a41b-09ac9b84763d
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 15%

---

# Products 변수{#products-variable}

처리 규칙을 사용하여 제품 변수를 설정할 수 없습니다. 모바일 SDK에서는 서버 호출 시 제품을 직접 설정하려면 컨텍스트 데이터 매개 변수 내의 특수 구문을 사용해야 합니다.

*`products`* 변수를 설정하려면 컨텍스트 데이터 키를 `"&&products"`로 설정하고 *`products`*&#x200B;에 대해 정의된 구문을 사용하여 값을 설정하십시오.

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

*`products`*&#x200B;는 이미지 요청에 직접 설정되고 다른 변수는 컨텍스트 데이터로 설정됩니다. 모든 컨텍스트 데이터 변수는 처리 규칙을 사용하여 매핑해야 합니다.

![](assets/products-procrules.png)

*`products`* 변수는 SDK에서 이미지 요청에 직접 설정되므로 처리 규칙을 사용하여 매핑할 필요가 없습니다.
