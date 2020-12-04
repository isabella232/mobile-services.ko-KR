---
description: iOS 확장 프로그램을 사용하면 Apple Watch 앱(WatchOS 1), 오늘 위젯, 사진 편집 위젯 및 기타 iOS 확장 앱에서 사용 데이터를 효율적으로 수집할 수 있습니다.
seo-description: iOS 확장 프로그램을 사용하면 Apple Watch 앱(WatchOS 1), 오늘 위젯, 사진 편집 위젯 및 기타 iOS 확장 앱에서 사용 데이터를 효율적으로 수집할 수 있습니다.
seo-title: iOS 확장 프로그램 구현
solution: Experience Cloud,Analytics
title: iOS 확장 프로그램 구현
topic: Developer and implementation
uuid: 8afc03fe-403e-4643-ada1-30e403ede238
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 100%

---


# iOS 확장 프로그램 구현 {#ios-extension-implementation}

iOS 확장 프로그램을 사용하면 Apple Watch 앱(WatchOS 1), 오늘 위젯, 사진 편집 위젯 및 기타 iOS 확장 앱에서 사용 데이터를 효율적으로 수집할 수 있습니다.

## 새로운 Adobe Experience Platform Mobile SDK 릴리스

Adobe Experience Platform Mobile SDK와 관련된 정보 및 설명서를 찾고 계십니까? [여기](https://aep-sdks.gitbook.io/docs/)를 클릭하여 최신 설명서를 확인하십시오.

2018년 9월 일자로 SDK의 새로운 주요 버전을 릴리스하였습니다. 이러한 새로운 Adobe Experience Platform Mobile SDK는 [Experience Platform Launch](https://www.adobe.com/kr/experience-platform/launch.html)를 통해 구성할 수 있습니다.

* 시작하려면 Adobe Experience Platform Launch로 이동합니다.
* Experience Platform SDK 리포지토리의 항목을 보려면 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)로 이동하십시오.

## 래퍼 대신 iOS SDK를 사용하기 위한 권장 사항 {#section_97577331FD9E4FFBBE05D402C67AEE69}

>[!IMPORTANT]
>
>자체 래퍼보다는 iOS SDK를 사용하는 것이 좋습니다.

Apple은 포함 앱에 요청을 보내고 응답을 받아 Watch 앱이 포함 앱과 통신할 수 있도록 하는 일련의 API를 제공합니다. Watch 앱에서 포함 앱으로 추적 데이터를 사전으로 보내고 포함 앱에서 추적 메서드를 호출하여 데이터를 전송할 수 있지만 이 솔루션에는 제한이 있습니다.

대부분의 경우, 사용자가 Watch 앱을 사용할 때 포함된 앱은 백그라운드에서 실행되며 `TrackActionInBackground`, `TrackLocation` 및 `TrackBeacon`을 호출해야만 안전합니다. 다른 추적 메서드를 호출하면 라이프사이클 데이터가 방해되므로, 이 세 메서드만 사용하여 Watch 앱의 데이터를 전송해야 합니다.

이 세 추적 메서드가 요구 사항을 만족하더라도 Watch 앱용 SDK에 인앱 메시지를 제외한 모든 모바일 기능이 포함되므로, iOS SDK를 사용하십시오.

## 시작하기 {#section_D0BE4F780C9C4CD8ADD2AD4EE0BD5FD4}

>[!IMPORTANT]
>
>프로젝트에 최소한 다음 타겟이 포함되어 있는지 확인하십시오.
>
>* 앱을 포함할 하나의 타겟.
>* 확장을 위한 하나의 타겟.
>



WatchKit 앱에서 작업하는 경우 세 번째 타겟이 있어야 합니다. Apple Watch용 개발에 대한 자세한 내용은 [Apple Watch용 개발](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/index.html#//apple_ref/doc/uid/TP40014969-CH8-SW1)을 참조하십시오.

## 포함된 앱 구성 {#section_0BAB0842E4C04A62B5E03DFC4BA77851}

Xcode 프로젝트에서 다음 단계를 완료하십시오.

1. AdobeMobileLibrary 폴더를 프로젝트로 드래그합니다.
1. `ADBMobileConfig.json` 파일이 포함된 앱 타겟의 구성원인지 확인합니다.
1. 포함 앱 타겟의 **[!UICONTROL 빌드 단계]** 탭에서 **[!UICONTROL 바이너리를 라이브러리와 연결]** 섹션을 확장하고 다음 라이브러리를 추가합니다.

   * `AdobeMobileLibrary.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. 포함된 앱 타겟의 **[!UICONTROL 기능]** 탭을 열고, **[!UICONTROL 앱 그룹]**&#x200B;을 사용하도록 설정하고, 새 앱 그룹을 추가합니다(예: `group.com.adobe.testAp`).

1. Adobe Mobile 라이브러리를 조작하기 전에, 애플리케이션 위임에서 `application:didFinishLaunchingWithOptions`에 앱 그룹을 설정합니다.

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. 예기치 않은 오류 없이 앱이 빌드되는지 확인합니다.

## 확장 프로그램 구성{#section_28C994B7892340AC8D1F07AF26FF3946}

1. `ADBMobileConfig.json` 파일이 확장 프로그램의 타겟 구성원인지 확인합니다.
1. 확장 프로그램 타겟의 **[!UICONTROL 빌드 단계]** 탭에서 **[!UICONTROL 바이너리를 라이브러리와 연결]** 섹션을 확장하고 다음 라이브러리를 추가합니다.

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. 확장 프로그램 타겟의 **[!UICONTROL 기능]** 탭을 열고, **[!UICONTROL 앱 그룹]**&#x200B;을 사용하도록 설정하고, 위의 *포함된 앱 구성*&#x200B;의 4단계에서 추가한 앱 그룹을 선택합니다.

1. Adobe Mobile 라이브러리를 조작하기 전에 InterfaceController에서 `awakeWithContext:`에 앱 그룹을 설정합니다.

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. 예기치 않은 오류 없이 앱이 빌드되는지 확인합니다.

## 추가 참고 사항 {#section_21497E81231549CB9F164DEECFF5BA0D}

다음은 기억해야 할 몇 가지 정보입니다.

* 컨텍스트 데이터 값 `a.RunMode`가 추가되었으며, 이 값은 데이터의 출처가 포함 앱인지 아니면 확장 프로그램인지 나타냅니다.

   * `a.RunMode = Application`

      이 값은 포함 앱에서 히트가 발생했음을 의미합니다.
   * `a.RunMode = Extension`

      이 값은 확장에서 히트가 발생했음을 의미합니다.

* 이전 버전의 SDK에서 업그레이드하는 경우, 포함 앱이 실행되면 Adobe에서는 포함된 앱의 폴더에서 앱 그룹의 공유 폴더로 모든 사용자 기본값과 캐시된 파일을 자동으로 마이그레이션합니다.
* 포함된 앱을 실행하지 않은 경우 확장의 히트가 무시됩니다.
* 버전 번호와 빌드 번호는 포함된 앱과 확장 앱 간에 동일해야 합니다.
* iOS 확장 앱에서는 라이프사이클 호출이 트리거되지 않습니다.

