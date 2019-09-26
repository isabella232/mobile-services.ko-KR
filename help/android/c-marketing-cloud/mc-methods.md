---
description: 다음은 Android 라이브러리에서 제공하는 Experience Cloud ID 메서드입니다.
keywords: android;library;mobile;sdk
seo-description: 다음은 Android 라이브러리에서 제공하는 Experience Cloud ID 메서드입니다.
seo-title: Adobe Experience Platform ID 서비스 메서드
solution: Marketing Cloud,Analytics
title: Adobe Experience Platform ID 서비스 메서드
topic: 개발자 및 구현
uuid: c5107a7e-273b-4f71-8738-4c603479b24c
translation-type: tm+mt
source-git-commit: 8fc515a6e89044b9dac98b3f207c5f43b658a2ec

---


# Adobe Experience Platform ID 서비스 메서드{#experience-cloud-id-service-methods}

다음은 Android 라이브러리에서 제공하는 Experience Cloud ID 메서드입니다.

The SDK currently supports multiple Adobe Experience Cloud Solutions], including Analytics, Target, Audience Manager, and the Adobe Experience Platform Identity Service.

Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `visitor`. For more information, see [Experience Cloud ID Configuration](/help/android/c-marketing-cloud/mcvid.md).

* **public static String appendToURL(최종 문자열 URL)**

   Adobe JavaScript 라이브러리에서 사용할 수 있도록 URL 문자열에 Adobe 방문자 데이터를 추가합니다. 이 메서드를 사용하려면 Mobile SDK 4.12 이상이 있어야 합니다. 자세한 내용은 [방문자 ID 지원 기능 추가](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-appendvisitorid.html)를 참조하십시오.

   >[!IMPORTANT]
   >
   >This method can cause a blocking network call. 시간이 중요한 스레드에 대해서는 호출하지 마십시오.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static String appendToURL(final String URL) 
      ```

      방문자 정보가 추가되는 필수 URL 문자열입니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      String urlSample = "https://example.com";`
              String urlWithAdobeVisitorInfo = Visitor.appendToURL(urlSample);
      
              Intent(Intent.ACTION_VIEW);
              i.setData(Uri.parse(urlWithAdobeVisitorInfo));
              startActivity(i);
      ```

* **getMarketingCloudId**

   방문자 ID 서비스에서 Experience Cloud ID를 검색합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static String getMarketingCloudId(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      String = Visitor.getMarketingCloudId();
      ```

      >[!IMPORTANT]
      >
      >This method can cause a blocking network call and should **not** be called from a UI thread.

* **syncIdentifiers**

   Experience Cloud ID를 사용하면 각 방문자와 연결할 수 있는 추가 고객 ID를 설정할 수 있습니다. 방문자 API는 여러 다른 고객 ID의 범위를 구분하기 위해 동일한 방문자의 여러 고객 ID와 고객 유형 식별자를 수락합니다. 이 메서드는 JavaScript 라이브러리의 `setCustomerIDs`에 해당합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void syncIdentifiers(Map<String, String> identifiers); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Map<String,String> identifiers = new HashMap<String, String>();
      identifiers.put("idType", "idValue");
      Visitor.syncIdentifiers(identifiers);
      ```

* **syncIdentifier**

   제공된 식별자 유형 및 값을 방문자 ID 서비스에 동기화합니다.

   다음 값 중 하나로 `authenticationState`에 전달하십시오.

   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void syncIdentifier(final String identifierType, final String identifier, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Visitor.syncIdentifier("myIdType", "valueForUser", VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT);
      ```

* **syncIdentifiers**

   제공된 식별자를 ID 서비스에 동기화합니다.

   다음 값 중 하나로 `authenticationState`에 전달하십시오.
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void syncIdentifiers(final Map<String String> identifiers, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Map<String, String> identifiers = new HashMap<String, String>();
          identifiers.put("myIdType", "valueForUser"); Visitor.syncIdentifiers(identifiers,
      VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED); 
      ```

* **getIdentifiers**

   읽기 전용 `ADBVisitorID` 개체 목록을 검색합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static List<VisitorID> getIdentifiers(); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      List<VisitorID> myVisitorIDs = Visitor.getIdentifiers(); 
      ```

* **getUrlVariablesAsync**

   버전 4.16.0에서 도입된 이 메서드는 방문자 ID 서비스 URL 변수를 포함하는 적절한 형식의 문자열을 반환합니다. 이 방법을 사용하는 방법에 대한 자세한 내용은 Adobe Experience [Platform ID 서비스 메서드를](/help/android/reference/hybrid-app.md)참조하십시오.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void getUrlVariablesAsync(final VisitorCallback callback);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      final String urlString = https://www.mydomain.com/index.php; 
      Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
        @Override 
        public void call(String urlVariables) { 
            final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
            ...
        } 
      });
      ```

## Public methods {#section_8AC744B431A3438C9B45629CA3EA0F51}

```java
public class VisitorID { 
    public final String idOrigin; 
    public final String idType; 
    public final String id; 
    public VisitorIDAuthenticationState authenticationState; 
 
    public enum VisitorIDAuthenticationState { 
         VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN(0), 
         VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED(1), 
         VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT(2); 
    } 
}
```
