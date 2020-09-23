---
description: Windows 8.1 Universal App Store 라이브러리에서 제공하는 Target 메서드 목록입니다.
seo-description: Windows 8.1 Universal App Store 라이브러리에서 제공하는 Target 메서드 목록입니다.
seo-title: Target 메서드
solution: Experience Cloud,Analytics
title: Target 메서드
topic: Developer and implementation
uuid: 8c35b31c-c70b-4dba-8759-173342a301e9
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 42%

---


# 타겟 메서드 {#target-methods}

Windows 8.1 Universal App Store 라이브러리에서 제공하는 Target 메서드 목록입니다.

SDK는 현재 분석, Target 및 Audience Manager을 비롯한 여러 Adobe Experience Cloud 솔루션을 지원합니다. 메서드에는 솔루션에 따라 접두사가 붙습니다. 분석 메서드 접두사는 &quot;Target&quot;입니다.

[라이프사이클 지표](/help/windows-appstore/metrics.md)는 각 mbox 로드에 매개 변수로 전송됩니다.

>[!TIP]
>
>winJS(JavaScript)의 `winmd` 메서드를 사용하면 모든 메서드에서 첫 번째 문자가 자동으로 소문자로 바뀝니다.

## 클래스 참조: TargetLocationRequest

### 속성

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## 문자열 상수

이 정보는 사용자 지정 매개 변수의 키를 설정하는 데 도움이 됩니다.

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

* **LoadRequest(winJS:loadRequest)**

   Sends `request` to your configured Target server and returns the string value of the offer generated in a block `callback`.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile; 
      ADB.Target.loadRequest(heroBannerRequest).then(function(content) { 
      // do something with content returned from target server 
      });
      ```

* **CreateRequest(winJS:createRequest)**

   Creates a `TargetLocationRequest` object with the given parameters.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile; 
      var heroBannerRequest = ADB.Target.createRequest("heroBanner", "default.png", null); 
      ```

* **CreateOrder &#x200B; ConfirmRequest(winJS:createOrder &#x200B; ConfirmRequest)**

   Creates a `TargetLocationRequest` object with the given parameters.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId, Platform::String ^orderTotal, Platform::String ^productPurchasedId, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^parameters); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      var ADB = ADBMobile; 
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null); 
      ```

* **ClearCookies(winJS:clearCookies)**

   현재 장치에서 응용 프로그램의 Target 쿠키를 지웁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void ClearCookies(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **GetPcId(winJS:getPcId)**

   현재 장치에 대한 PC ID 쿠키를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static Platform::String ^GetPcId();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      auto pcId = ADBMobile.Target.getPcId(); 
      ```

* **GetSessionId(winJS:getSessionId)**

   현재 장치에 대한 세션 ID 쿠키를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static Platform::String ^GetSessionId(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      auto sessionId = ADBMobile.Target.getSessionId(); 
      ```

