---
description: 다음은 Android 라이브러리에서 제공하는 Adobe Target 메서드 목록입니다.
keywords: android;library;mobile;sdk
seo-description: 다음은 Android 라이브러리에서 제공하는 Adobe Target 메서드 목록입니다.
seo-title: Android용 Target 메서드
solution: Experience Cloud,Analytics
title: Android용 Target 메서드
topic: Developer and implementation
uuid: 8e9808b2-ba80-4646-ba05-8e62d4fde065
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '603'
ht-degree: 100%

---


# Android용 Target 메서드{#target-methods}

다음은 Android 라이브러리에서 제공하는 Adobe Target 메서드 목록입니다.

현재 SDK는 Analytics, Target, Audience Manager 및 Adobe Experience Platform ID 서비스 등 여러 Adobe Experience Cloud 솔루션을 지원합니다. 메서드에는 솔루션에 따라 접두사가 추가됩니다. 예를 들면 Experience Cloud ID 메서드에는 `target` 접두사가 추가됩니다.

>[!TIP]
>
>[라이프사이클 지표](/help/android/metrics.md)는 각 mbox 로드에 매개 변수로 전송됩니다.

## 클래스 참조: TargetLocationRequest {#section_A8CC898922164E819EC730DC92A6742B}

**속성:**

```java
public String name; 
public String defaultContent; 
public HashMap<String, Object> parameters;
```

**문자열 상수**

>[!TIP]
>
>다음 상수는 사용자 지정 매개 변수에 대한 키를 설정할 때 쉽게 사용됩니다.

```java
public static final String TARGET_PARAMETER_ORDER_ID   = "orderId"; 
public static final String TARGET_PARAMETER_ORDER_TOTAL         = "orderTotal"; 
public static final String TARGET_PARAMETER_PRODUCT_PURCHASE_ID = "productPurchasedId"; 
public static final String TARGET_PARAMETER_CATEGORY_ID         = "categoryId"; 
public static final String TARGET_PARAMETER_MBOX_3RDPARTY_ID    = "mbox3rdPartyId"; 
public static final String TARGET_PARAMETER_MBOX_PAGE_VALUE     = "mboxPageValue"; 
public static final String TARGET_PARAMETER_MBOX_PC             = "mboxPC"; // pcId in cookie 
public static final String TARGET_PARAMETER_MBOX_SESSION_ID     = "mboxSession"; // sessionId in cookie 
public static final String TARGET_PARAMETER_MBOX_HOST           = "mboxHost";
```

>[!IMPORTANT]
>
>* 4.14.0 **이전** 버전의 SDK를 사용하는 경우 [https://developers.adobetarget.com/api/#input-parameters](https://developers.adobetarget.com/api/#input-parameters)에서 매개 변수 제한 사항을 참조하십시오.
   >
   >
* 4.14.0 **이후** 버전의 SDK를 사용하는 경우 [](https://developers.adobetarget.com/api/#batch-input-parameters)https://developers.adobetarget.com/api/#batch-input-parameters에서 매개 변수 제한 사항을 참조하십시오.


* **loadRequest**

   구성된 Target 서버에 request를 보내고 차단 callback에서 생성된 오퍼의 문자열 값을 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void loadRequest(TargetLocationRequest request, TargetCallback<String> callback);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Target.loadRequest(heroBannerRequest, new Target.TargetCallback<String>() {  @Override  public void call(String item) {   // do something with item  } });
      ```

* **loadRequest**

   구성된 Target 서버에 request를 보내고 차단 callback에서 생성된 오퍼의 문자열 값을 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void loadRequest(final String name final String defaultContent, final Map `<String, Object>` profileParameters, 
                                     final Map `<String, Object>` orderParameters,final Map `<String Object>` mboxParameters, final TargetCallback<String> callback)
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”);
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); 
      mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters
      new TargetCallback<String>() {
          @Override
          public void call (String item) {
             Log.d(“Target Content”, item); 
          }
      });
      ```

* **loadRequest**

   구성된 Target서버에 요청을 보내고 TargetCallback에서 생성된 오퍼의 문자열 값을 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void loadRequest(final String name, final String defaultContent, final Map<String, Object> profileParameters, final Map<String, Object> orderParameters, final Map<String, Object> mboxParameters, final Map<String, Object> requestLocationParameters, final TargetCallback<String> callback);
      ```

   * **반환:** 해당 없음

   * **매개 변수:**

      다음은 이 메서드에 대한 매개 변수입니다.

      * **이름**

         검색할 Target mbox/위치의 이름입니다.

         * **유형:** 문자열
      * **defaultContent**

         Target 서버에 도달할 수 없거나 사용자가 캠페인에 적합하지 않은 경우 콜백에서 반환되는 값입니다.

         * **유형:** 문자열
      * **profileParameters**

         이 사전의 값은 Target에 전송되는 요청의 &quot;profileParameters&quot; 개체에 삽입합니다.

         * **유형**: 맵 `<String, Object>`
      * **orderParameters**

         이 사전의 값은 Target에 전송되는 요청의 &quot;order&quot; 개체에 삽입합니다.

         * **유형**: 맵 `<String, Object>`
      * **mboxParameters**

         이 사전의 값은 Target에 전송되는 요청에 삽입됩니다.

         * **유형**: 맵 `<String, Object>`
      * **requestLocationParameters**

         이 사전의 값은 Target에 전송되는 요청의 &quot;requestLocation&quot; 개체에 삽입됩니다.

         * **유형**: 맵 `<String, Object>`
      * **callback**

         이 메서드는 Target 서버의 오퍼 콘텐츠를 사용하여 호출됩니다. Target 서버에 연결할 수 없거나 사용자가 캠페인에 적합하지 않으면 defaultContent가 반환됩니다.

         * **유형:** TargetCallback `<String>`
   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”); 
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Map `<String, Object>` requestLocationParameters = new HashMap `<String, Object>`(); requestLocationParameters.put(“request-location-parameter-key”, “request-location-parameter-value”); 
      
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters, requestLocationParameters,new TargetCallback<String>() {
         @Override
         public void call (String item) { 
            Log.d(“Target Content”, item);
         } 
      });
      ```

      기본 Target API에 대한 자세한 내용은 Target 개발자 도움말에서 [제공](https://docs.adobe.com/dev/products/target/reference/delivery.html)을 참조하십시오.








* **createOrderConfirmRequest**

   지정된 매개 변수로 TargetLocationRequest 개체를 만듭니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static TargetLocationRequest createOrderConfirmRequest(String name, String orderId, String orderTotal, String productPurchasedId, Map<String, Object> parameters);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      TargetLocationRequest orderConfirm = Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null);
      ```

* **createRequest**

   지정된 매개 변수로 TargetLocationRequest 개체를 만듭니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static TargetLocationRequest createRequest(String name, String defaultContent, Map<String, Object> parameters);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      TargetLocationRequest heroBannerRequest = Target.createRequest("heroBanner", "default.png", null);
      ```

* **clearCookies**

   앱에서 모든 타겟 쿠키를 지웁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void clearCookies();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Target.clearCookies();
      ```

* **getPcID**

   pcID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static String getPcID();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Target.getPcID();
      ```

* **getSessionID**

   세션 ID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static String getSessionID();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Target.getSessionID();
      ```

* **setThirdPartyID**

   타사 ID를 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static String setThirdPartyID(final String thirdPartyId);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Target.setThirdPartyID(“third-party-id”);
      ```

* **getThirdPartyID**

   타사 ID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static String getThirdPartyID();
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      String thirdPartyId = Target.getThirdPartyID();
      ```
