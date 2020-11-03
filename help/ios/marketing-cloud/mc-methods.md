---
description: 다음은 iOS 라이브러리에서 제공하는 Adobe Experience Platform ID 서비스 메서드입니다.
seo-description: 다음은 iOS 라이브러리에서 제공하는 Adobe Experience Platform ID 서비스 메서드입니다.
seo-title: Adobe Experience Platform ID 서비스 메서드
solution: Experience Cloud,Analytics
title: Adobe Experience Platform ID 서비스 메서드
topic: Developer and implementation
uuid: cdd307bc-8b7d-47a8-b77e-00902b9e2968
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '461'
ht-degree: 100%

---


# Adobe Experience Platform ID 서비스 메서드 {#experience-cloud-id-service-methods}

다음은 iOS 라이브러리에서 제공하는 Adobe Experience Platform ID 서비스 메서드입니다.

현재 SDK는 Analytics, Target, Audience Manager, Experience Cloud 방문자 ID 서비스 등 여러 Adobe Experience Cloud 솔루션을 지원합니다.

메서드에는 솔루션에 따라 접두사가 추가되며, Experience Cloud ID 메서드의 경우 `visitor` 접두사가 추가됩니다. 자세한 내용은 [Experience Cloud ID 사용](/help/ios/marketing-cloud/mcvid.md)을 참조하십시오.

* **`+`(nullable NSURL `*`)visitorAppendToURL:(nullable NSURL `*`)url;**

   Adobe JavaScript 라이브러리에서 사용할 수 있도록 URL 문자열에 Adobe 방문자 데이터를 추가합니다. 이 메서드를 사용하려면 Mobile SDK 버전 4.12 이상이 있어야 합니다. 자세한 내용은 [방문자 ID 지원 기능 추가](https://docs.adobe.com/content/help/ko-KR/id-service/using/id-service-api/methods/appendvisitorid.html)를 참조하십시오.

   >[!IMPORTANT]
   >
   >이 메서드로 인해 네트워크 호출이 차단될 수 있습니다. 시간이 중요한 스레드에 대해서는 호출하지 마십시오.

   * 입력: `URL<NSURL>`방문자 정보를 추가할 필수 URL 문자열입니다.
   * `URL<NSURL>`
방문자 정보가 추가된 문자열입니다.

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
       NSURL *url = [NSURL URLWithString:@"https://www.example.com"];  
       NSURL *decoratedURL = [ADBMobile visitorAppendToURL: url];  
       [[UIApplication sharedApplication] openURL: decoratedURL];  
      ```

* **visitorMarketingCloudID**

   ID 서비스에서 Experience Cloud ID를 검색합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (NSString  *)  visitorMarketingCloudID;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSString *mcid = [ADBMobile visitorMarketingCloudID]; 
      ```

      >[!IMPORTANT]
      >
      >이 메서드로 인해 네트워크 호출이 차단될 수 있으므로 UI 스레드에서 호출해서는 **안 됩니다**.

* **visitorSyncIdentifiers:**

   Experience Cloud ID를 사용하면 각 방문자와 연결할 수 있는 추가 고객 ID를 설정할 수 있습니다. 방문자 API는 여러 다른 고객 ID의 범위를 구분하기 위해 동일한 방문자의 여러 고객 ID와 고객 유형 식별자를 수락합니다. 이 메서드는 JavaScript 라이브러리의 `setCustomerIDs`에 해당합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      +  (void)  visitorSyncIdentifiers:(NSDictionary  *)identifiers;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"idType":@"idValue"}];
      ```

* **visitorSyncIdentifiers:authenticationState:**

   제공된 식별자를 ID 서비스에 동기화합니다. 다음 값 중 하나로 `authState`에 전달하십시오.

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      +  (void) visitorSyncIdentifiers:(nullable NSDictionary  *)identifiers  authenticationState:(ADBMobileVisitorAuthenticationState)authState; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"myIdType":@"valueForUser"}  authenticationState:ADBMobileVisitorAuthenticationStateAuthenticated]; 
      ```

* **visitorSyncIdentifierWithType:identifier:authenticationState:**

   제공된 식별자 유형 및 값을 ID 서비스에 동기화합니다. 다음 값 중 하나로 `authState`에 전달하십시오.

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) visitorSyncIdentifierWithType:(nullable NSString *)identifierType  
      identifier:(nullable NSString *)identifier authenticationState:
      (ADBMobileVisitorAuthenticationState)authState; 
      ```

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      [ADBMobile visitorSyncIdentifierWithType:@"myIdType" identifier:@"valueForUser"  
      authenticationState:ADBMobileVisitorAuthenticationStateLoggedOut]; 
      ```

* **visitorGetIDs**

   읽기 전용 `ADBVisitorID` 개체 배열을 검색합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      +  (nullable NSArray *) visitorGetIDs;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSArray *myVisitorIDs = [ADBMobile visitorGetIDs];
      ```

* **visitorgetUrlVariablesAsync**

   버전 4.16.0에서 도입된 이 메서드는 방문자 ID 서비스 URL 변수를 포함하는 적절한 형식의 문자열을 반환합니다. 이 메서드를 사용하는 방법에 대한 자세한 내용은 [Adobe Experience Platform ID 서비스 메서드](/help/ios/reference/hybrid-app.md)를 참조하십시오.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objectivec
      + (void) visitorGetUrlVariablesAsync:(nullable void (^)(NSString* __nullable urlVariables))callback;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objectivec
      NSString *urlString = @"https://www.mydomain.com/index.php"; 
      [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
        NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
        // use urlStringWithVisitorData 
      }];
      ```

## ADBVisitorID 인터페이스 {#section_2FF74454D25C4ADABAC5E43CBFAAEC26}

**공용 메서드:**

```objective-c
- (nullable NSString *) idType; 
- (nullable NSString *) identifier; 
- (ADBMobileVisitorAuthenticationState) authenticationState; 
```

## ADBMobileVisitorAuthenticationState enum {#section_A55A3F336DDF4F838900632087F51430}

```objective-c
ADBMobileVisitorAuthenticationStateUnknown, 
ADBMobileVisitorAuthenticationStateAuthenticated, 
ADBMobileVisitorAuthenticationStateLoggedOut
```

