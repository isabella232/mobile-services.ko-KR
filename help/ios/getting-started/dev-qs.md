---
description: 다음은 iOS 라이브러리를 구현하고 시작, 업그레이드, 세션, 참여 사용자 등의 라이프사이클 지표를 수집하는 데 유용한 정보입니다.
seo-description: 다음은 iOS 라이브러리를 구현하고 시작, 업그레이드, 세션, 참여 사용자 등의 라이프사이클 지표를 수집하는 데 유용한 정보입니다.
seo-title: 핵심 구현 및 라이프사이클
solution: Marketing Cloud,Analytics
title: 핵심 구현 및 라이프사이클
topic: 개발자 및 구현
uuid: 96d06325-e424-4770-8659-4b5431318ee3
translation-type: tm+mt
source-git-commit: be980e0e639d5b0df3f1b6a6f91f3ad0a5efe8d7

---


# Core implementation and lifecycle {#core-implementation-and-lifecycle}

다음은 iOS 라이브러리를 구현하고 시작, 업그레이드, 세션, 참여 사용자 등의 라이프사이클 지표를 수집하는 데 유용한 정보입니다.

## SDK 다운로드 {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>To download the SDKs, you **must** use iOS 6 or later.

**전제 조건**

SDK를 다운로드하기 전에 Core 구현 및 *라이프사이클에서* 보고서 세트 [](/help/ios/getting-started/requirements.md) 만들기의 단계를 완료하여 개발 보고서 세트를 설정하고 미리 채워진 구성 파일 버전을 다운로드합니다.

SDK를 다운로드하려면:

1. Download, unzip the `[Your_App_Name_]AdobeMobileLibrary-4.*-iOS.zip` file and verify that you have the following software components:

   * `ADBMobile.h`: iOS AppMeasurement용으로 사용되는 Objective-C 헤더 파일입니다.
   * `ADBMobileConfig.json`: 앱에 맞게 사용자 지정된 SDK 구성 파일입니다.
   * `AdobeMobileLibrary.a`, iOS 장치(armv7, armv7s, arm64) 및 시뮬레이터(i386, x86_64)에 대한 라이브러리 빌드가 포함된 bitcode 지원 지방 바이너리입니다.

      iOS 앱이 타겟인 경우 이 패트 바이너리를 연결해야 합니다.

   * `AdobeMobileLibrary_Extension.a`: iOS 장치(armv7, armv7s, arm64)와 시뮬레이터(i386, x86_64)의 라이브러리 빌드가 포함된 Bitcode 사용 패트 바이너리입니다.

      iOS 확장 프로그램이 타겟인 경우 이 패트 바이너리를 연결해야 합니다.

   * `AdobeMobileLibrary_Watch.a`: Apple Watch 장치(armv7k)와 시뮬레이터(i386, x86_64)의 라이브러리 빌드가 포함된 Bitcode 사용 패트 바이너리입니다.

      Apple Watch(watchOS 2) 확장 앱이 타겟인 경우 이 패트 바이너리를 연결해야 합니다.

   * `AdobeMobileLibrary_TV.a`: 새 Apple TV 장치(arm64)와 시뮬레이터(x86_64)의 라이브러리 빌드가 포함된 Bitcode 사용 패트 바이너리입니다.

      Apple TV(tvOS) 앱이 타겟인 경우 이 패트 바이너리를 연결해야 합니다.

>[!IMPORTANT]
>
>If you download the SDK outside the Adobe Mobile services UI, the `ADBMobileConfig.json` file must be manually configured. If you are new to Analytics and the Mobile SDK, see [Before You Start](/help/ios/getting-started/requirements.md) to set up a development report suite and download a pre-populated version of the configuration file.

## Add the SDK and config file to your project {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Xcode IDE를 실행하고 앱을 엽니다.
1. Project Navigator에서 `AdobeMobileLibrary` 폴더를 드래그하여 프로젝트 아래에 놓습니다.
1. 다음을 확인합니다.

   * **[!UICONTROL 필요한 경우 항목 복사]확인란이 선택되어 있습니다.**
   * **[!UICONTROL 그룹 생성]**&#x200B;이 선택되어 있습니다.
   * **[!UICONTROL 대상에 추가]섹션의 확인란이 선택되어 있지 않습니다.**
   ![](assets/step_3.png)

1. **[!UICONTROL 마침을 클릭합니다]**.
1. In **[!UICONTROL Project Navigator]**, select **[!UICONTROL`ADBMobileConfig.json`]**.
1. In **[!UICONTROL File Inspector]**, add the JSON file to any targets in your project that will use the Adobe SDK.

   ![](assets/step_4.png)

1. In **[!UICONTROL Project Navigator]**, complete the following steps:

   1. 앱을 클릭합니다.
   1. **[!UICONTROL 일반]** 탭에서 타겟을 선택하고 **[!UICONTROL 연결된 프레임워크]및**&#x200B;라이브러리&#x200B;**섹션에서 필요한 프레임워크 및 라이브러리를 연결합니다.**
   * **iOS 앱 타겟**
      * `SystemConfiguration.framework`
      * `WebKit.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary.a`
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
   > Linking more than one `AdobeMobileLibrary*.a` file in the same target will result in unexpected behavior or the inability to build.

1. 오류 없이 앱이 빌드되는지 확인합니다.

## Implement lifecycle metrics {#section_532702562A7A43809407C9A2CBA80E1E}

>[!IMPORTANT]
>
>iOS will send lifecycle information with or without calling `collectlifecycledata`, and `collectlifecycledata` is only a way to initiate lifecycle earlier in the application's launch sequence.

After you enable lifecycle, each time your app is launched, one hit is sent to measure launches, upgrades, sessions, engaged users, and other [Lifecycle Metrics](/help/ios/metrics.md).

추가 `collectLifecycleData`/ `collectLifecycleDataWithAdditionalData` 호출 `application:didFinishLaunchingWithOptions`:

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
 [ADBMobile collectLifecycleData]; 
    return YES; 
}
```

### 라이프사이클 호출과 함께 추가 데이터 포함

라이프사이클 지표 호출을 통해 추가 데이터를 포함하려면 `collectLifecycleDataWithAdditionalData`를 사용하십시오.

>[!IMPORTANT]
>
>Any data that is passed to the SDK through `collectLifecycleDataWithAdditionalData:` is persisted in `NSUserDefaults` by the SDK. SDK는 `NSDictionary` 또는 `NSString` 유형이 아닌 `NSNumber` 매개 변수에서 값을 제거합니다.

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
