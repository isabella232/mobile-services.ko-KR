---
description: 다음은 tvOS로 Apple TV를 구현하는 데 유용한 정보입니다.
solution: Experience Cloud Services,Analytics
title: tvOS를 사용한 Apple TV 구현
topic-fix: Developer and implementation
uuid: d1571ea2-a5de-4b96-a527-72abbf51fab8
exl-id: 35b7f02d-ae48-4c6f-9a3a-6d106a1026ad
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 100%

---

# tvOS를 사용한 Apple TV 구현 {#apple-tv-implementation-with-tvos}

다음은 tvOS로 Apple TV를 구현하는 데 유용한 정보입니다.

## 새로운 Adobe Experience Platform Mobile SDK 릴리스

Adobe Experience Platform Mobile SDK와 관련된 정보 및 설명서를 찾고 계십니까? [여기](https://aep-sdks.gitbook.io/docs/)를 클릭하여 최신 설명서를 확인하십시오.

2018년 9월 일자로 SDK의 새로운 주요 버전을 릴리스하였습니다. 이러한 새로운 Adobe Experience Platform Mobile SDK는 [Experience Platform Launch](https://www.adobe.com/kr/experience-platform/launch.html)를 통해 구성할 수 있습니다.

* 시작하려면 Adobe Experience Platform Launch로 이동합니다.
* Experience Platform SDK 리포지토리의 항목을 보려면 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)로 이동하십시오.

## 개요

이제 Apple TV로 기본 tvOS 환경에서 실행할 애플리케이션을 만들 수 있습니다. iOS에서 사용 가능한 여러 프레임워크를 사용하여 기본적인 앱을 만들거나 XML 템플릿 및 JavaScript를 사용하여 사용자 앱을 만들 수 있습니다.

>[!TIP]
>
>tvOS 지원은 `AdobeMobileLibrary` 버전 4.7.0부터 제공됩니다.

## 시작하기 {#section_CAB40A5B5FC745068C8A5DF8F9AB6199}

>[!TIP]
>
>프로젝트에 tvOS를 타깃팅하는 타겟, 즉 Apple TV 앱이 있다고 가정합니다. 자세한 내용은 [tvOS](https://developer.apple.com/tvos/documentation/)를 참조하십시오.

## tvOS용 기본 앱 구성 {#section_5095F19B3C4545F68E8C1E37A7E303AE}

Xcode 프로젝트에서 다음 단계를 완료하십시오.

1. AdobeMobileLibrary 폴더를 프로젝트로 드래그합니다.
1. `ADBMobileConfig.json` 파일이 타겟 구성원인지 확인합니다.
1. tvOS 앱 타겟의 **[!UICONTROL 빌드 단계]** 탭에서 **[!UICONTROL 바이너리를 라이브러리와 연결]** 섹션을 확장하고 다음 라이브러리를 추가합니다.

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

자세한 내용은 [iOS](https://developer.apple.com/ios/resources/)의 iOS 설명서를 참조하십시오.

## tvOS용 TVML/TVJS 앱 구성 {#section_AB2EC8C326654F3387658EBBD990BB12}

1. `AdobeMobileLibrary` 폴더를 프로젝트로 드래그합니다.
1. `ADBMobileConfig.json` 파일이 타겟 구성원인지 확인합니다.
1. tvOS 앱 타겟의 **[!UICONTROL 빌드 단계]** 탭에서 **[!UICONTROL 바이너리를 라이브러리와 연결]** 섹션을 확장하고 다음 라이브러리를 추가합니다.

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

1. `TVApplicationControllerDelegate` 클래스의 구현 파일에서 SDK를 가져옵니다.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. `TVApplicationControllerDelegate` 클래스의 `application:didFinishLaunchWithOptions:` 메서드에서 `installTVMLHooks:` 메서드를 사용하여 `TVApplicationController` 개체를 SDK에 전달합니다.

   Adobe SDK를 앱의 JSContext에 등록하려면 앱의 `TVApplicationController`에 액세스해야 합니다. 이 단계에서는 JavaScript 파일에서 Adobe SDK의 기본 메서드를 호출할 수 있습니다.

   ```objective-c
   [ADBMobile installTVMLHooks:appController];
   ```

1. JavaScript 파일에서 `ADBMobile` 개체를 사용하여 Adobe SDK의 기본 메서드에 액세스합니다.

   사용할 수 있는 메서드의 전체 목록은 [TVJS 메서드](/help/ios/apple-tv-implementation-tvos/tvjs-methods.md)를 참조하십시오.
