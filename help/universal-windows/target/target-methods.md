---
description: 유니버설 Windows 플랫폼 라이브러리에서 제공하는 Target 메서드 목록입니다.
solution: Experience Cloud,Analytics
title: Target 메서드
topic-fix: Developer and implementation
uuid: 2ad5953b-7850-446a-8053-b3715b86329b
exl-id: d7aeee41-1c34-4f98-8455-e9f429287cfc
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 37%

---

# Target 메서드 {#target-methods}

유니버설 Windows 플랫폼 라이브러리에서 제공하는 Target 메서드 목록입니다.

현재 SDK는 Analytics, Target 및 Audience Manager 등 여러 Adobe Experience Cloud 솔루션을 지원합니다.

[라이프사이클 ](/help/universal-windows/metrics.md) 지표는 각 mbox 로드에 매개 변수로 전송됩니다.

>[!TIP]
>
>winJS(JavaScript)에서 `winmd` 메서드를 사용하면 모든 메서드가 자동으로 첫 번째 문자를 소문자로 바꿉니다.

## 클래스 참조: TargetLocationRequest

## 속성

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## 문자열 상수

다음은 사용자 지정 매개 변수에 대한 키를 설정하는 데 유용한 정보입니다.

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

* **LoadRequest(winJS: loadRequest)**

   구성된 Target 서버에 `request`을(를) 보내고 블록 `callback`에서 생성된 오퍼의 문자열 값을 반환합니다.

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

* **CreateRequest (winJS: createRequest)**

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

* **주문 &#x200B; 확인 요청(winJS: createOrder &#x200B; ConfirmRequest)**

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

* **ClearCookies(winJS: clearCookies)**

   현재 장치에서 응용 프로그램에 대한 Target 쿠키를 지웁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      static void ClearCookies();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **GetPcId(winJS: getPcId)**

   현재 장치에 대한 PC ID 쿠키를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      staticPlatform::String ^GetPcId();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
      autopcId = ADBMobile.Target.getPcId();
      ```

* **GetSessionId(winJS: getSessionId)**

   현재 장치에 대한 세션 ID 쿠키를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```csharp
      staticPlatform::String ^GetSessionId();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```js
       autosessionId=ADBMobile.Target.getSessionId(); 
      ```
