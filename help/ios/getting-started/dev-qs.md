---
description: 다음은 iOS 라이브러리를 구현하고 시작, 업그레이드, 세션, 참여 사용자 등의 라이프사이클 지표를 수집하는 데 유용한 정보입니다.
seo-description: 다음은 iOS 라이브러리를 구현하고 시작, 업그레이드, 세션, 참여 사용자 등의 라이프사이클 지표를 수집하는 데 유용한 정보입니다.
seo-title: 핵심 구현 및 라이프사이클
solution: Experience Cloud,Analytics
title: 핵심 구현 및 라이프사이클
topic: Developer and implementation
uuid: 96d06325-e424-4770-8659-4b5431318ee3
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '656'
ht-degree: 100%

---


# 핵심 구현 및 라이프사이클 {#core-implementation-and-lifecycle}

다음은 iOS 라이브러리를 구현하고 시작, 업그레이드, 세션, 참여 사용자 등의 라이프사이클 지표를 수집하는 데 유용한 정보입니다.

## SDK 다운로드 {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>SDK를 다운로드하려면 iOS 6 이상을 사용&#x200B;**해야** 합니다.

**전제 조건**

SDK를 다운로드하기 전에 [핵심 구현 및 라이프사이클](/help/ios/getting-started/requirements.md)에서 *보고서 세트 생성*&#x200B;의 단계를 완료하여 개발 보고서 세트를 설정하고 미리 채워진 구성 파일 버전을 다운로드합니다.

SDK를 다운로드하려면:

1. `[Your_App_Name_]AdobeMobileLibrary-4.*-iOS.zip` 파일을 다운로드하여 압축을 푼 후에 다음 소프트웨어 구성 요소가 있는지 확인합니다.

   * `ADBMobile.h`: iOS AppMeasurement용으로 사용되는 Objective-C 헤더 파일입니다.
   * `ADBMobileConfig.json`: 앱에 맞게 사용자 지정된 SDK 구성 파일입니다.
   * `AdobeMobileLibrary.a` iOS 장치(armv7, armv7s, arm64)와 시뮬레이터(i386, x86_64)의 라이브러리 빌드가 포함된 비트코드 사용 패트 바이너리입니다.

      iOS 앱이 타겟인 경우 이 패트 바이너리를 연결해야 합니다.

   * `AdobeMobileLibrary_Extension.a`: iOS 장치(armv7, armv7s, arm64)와 시뮬레이터(i386, x86_64)의 라이브러리 빌드가 포함된 Bitcode 사용 패트 바이너리입니다.

      iOS 확장 프로그램이 타겟인 경우 이 패트 바이너리를 연결해야 합니다.

   * `AdobeMobileLibrary_Watch.a`: Apple Watch 장치(armv7k)와 시뮬레이터(i386, x86_64)의 라이브러리 빌드가 포함된 Bitcode 사용 패트 바이너리입니다.

      Apple Watch(watchOS 2) 확장 앱이 타겟인 경우 이 패트 바이너리를 연결해야 합니다.

   * `AdobeMobileLibrary_TV.a`: 새 Apple TV 장치(arm64)와 시뮬레이터(x86_64)의 라이브러리 빌드가 포함된 Bitcode 사용 패트 바이너리입니다.

      Apple TV(tvOS) 앱이 타겟인 경우 이 패트 바이너리를 연결해야 합니다.

>[!IMPORTANT]
>
>Adobe Mobile Services UI 외부에서 SDK를 다운로드하는 경우에는 `ADBMobileConfig.json` 파일을 수동으로 구성해야 합니다. Analytics 및 Mobile SDK를 처음 사용하는 경우 [시작하기 전에](/help/ios/getting-started/requirements.md)를 참조하여 개발 보고서 세트를 설정하고 미리 채워진 구성 파일 버전을 다운로드합니다.

## 프로젝트에 SDK 및 구성 파일 추가 {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Xcode IDE를 실행하고 앱을 엽니다.
1. Project Navigator에서 `AdobeMobileLibrary` 폴더를 드래그하여 프로젝트 아래에 놓습니다.
1. 다음을 확인합니다.

   * **[!UICONTROL 필요한 경우 항목 복사]** 확인란이 선택되어 있습니다.
   * **[!UICONTROL 그룹 생성]**&#x200B;이 선택되어 있습니다.
   * **[!UICONTROL 대상에 추가]** 섹션의 확인란이 선택되어 있지 않습니다.

   ![](assets/step_3.png)

