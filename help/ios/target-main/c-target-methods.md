---
description: 다음은 iOS 라이브러리에서 제공하는 Adobe Target 메서드 목록입니다.
seo-description: 다음은 iOS 라이브러리에서 제공하는 Adobe Target 메서드 목록입니다.
seo-title: Adobe Mobile Services 용 iOS Target 메서드
solution: Marketing Cloud, Analytics
title: Ios 용 타겟 메서드
topic: 개발자 및 구현
uuid: 692 BCDA 1-02 BA -4902-BD 65-15888 ADF 1952
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Ios 용 타겟 메서드 {#target-methods}

다음은 iOS 라이브러리에서 제공하는 Adobe Target 메서드 목록입니다.

SDK는 현재 Analytics, Target, Audience Manager 및 Adobe Experience Platform Identity Service를 비롯한 다양한 Adobe Experience Cloud 솔루션에 대한 지원을 제공합니다. 메서드에는 솔루션에 따라 접두사가 붙습니다. 예를 들어 메서드의 경우 앞에 `target`target이 붙습니다.

>[!TIP]
>
>라이프사이클 지표는 각 mbox 로드에 매개 변수로 전송됩니다. 자세한 내용은 [라이프사이클 지표](/help/ios/metrics.md)를 참조하십시오.

## 클래스 참조: Adbtargetlocationrequest

### 속성

```objective-c
NSString *name; 
NSString *defaultContent; 
NSMutableDictionary *parameters;
```

### 문자열 상수

>[!TIP]
>
>사용자 지정 매개 변수에 대한 키를 설정할 때 다음 상수를 사용할 수 있습니다.

```iOS
NSString *const ADBTargetParameterOrderId; 
NSString *const ADBTargetParameterOrderTotal; 
NSString *const ADBTargetParameterProductPurchasedId; 
NSString *const ADBTargetParameterCategoryId; 
NSString *const ADBTargetParameterMbox3rdPartyId; 
NSString *const ADBTargetParameterMboxPageValue; 
NSString *const ADBTargetParameterMboxPc; 
NSString *const ADBTargetParameterMboxSessionId; 
NSString *const ADBTargetParameterMboxHost;
```

>[!IMPORTANT]
>
>* If you are using SDKs **before** version 4.14.0, see [Input Parameters](https://developers.adobetarget.com/api/#input-parameters) for parameters limitations.
   >
   >
* If you are using SDKs version 4.14.0 **or after**, see [Batch Input Parameters](https://developers.adobetarget.com/api/#batch-input-parameters) for parameters limitations.


### 메서드에서 사용할 수 있습니다

* **targetLoadRequest:&#x200B;callback**

   구성된 Target 서버에 request를 보내고 차단 `callback`에서 생성된 오퍼의 문자열 값을 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) targetLoadRequest:(ADBTargetLocationRequest *)request
                        callback:(void (^)(NSString *content))callback;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile targetLoadRequest:myRequest
                          callback:^(NSString *content) {
                            // do something with content
                          }];
      ```

* **targetLoadRequestWithName:defaultContent:profileParameters:orderParameters:mboxParameters:requestLocationParameters:callback:**

   구성된 Target 서버에 request를 보내고 차단 콜백에서 생성된 오퍼의 문자열 값을 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) targetLoadRequestWithName:(nullable NSString *)name
                          defaultContent:(nullable NSString *)defaultContent
                      profileParameters:(nullable NSDictionary *)profileParameters
                        orderParameters:(nullable NSDictionary *)orderParameters
                         mboxParameters:(nullable NSDictionary *)mboxParameters
                requestLocationParameters:(nullable NSDictionary *)requestLocationParameters
                                 callback:(nullable void (^)(NSString
                                 * __nullable content))callback;
      ```

   * 반환: 해당 없음

   * 다음은 이 메서드의 매개 변수입니다.

      * **`name`**

         검색할 Target mbox/위치의 이름입니다.

         * **유형**: NSString*
      * **`defaultContent`**

         Target 서버에 도달할 수 없거나 사용자가 캠페인에 적합하지 않은 경우 콜백에서 반환되는 값입니다.

         * **유형**: NSString*
      * **`profileParameters`**

         이 사전의 값은 Target에 전송되는 요청의 "profileParameters" 개체에 삽입합니다.

         * **유형**: NSDictionary*
      * **`orderParameters`**

         이 사전의 값은 Target에 전송되는 요청의 "order" 개체에 삽입합니다.

         * **유형**: NSDictionary
      * **`mboxParameters`**

         이 사전의 값은 Target에 전송되는 요청의 "mboxParameters" 개체에 삽입합니다.

         * **유형**: NSDictionary*
      * **`requestLocationParameters`**

         이 사전의 값은 Target에 전송되는 요청의 "requestLocation" 개체에 삽입됩니다.

         **유형**: NSDictionary*

      * **`callback`**

         이 메서드는 Target 서버의 오퍼 콘텐츠를 사용하여 호출됩니다. Target 서버에 연결할 수 없거나 사용자가 캠페인에 적합하지 않으면 defaultContent가 반환됩니다.
      **유형**: Function

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile targetLoadRequestWithName:@"myHeroBanner"
                            defaultContent:@"defaultHeroBanner.png"
                        profileParameters:@{@"age":@"20-29"}
                          orderParameters:nil
                           mboxParameters:@{@"customParam":@"customValue"}
                requestLocationParameters:@{@"host":@"my.hostname.com"}
                                 callback:^(NSString *content){
                                   // do something with content
                                   myImageView.image = [UIImage imageNamed:content];
                                 }];
      ```

      기본 타겟 API에 대한 자세한 내용은 [Adobe Target 개발자를](https://docs.adobe.com/dev/products/target/reference/delivery.html)참조하십시오.







* **targetLoadRequestWithName:defaultContent:profileParameters:orderParameters:mboxParameters:callback**

   구성된 Target 서버에 요청을 보내고 차단 callback에서 생성된 오퍼의 문자열 값을 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) targetLoadRequestWithName:(nullable NSString *)name
                          defaultContent:(nullable NSString *)defaultContent
                      profileParameters:(nullable NSDictionary *)profileParameters
                        orderParameters:(nullable NSDictionary *)orderParameters
                         mboxParameters:(nullable NSDictionary *)mboxParameters
                               callback:(nullable void (^)(NSString * __nullable content))callback;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile targetLoadRequestWithName:@"mboxName"
                            defaultContent:@"defaultContent"
                         profileParameters:{@"profile-parameter-key": @"profile-parameter-value"}
                           orderParameters:@{@"order-parameter-key": @"order-parameter-value"}
                            mboxParameters:@{@"mbox-parameter-key": @"mbox-parameter-value"}
                                   callback:^(NSString * content) {
                                           //do something with content 
                                 }
                               }];
      ```

