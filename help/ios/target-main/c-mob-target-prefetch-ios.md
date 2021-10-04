---
description: Adobe Target 미리 가져오기 기능은 iOS Mobile SDK를 사용하여 서버 응답을 캐시하여 가능한 한 적은 시간에 오퍼 콘텐츠를 가져옵니다.
title: iOS에서 오퍼 콘텐츠 미리 가져오기
uuid: fef58042-65e2-4579-b8f1-d21554d2af57
exl-id: 64d43be7-6bd1-4657-8154-5b2c1cbbf42b
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 85%

---

# iOS에서 오퍼 콘텐츠 미리 가져오기 {#prefetch-offer-content-in-ios}

Adobe Target 미리 가져오기 기능은 iOS Mobile SDK를 사용하여 서버 응답을 캐시하여 가능한 한 적은 시간에 오퍼 컨텐츠를 가져옵니다.

>[!IMPORTANT]
>
>iOS용 Mobile SDK의 미리 가져오기 기능은 Adobe Target의 Auto Target, Auto Allocate 및 Automated Personalization 활동 유형에서 지원되지 않습니다.

이 프로세스는 로드 시간을 줄이고, 다중 네트워크 호출을 방지하며, 모바일 앱 사용자가 방문한 mbox를 Adobe Target에 알려줄 수 있도록 해줍니다. 모든 콘텐츠는 미리 가져오기 호출 중에 검색되고 캐시되며, 이 콘텐츠는 지정된 mbox 이름에 대해 캐시된 콘텐츠를 포함하는 이후의 모든 호출에 대한 캐시에서 검색됩니다.

미리 가져오기 콘텐츠는 실행 간에는 지속되지 않으며, 애플리케이션이 상주하는 한 또는 `clearPrefetchCache()` 메서드가 호출될 때까지 캐시됩니다.