1. **[!UICONTROL 마침을 클릭합니다]**.
1. **[!UICONTROL Project Navigator]**&#x200B;에서 **`ADBMobileConfig.json`**&#x200B;를 선택합니다.
1. **[!UICONTROL File Inspector]**&#x200B;에서 Adobe SDK를 사용할 프로젝트의 타겟에 JSON 파일을 추가합니다.

   ![](assets/step_4.png)

1. **[!UICONTROL Project Navigator]**&#x200B;에서 다음 단계를 완료합니다.

   1. 앱을 클릭합니다.
   1. **[!UICONTROL 일반]** 탭에서 타겟을 선택하고 **[!UICONTROL 연결된 프레임워크]** 및 라이브러리&#x200B;**[!UICONTROL 섹션에서 필요한 프레임워크 및 라이브러리를 연결합니다.]**
   * **iOS 앱 타겟**
      * `SystemConfiguration.framework`
      * `WebKit.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary.a`
      * `CoreLocation.framework`(선택 사항이지만 지역 추적 기능에 필요함)
   * **iOS 확장 프로그램 타겟**

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Extension.a`
   * **Apple Watch(watchOS 2) 타겟**

      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Watch.a`
   * **Apple TV(tvOS) 타겟**

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_TV.a`

   >[!CAUTION]
   >
   > 두 개 이상의 `AdobeMobileLibrary*.a` 파일을 동일한 타겟에 연결하면 예기치 않은 동작이 발생하거나 빌드할 수 없게 됩니다.

1. 오류 없이 앱이 빌드되는지 확인합니다.

## 라이프사이클 지표 구현 {#section_532702562A7A43809407C9A2CBA80E1E}

>[!IMPORTANT]
>
>iOS는 `collectlifecycledata`를 호출하거나 호출하지 않고 라이프사이클 정보를 전송하며 `collectlifecycledata`는 애플리케이션의 실행 시퀀스에서 이전의 라이프사이클을 시작하는 유일한 방법입니다.

라이프사이클을 사용하면 앱이 시작될 때마다 시작, 업그레이드, 세션, 참여 사용자 및 기타 [라이프사이클 지표](/help/ios/metrics.md)를 측정하기 위해 한 번의 히트가 전송됩니다.

`application:didFinishLaunchingWithOptions`에 `collectLifecycleData`/`collectLifecycleDataWithAdditionalData` 호출을 추가합니다.

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
 [ADBMobile collectLifecycleData]; 
    return YES; 
}
```

### 라이프사이클 호출로 추가 데이터 포함

라이프사이클 지표 호출을 통해 추가 데이터를 포함하려면 `collectLifecycleDataWithAdditionalData`를 사용하십시오.

>[!IMPORTANT]
>
>`collectLifecycleDataWithAdditionalData:`를 통해 SDK에 전달되는 모든 데이터는 SDK에 의해 `NSUserDefaults`에서 유지됩니다. SDK는 `NSDictionary` 또는 `NSString` 유형이 아닌 `NSNumber` 매개 변수에서 값을 제거합니다.

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
    NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
    [contextData setObject:@"Game" forKey:@"myapp.category"]; 
    [ADBMobile collectLifecycleDataWithAdditionalData:contextData]; 
    return YES; 
}
```

`collectLifecycleDataWithAdditionalData`와 함께 전송되는 추가 컨텍스트 데이터 값은 Adobe Mobile Services의 사용자 지정 변수에 매핑해야 합니다.

![](assets/map-variable-lifecycle.png)

다른 라이프사이클 지표는 자동으로 수집됩니다. 자세한 내용은 [라이프사이클 지표](/help/ios/metrics.md)를 참조하십시오.

## 다음 단계 {#section_A24DC703359D4B5C8F493D6421306FD3}

다음 작업을 완료하십시오.

* [앱 상태 추적](/help/ios/analytics-main/states.md)
* [앱 작업 추적](/help/ios/analytics-main/actions.md)
