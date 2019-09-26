---
description: 머천다이징 eVar 및 제품별 이벤트의 products 변수의 예입니다.
seo-description: 머천다이징 eVar 및 제품별 이벤트의 products 변수의 예입니다.
seo-title: 머천다이징 eVar 및 제품 특화 이벤트가 포함된 products 변수
solution: Marketing Cloud,Analytics
title: 머천다이징 eVar 및 제품 특화 이벤트가 포함된 products 변수
topic: 개발자 및 구현
uuid: 94e882e4-b19d-4c48-9dfb-331465490347
translation-type: tm+mt
source-git-commit: b630c5cf09be7fbe31018cbf50564001eb6e2a5a

---


# Products variable with merchandising eVars and product-specific events{#products-variable-with-merchandising-evars-and-product-specific-events}

머천다이징 eVar 및 제품별 이벤트의 products 변수의 예입니다.

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
>변수를 사용하여 제품별 이벤트를 트리거하는 경우 *`&&products`* *`&&events`* 변수에서 해당 이벤트를 설정해야 하며, 그렇지 않으면 처리 중에 이벤트가 필터링됩니다.

