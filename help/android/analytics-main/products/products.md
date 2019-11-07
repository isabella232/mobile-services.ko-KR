---
description: products 변수는 처리 규칙을 사용하여 설정할 수 없습니다. Mobile SDK에서 컨텍스트 데이터 매개 변수에 특수 구문을 사용하여 서버 호출에 대해 products를 설정해야 합니다.
keywords: android;라이브러리;모바일;sdk
seo-description: products 변수는 처리 규칙을 사용하여 설정할 수 없습니다. Mobile SDK에서 컨텍스트 데이터 매개 변수에 특수 구문을 사용하여 서버 호출에 대해 products를 설정해야 합니다.
seo-title: products 변수
solution: Marketing Cloud,Analytics
title: products 변수
topic: 개발자 및 구현
uuid: f4484022-cb8b-4dea-9209-5a110ba607df
translation-type: ht
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products 변수 {#products-variable}

products 변수는 처리 규칙을 사용하여 설정할 수 없습니다. Mobile SDK에서 컨텍스트 데이터 매개 변수에 특수 구문을 사용하여 서버 호출에 대해 products를 설정해야 합니다.

*products* 변수를 설정하려면 컨텍스트 데이터 키를 `"&&products"`로 설정하고 *products* 변수에 대해 정의된 구문을 사용하여 값을 설정하십시오.

```java
cdata.put("&&products", "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]");
```

예:

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata.put("&&products", ";Running Shoes;1;69.95,;Running Socks;10;29.99"); 
cdata.put("myapp.purchase", "1"); 
cdata.put("myapp.purchaseid", "1234567890"); 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("purchase", cdata); 
// trackState example: 
Analytics.trackState("Order Confirmation", cdata);
```

*products* 변수는 이미지 요청에 설정되고 다른 변수는 컨텍스트 데이터로 설정됩니다. 모든 컨텍스트 데이터 변수는 처리 규칙을 사용하여 매핑해야 합니다.

![](assets/map-products.png)

이 변수는 SDK에서 직접 이미지 요청에 설정했기 때문에 *products* 변수를 처리 규칙에 따라 매핑할 필요는 없습니다.
