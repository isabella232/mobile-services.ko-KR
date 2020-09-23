---
description: 모바일 웹 콘텐츠를 여는 앱의 경우, 방문자가 기본 웹과 모바일 웹 사이를 이동할 때 개별적으로 식별되지 않도록 해야 합니다.
seo-description: 모바일 웹 콘텐츠를 여는 앱의 경우, 방문자가 기본 웹과 모바일 웹 사이를 이동할 때 개별적으로 식별되지 않도록 해야 합니다.
seo-title: 앱과 모바일 웹 간 방문자 추적
solution: Experience Cloud,Analytics
title: 앱과 모바일 웹 간 방문자 추적
topic: Developer and implementation
uuid: 2d951de6-3954-4379-a4ff-99b9695b9869
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 87%

---


# 앱과 모바일 웹 간 방문자 추적 {#visitor-tracking-between-an-app-and-mobile-web}

모바일 웹 콘텐츠를 여는 앱의 경우, 방문자가 기본 웹과 모바일 웹 사이를 이동할 때 개별적으로 식별되지 않도록 해야 합니다.

## 앱의 방문자 ID

iOS SDK는 앱이 설치되면 고유 방문자 ID를 생성합니다. 이 ID는 모바일 장치의 영구 메모리에 저장되며 모든 히트와 함께 전송됩니다. 이 ID는 사용자가 앱을 제거할 때만 제거됩니다.

>[!TIP]
>
>앱 방문자 ID는 업그레이드 시에도 유지됩니다.

## 모바일 웹의 방문자 ID

일반적인 모바일 웹 구현에서는 데스크톱 사이트에서 사용되는 것과 동일한 표준 Analytics `s_code.js` 또는 `AppMeasurement.js`를 사용합니다. JavaScript 라이브러리에는 고유한 방문자 ID를 생성하는 자체 메서드가 있습니다. 이로 인해 앱에서 모바일 웹 콘텐츠를 열 때 다른 방문자 ID가 생성됩니다.

앱 및 모바일 웹에서 동일한 방문자 ID를 사용하고 URL의 모바일 웹에 앱 방문자 ID를 전달하려면 다음을 수행하십시오.

## 앱과 모바일 웹 간 방문자 추적 구현 {#section_EDC91D6C67AD43999227707C2769C65D}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 [핵심 구현 및 라이프사이클](/help/ios/getting-started/dev-qs.md)에서 *프로젝트에 SDK 및 구성 파일 추가*&#x200B;를 참조하십시오.
1. 웹 보기를 여는 데 사용 중인 URL에 방문자 정보를 추가하려면 `visitorAppendToURL`을 호출합니다.

   ```objective-c
   NSURL *url = [NSURL URLWithString:@”https://www.mydomain.com/index.php"]; 
   NSURL *urlWithVisitorData = [ADBMobile visitorAppendToURL:url]; 
   [[UIApplication sharedApplication] openURL:urlWithVisitorData];
   ```

   또는, SDK 버전 4.16.0부터 `visitorGetUrlVariablesAsync:`를 호출할 수 있고 고유의 URL을 다음과 같이 생성할 수 있습니다.

   ```objective-c
   NSString *urlString = @"https://www.mydomain.com/index.php"; 
   [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
       NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
       NSURL *urlWithVisitorData = [NSURL URLWithString:urlStringWithVisitorData]; 
       [[UIApplication sharedApplication] openURL:urlWithVisitorData options:@{} completionHandler:^(BOOL success) { 
           // handle openURL success 
       }]; 
   }];
   ```

대상 도메인의 ID 서비스 코드는 새 ID에 대한 요청을 Adobe으로 보내는 대신 URL에서 MID를 추출합니다. 대상 페이지의 ID 서비스 코드는 전달한 MID를 사용하여 방문자를 추적합니다.

모바일 웹 콘텐츠의 히트에서 각 히트에 `mid` 매개 변수가 있는지 확인하고 이 값이 앱 코드에서 전송 중인 `mid`와 일치하는지 확인합니다.

## 방문자 추적 문제 해결 {#section_C070AE85E3CE4E9893FD4F40E73F2C92}

### `[ADBMobile visitorAppendToURL:]`이 표시되지 않습니다.

상위 애플리케이션에서 번들로 제공되는 Adobe SDK 버전이 4.12.0 이상인지 확인하십시오.

### URL에 Adobe ID가 표시되지 않습니다.

다음을 확인합니다.

* 웹 보기를 여는 데 사용 중인 URL 문자열이 `[ADBMobile visitorAppendToURL:]`에서 생성되었습니다.

* Adobe ID가 인코딩되어 있습니다.

   열고 있는 URL에 ID가 추가되었는지 확인하려면 `adobe_mc` 쿼리 매개 변수를 찾으십시오.

### 내 앱의 &#39;mid&#39;가 웹 보기의 mid와 동일하지 않습니다.*

다음을 확인합니다.

* 웹 보기를 여는 데 사용 중인 URL 문자열이 `[ADBMobile visitorAppendToURL:]`에서 생성되었습니다.

   URL 문자열에 Adobe 매개 변수가 포함되어 있습니다.

   이 문자열에는 `adobe_mc="SAMPLE_ID_DATA"`가 있어야 하며, 여기서 `"SAMPLE_ID_DATA"`에는 Adobe Mobile SDK에서 생성한 ID가 포함되어 있습니다.

* `VisitorAPI.js` 버전이 1.7.0 이상입니다.

이러한 문제 해결 단계로 문제가 해결되지 않으면 Adobe Client Care에 문의하십시오. Adobe에서 구현을 검증할 수 있도록 샘플 애플리케이션 및 관련 사이트를 공유할 준비를 하십시오.