>[!IMPORTANT]
>
>Target 미리 가져오기 API는 SDK 4.14.0 이후 버전에서 사용할 수 있게 되었습니다. 매개 변수 제한 사항에 대한 자세한 내용은 [배치 입력 매개 변수](https://developers.adobetarget.com/api/#batch-input-parameters)를 참조하십시오.

SDK 버전 4.14 이상에서는 지정되는 경우 v2 batch mbox TnT 호출을 시작할 때 파일에서`environmentId``ADBMobileConfig.json`가 선택됩니다. 이 파일에 `environmentId` 가 지정되지 않은 경우, TNT batch mbox 호출에서 환경 매개 변수가 전송되지 않고 기본 환경에 대한 오퍼가 전달됩니다.

예:

```
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## 미리 가져오기 메서드 {#section_05967F1F3A554B0FBC2C08A954554BDE}

iOS에서 미리 가져오기에 사용할 수 있는 메서드는 다음과 같습니다.

* **targetPrefetchContent**

   구성된 Target 서버에 다수의 위치를 사용하는 미리 가져오기 요청을 전송하고 제공된 콜백에서 요청 상태를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      (void) targetPrefetchContent:(nonnull NSArray*)targetPrefetchObjectArray 
                     withProfileParameters:(nullable NSDictionary*)profileParameters 
                            callback:(nullable void(^)(BOOL success))callback;
      ```

   * 다음은 이 메서드에 대한 매개 변수입니다.

      * **`targetPrefetchArray`**

         미리 가져올 각 Target 위치에 대한 이름 및 mboxParameters를 포함하는 `TargetPrefetchObjects` 배열입니다.

      * **`profileParameters`**

         이 요청의 모든 위치 미리 가져오기에 사용할 프로필 매개 변수의 키 및 값을 포함합니다.

      * **`callback`**

         미리 가져오기가 완료되면 호출됩니다. 미리 가져오기가 성공하면 `true`를 반환하고, 실패하면 `false`를 반환합니다.

* **targetLoadRequests**

   요청 배열에 지정된 여러 mbox 위치에 대한 배치 요청을 실행합니다. 배열에 있는 각 개체는 제공된 mbox 위치에 컨텐츠를 사용할 수 있을 때 호출되는 콜백 함수를 포함합니다.

   >[!IMPORTANT]
   >
   >요청한 위치의 콘텐츠가 이미 캐시된 경우 제공된 콜백에서 즉시 반환됩니다. 그렇지 않으면 Target 서버에 컨텐츠를 검색하도록 SDK가 네트워크 요청을 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      (void)targetLoadRequests:(nonnullNSArray*)requests 
               withProfileParameters:(nullableNSDictionary*)profileParameters;
      ```

   * 다음은 이 메서드에 대한 매개 변수입니다.

      * **`requests`**

         검색할 위치에 대한 이름, 기본 컨텐츠, 매개 변수 및 콜백 함수를 포함하는 `TargetRequestObjects` 배열입니다.

      * **`profileParameters`**

         이 요청의 모든 위치 미리 가져오기에 사용할 프로필 매개 변수의 키 및 값을 포함합니다.

* **targetPrefetchClearCache**

   Target 미리 가져오기에 의해 캐시된 데이터를 지웁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      (void) targetPrefetchClearCache; 
      ```

   * 이 메서드에 대한 매개 변수가 없습니다.

* **targetRequestObjectWithName**

   제공된 데이터로 `TargetRequestObject` 인스턴스를 생성 및 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      +(nullableADBTargetRequestObject*)targetRequestObjectWithName:(nonnullNSString*)name
      defaultContent:(nonnullNSString*)defaultContent
      mboxParameters:(nullableNSDictionary*)mboxParameters
      callback:(nullablevoid(^)(NSString*__nullablecontent))callback;
      ```

   * 이 메서드에 대한 매개 변수가 없습니다.

* **createTargetPrefetchObject**

   제공된 데이터로 `TargetPrefetchObject` 인스턴스를 생성 및 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      +(nullable ADBTargetPrefetchObject *) targetPrefetchObjectWithName:(nonnullNSString *)name
      mboxParameters:(nullableNSDictionary *)mboxParameters;
      ```

## 공용 클래스 {#section_A273E53F069E4327BBC8CE4910B37888}

다음은 iOS에서 미리 가져오기를 지원하는 공용 클래스입니다.

### 클래스 참조: TargetPreFetchObject

mbox 미리 가져오기에 사용되는 mbox 이름 및 매개 변수를 캡슐화합니다.

* **`name`**

   검색할 위치/mbox의 이름입니다.

   * **유형**: NSString*

* **`mboxParameters`**

   mbox 매개 변수의 키-값 쌍을 포함하는 선택적 사전입니다.

   * **유형**: NSDictionary*

* **`orderParameters`**

   순서 매개 변수의 키-값 쌍을 포함하는 사전입니다.

   * **유형**: NSDictionary*

* **`productParameters`**

   제품 매개 변수의 키-값 쌍을 포함하는 사전입니다.

   * **유형**: NSDictionary*

### 클래스 참조: TargetRequestObject

이 클래스는 Target 위치 요청에 사용되는 mbox 이름, 기본 컨텐츠, mbox 매개 변수 및 반환 콜백을 캡슐화합니다.

* **`name`**

   요청된 위치의 이름입니다.

   * **유형**: NSString*

* **`mboxParameters`**

   검색할 위치/mbox의 이름을 나타내는 NSString 값입니다.

   * **유형**: NSString*

* **`defaultContent`**

   Target 서버에 연결할 수 없는 경우 반환되는 기본 컨텐츠입니다.

   * **유형**: NSString*

* **`callback`**

   배치(일괄 처리)에서 Target 위치를 요청할 때 이 위치에 대한 컨텐츠가 있으면 콜백이 호출됩니다.

   * **유형**: Function

## 코드 샘플 {#section_BF7F49763D254371B4656E17953D520C}

다음은 iOS SDK를 사용하여 컨텐츠를 미리 가져오는 방법의 예입니다.

```objective-c
/** 
 * Prefetch Content 
 */ 
  
    NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
    NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
    NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
  
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    // Creating Prefetch Objects 
    ADBTargetPrefetchObject *prefetch1 = [ADBMobile targetPrefetchObjectWithName:@"logo" mboxParameters:mboxParameters1]; 
    prefetch1.productParameters = productParameters1; 
    prefetch1.orderParameters = orderParameters1; 
  
    ADBTargetPrefetchObject *prefetch2 = [ADBMobile targetPrefetchObjectWithName:@"buttonColor" mboxParameters:mboxParameters2]; 
    prefetch2.productParameters = productParameters2; 
    prefetch2.orderParameters = orderParameters2; 

    // Creating prefetch Array 
    NSArray *prefetchArray = @[prefetch1,prefetch2]; 
  
    // Creating Profile parameters 
    NSDictionary *profileParmeters = @{@"age":@"20-32"};

    // Target API Call 
    [ADBMobile targetPrefetchContent:prefetchArray withProfileParameters:profileParmeters callback:^(BOOL isSuccess){ 
       // do something with the Boolean result 
    }];
```

다음은 iOS SDK를 사용한 `loadRequest` 일괄 처리의 예입니다.

```objective-c
/** 
 * Batch loadRequest  
 */ 
  
   NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
   NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
   NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    ADBTargetRequestObject *request1 = [ADBMobile targetRequestObjectWithName:@"logo" defaultContent:@"BlueWhale" mboxParameters:mboxParameters1 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
  
    request1.productParameters = productParameters1; 
    request1.orderParameters = orderParameters1;

    ADBTargetRequestObject *request2 = [ADBMobile targetRequestObjectWithName:@"buttonColor" defaultContent:@"red" mboxParameters:mboxParameters2 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
    request2.productParameters = productParameters1; 
    request2.orderParameters = orderParameters1;

    // create request object array 
    NSArray *requestArray = @[request1,request2]; 
  
    // Call the API 
    [ADBMobile targetLoadRequests:requestArray withProfileParameters:profileParmeters];
```

## 추가 정보 {#section_A454BAD1CD49423E86C71BAEE06125FD}

다음은 이러한 샘플에 대한 추가 정보입니다.

* `ProductParameters`는 다음 키만 허용합니다.

   * `id`
   * `categoryId`

* `OrderParameters`는 다음 키만 허용합니다.

   * `id`
   * `total`
   * `purchasedProductIds`

* `purchasedProducts`는 다수의 문자열을 허용합니다.