* **targetCreateOrder&#x200B;ConfirmRequestWithName:&#x200B;orderId:&#x200B;orderTotal:&#x200B;productPurchasedId:&#x200B;parameters**

   를 만듭니다 `ADBTargetLocationRequest`.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateOrderConfirmRequestWithName:(NSString *)name
                                      orderId:(NSString *)orderId
                                  orderTotal:(NSString *)orderTotal
                          productPurchasedId:(NSString *)productPurchasedId
                              parameters:(NSDictionary *)parameters;
      ```

* **targetCreateRequestWithName:&#x200B;&#x200B;defaultContent:&#x200B;parameters**

   주어진 매개 변수로 ADBTargetLocationRequest 개체를 만드는 편의 생성자입니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateRequestWithName:(NSString *)name
                           defaultContent:(NSString *)defaultContent
                               parameters:(NSDictionary *)parameters;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      ADBTargetLocationRequest *myRequest =  
      [ADBMobile targetCreateRequestWithName:@"heroBanner"
                              defaultContent:@"default.png"
                                  parameters:nil];
      ```

* **targetThirdPartyID**

   타사 ID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (nullable NSString *) targetThirdPartyID;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSString *thirdPartyId = [ADBMobile targetThirdPartyID];
      ```

* **targetSetThirdPartyID**

   타사 ID를 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) targetSetThirdPartyID:(nullable NSString *)thirdPartyID;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile targetSetThirdPartyID:@"thirdPartyID"];
      ```

* **targetClearCookies**

   앱에서 모든 타겟 쿠키를 지웁니다.

   >[!TIP]
   >
   >SDK의 버전 4.10.0 이후, Target는 더 이상 쿠키를 사용하지 않습니다. 이 메서드는 thirdPartyID 및 sessionID를 재설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) targetClearCookies;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile targetClearCookies];
      ```

* **targetPcID**

   PcID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSString *myTargetPcID = [ADBMobile targetPcID];
      ```

* **targetSessionID**

   SessionID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSString *myTargetSessionID = [ADBMobile targetSessionID];
      ```

### 예

```objective-c
// make your request 
ADBTargetLocationRequest *myRequest =  
 [ADBMobile targetCreateRequestWithName:@"heroBanner"  
                         defaultContent:@"default.png"  
                          parameters:nil]; 
// load your request 
[ADBMobile targetLoadRequest:myRequest  
                    callback:^(NSString *content) { 
                        // do something with content 
                        heroImage.image = [UIImage imageNamed:content];
                    }];
```
