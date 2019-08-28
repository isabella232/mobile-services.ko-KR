---
description: Universal Windows Platform 라이브러리에서 제공하는 타겟 목록 메서드입니다.
seo-description: Universal Windows Platform 라이브러리에서 제공하는 타겟 목록 메서드입니다.
seo-title: 타겟 메서드
solution: Marketing Cloud, Analytics
title: 타겟 메서드
topic: 개발자 및 구현
uuid: 2 AD 5953 B -7850-446 A -8053-B 3715 B 86329 B
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Target methods {#target-methods}

Universal Windows Platform 라이브러리에서 제공하는 타겟 목록 메서드입니다.

현재 SDK는 Analytics, Target 및 Audience Manager을 포함하여 여러 Adobe Experience Cloud 솔루션을 지원합니다.

[라이프사이클 지표는](/help/universal-windows/metrics.md) 각 mbox 로드에 매개 변수로 전송됩니다.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

## 클래스 참조: TargetLocationRequest

## 속성

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## 문자열 상수

이 정보는 사용자 지정 매개 변수에 대한 키를 설정하는 데 도움이 됩니다.

```
static property Platform::String ^TARGET_PARAMETER_ORDER_ID { 
  Platform::String ^get() { return L"orderId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_ORDER_TOTAL { 
  Platform::String ^get() { return L"orderTotal"; } 
} 
static property Platform::String ^TARGET_PARAMETER_PRODUCT_PURCHASE_ID { 
  Platform::String ^get() { return L"productPurchasedId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_CATEGORY_ID { 
  Platform::String ^get() { return L"categoryId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_3RDPARTY_ID { 
  Platform::String ^get() { return L"mbox3rdPartyId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PAGE_VALUE { 
  Platform::String ^get() { return L"mboxPageValue"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PC { 
  Platform::String ^get() { return L"mboxPC"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_SESSION_ID { 
  Platform::String ^get() { return L"mboxSession"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_HOST { 
  Platform::String ^get() { return L"mboxHost"; } 
}
```

* **Loadrequest (winjs: Loadrequest)**

   Sends `request` to your configured Target server and returns the string value of the offer generated in a block `callback`.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var fADB = ADBMobile; 
       ADB.Target.loadRequest(heroBannerRequest).then(function(content){ 
          //do something with content returned from target server 
       });
      ```

* **Createrequest (winjs: Createrequest)**

   지정된 매개 변수로 `TargetLocationRequest` 개체를 만듭니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile;
      var heroBannerRequest = ADB.Target.createRequest("heroBanner","default.png", null); 
      ```

* **Createorderconfirmrequest (winjs: Createorderconfirmrequest)**

   지정된 매개 변수로 `TargetLocationRequest` 개체를 만듭니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId,Platform::String ^orderTotal,Platform::String ^productPurchasedId,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      varADB = ADBMobile;
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm","order","47.88","3722",null);
      ```

* **Clearcookies (winjs: Clearcookies)**

   현재 장치에서 애플리케이션의 Target 쿠키를 지웁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void ClearCookies();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **Getpcid (winjs: Getpcid)**

   현재 장치의 PC ID 쿠키를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      staticPlatform::String ^GetPcId();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      autopcId = ADBMobile.Target.getPcId();
      ```

* **Getsessionid (winjs: Getsessionid)**

   현재 장치의 세션 ID 쿠키를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      staticPlatform::String ^GetSessionId();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
       autosessionId=ADBMobile.Target.getSessionId(); 
      ```

