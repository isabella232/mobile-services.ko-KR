---
description: products 변수는 처리 규칙을 사용하여 설정할 수 없습니다. iOS 4.x SDK에서 컨텍스트 데이터 매개 변수에 특수 구문을 사용하여 서버 호출에 대해 직접 products를 설정해야 합니다.
seo-description: products 변수는 처리 규칙을 사용하여 설정할 수 없습니다. iOS 4.x SDK에서 컨텍스트 데이터 매개 변수에 특수 구문을 사용하여 서버 호출에 대해 직접 products를 설정해야 합니다.
seo-title: products 변수
solution: Marketing Cloud, Analytics
title: products 변수
topic: 개발자 및 구현
uuid: 6 ece 4 d 27-ef 86-435 c-a 6 f 7-bd 76 be 1 c 95 ca
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products variable {#products-variable}

products 변수는 처리 규칙을 사용하여 설정할 수 없습니다. iOS 4.x SDK에서 컨텍스트 데이터 매개 변수에 특수 구문을 사용하여 서버 호출에 대해 직접 products를 설정해야 합니다.

*`products`* 변수를 설정하려면 컨텍스트 데이터 키를 설정하고 `"&&products"`*`products`* 변수에 대해 정의된 구문을 사용하여 값을 설정합니다.

```objective-c
[contextData setObject:@"Category;Product;Quantity;Price[,Category;Product;Quantity;Price]" forKey:@"&&products"];
```

예:

```objective-c
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
[contextData setObject:@";Running Shoes;1;69.95,;Running Socks;10;29.99" forKey:@"&&products"]; 
[contextData setObject:@"1234567890" forKey:@"m.purchaseid"]; 
[contextData setObject:@"1" forKey:@"m.purchase"]; 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"purchase" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"Order Confirmation" data:contextData]; 
```

*`products`* 는 이미지 요청에 직접 설정되며 다른 변수는 컨텍스트 데이터로 설정됩니다. 모든 컨텍스트 데이터 변수는 처리 규칙을 사용하여 매핑해야 합니다.

![](assets/map-products.png)

이 변수는 SDK에서 직업 이미지 요청에 설정했기 때문에 *`products`* 변수를 처리 규칙에 따라 매핑할 필요는 없습니다.
