---
description: 모바일 웹 콘텐츠를 여는 앱의 경우, 방문자가 기본 웹과 모바일 웹 사이를 이동할 때 개별적으로 식별되지 않도록 합니다.
seo-description: 모바일 웹 콘텐츠를 여는 앱의 경우, 방문자가 기본 웹과 모바일 웹 사이를 이동할 때 개별적으로 식별되지 않도록 합니다.
seo-title: 앱과 모바일 웹 간 방문자 추적
solution: Marketing Cloud, Analytics
title: 앱과 모바일 웹 간 방문자 추적
topic: 개발자 및 구현
uuid: 073572 e 4-4 c 55-4 b 27-b 4 a 7-e 4349 ccde 7 bf
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Visitor tracking between an app and the mobile web {#visitor-tracking-between-an-app-and-mobile-web}

모바일 웹 콘텐츠를 여는 앱의 경우, 방문자가 기본 웹과 모바일 웹 사이를 이동할 때 개별적으로 식별되지 않도록 합니다.

## 앱의 방문자 ID

Android SDK는 앱이 설치될 때 고유 방문자 ID를 생성합니다. 이 ID는 모바일 장치의 영구 메모리에 저장되고 모든 히트와 함께 전송되며 사용자가 앱 설치를 제거하는 경우에만 제거됩니다.

>[!TIP]
>
>앱 방문자 ID는 업그레이드를 통해 지속됩니다.

## 모바일 웹의 방문자 ID

일반적인 모바일 웹 구현에서는 데스크톱 사이트에서 사용되는 것과 동일한 표준 Analytics `s_code.js` 또는 `AppMeasurement.js`를 사용합니다. JavaScript 라이브러리에는 고유한 방문자 ID를 생성하는 자체 메서드가 있습니다. 이로 인해 앱에서 모바일 웹 콘텐츠를 열 때 다른 방문자 ID가 생성됩니다.

## Implementing visitor tracking between an app and the mobile web {#section_1755BCCFD42D456EB2319141030FDDFF}

앱 및 모바일 웹에서 동일한 방문자 ID를 사용하려면

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 핵심 구현 *및* 라이프사이클에서 [Intellij 아이디어 또는 Eclipse 프로젝트에 SDK 및 구성 파일 추가를](/help/android/getting-started/dev-qs.md)참조하십시오.

1. 웹 보기를 여는 데 사용 중인 URL에 방문자 정보를 추가하려면 `visitorAppendToURL`을 호출합니다.

   ```java
   String urlString = "https://www.mydomain.com/index.php"; 
   String urlStringWithVisitorData = Visitor.appendToURL(urlString); 
   Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
   startActivity(browserIntent);
   ```

   또는, SDK 버전 4.16.0부터 `Visitor.getUrlVariablesAsync`를 호출할 수 있고 고유의 URL을 다음과 같이 생성할 수 있습니다.

   ```java
   final String urlString = "https://www.mydomain.com/index.php"; 
   Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
       @Override 
       public void call(String urlVariables) { 
           final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
           final Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
           startActivity(browserIntent); 
       } 
   });
   ```

대상 도메인의 ID 서비스 코드는 Adobe에 새 ID 요청을 전송하는 대신 URL에서 MID를 추출합니다. 이 코드는 전달된 MID를 사용하여 방문자를 추적합니다.

모바일 웹 콘텐츠의 히트에서 각 히트에 `mid` 매개 변수가 있는지 확인하고 이 값이 앱 코드에서 전송되는 `mid`와 일치하는지 확인합니다.

## Troubleshooting visitor tracking {#section_9B641F8569E34A089C52AA28EA4C891D}

### `Visitor.appendToURL`표시되지 않습니다.

상위 애플리케이션에서 번들로 제공되는 Adobe SDK 버전이 4.12.0 이상인지 확인하십시오.

**URL에 Adobe ID가 표시되지 않습니다.**

* 다음을 확인합니다.
   * 웹 보기를 여는 데 사용 중인 URL 문자열이 `Visitor.appendToURL(urlString)`)에서 생성되었습니다.
   * Adobe ID가 인코딩되어 있습니다.
To ensure that the IDs that are appended to the URL that is being opened, verify that the `adobe_mc` query parameter appears in the URL.

### 내 앱의 `mid`가 웹 보기의 mid와 동일하지 않습니다.

* 다음을 확인합니다.

   * 웹 보기를 여는 데 사용 중인 URL 문자열이 `Visitor.appendToURL(urlString)`)에서 생성되었습니다.
   * URL 문자열에 Adobe 매개 변수가 포함되어 있습니다.

      The string should contain `adobe_mc="SAMPLE_ID_DATA"` where `"SAMPLE_ID_DATA"` contains the IDs that are generated in the Adobe Mobile SDK.
   * `VisitorAPI.js` 버전이 1.7.0 이상입니다.

이러한 문제 해결 단계로 문제가 해결되지 않으면 Adobe Experience Care에 문의하십시오.

>[!IMPORTANT]
>
>Adobe에서 구현을 검증할 수 있도록 하려면 샘플 응용 프로그램과 관련 사이트를 공유해야 합니다.

