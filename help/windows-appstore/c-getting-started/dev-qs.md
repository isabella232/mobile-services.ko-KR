---
description: 'null'
seo-description: 'null'
seo-title: 개발자 빠른 시작
solution: Marketing Cloud, Analytics
title: 개발자 빠른 시작
topic: 개발자 및 구현
uuid: B 368959 B-D 985-436 E -8 B 3 E -97 E 355 A 97951
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start {#developer-quick-start}

SDK를 구현하려면 Visual Studio 2013 이상이 필요합니다.

## SDK 가져오기 {#section_99FE1A17A36D4A2C943939023CF6265C}

[SDK 다운로드](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)를 압축 해제하면 지원되는 각 아키텍처 및 플랫폼 조합에 대해 별도의 폴더가 있습니다. 이 가이드의 뒷부분에 설명된 `ADBMobileConfig.json` 파일도 있습니다.

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll`/ `.winmd` files are provided for each target platform (Windows 8.1, Windows Phone 8.1), and supported architecture (x86, x64, ARM). 파일은 다음에 따라 폴더 구조로 구분됩니다.

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. `.winmd` 파일에는 메타데이터만 포함되어 있으며 이에 따라 Microsoft에 따라 `255.255.255.255` 허용되는 비헤이비어가 포함되어 있습니다 (winrt C + [+/CX 구성 요소 DLL에 대한 어셈블리 정보를 추가하는 방법은 참조).](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode) 참조). To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## Syntax differences {#section_A02DE120B6D240F5AFFE7509755C4F14}

Windows 8.1 Universal App Store 라이브러리는 여러 프로그래밍 언어로 사용할 수 있습니다. 이 가이드의 예는 WinJS(JavaScript)로 작성되어 있으므로 다른 언어를 사용하는 경우에는 수정해야 할 수 있습니다. winJS(JavaScript)에서 winmd 메서드를 사용할 때 모든 메서드에서 첫 번째 문자가 자동으로 소문자가 됩니다.

구현 간의 주요 차이점은 컨텍스트 데이터에 사용되는 데이터 구조입니다.

Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config file to your project - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Visual Studio를 시작하고 솔루션을 엽니다.
1. **솔루션 탐색기에서****[!UICONTROL 참조를]** 마우스 오른쪽 단추로 클릭하고 참조 **[!UIUCONTROL 추가를]**&#x200B;선택합니다.

1. Select the correct version of the library and browse to the associated `ADBMobile.winmd` file.

   자세한 내용은 아래 올바른 버전 *선택* 섹션을 참조하십시오.

1. **[!UICONTROL 추가를 클릭합니다]**.

1. Verify that `ADBMobile.winmd` is selected in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Windows Phone 앱에 참조를 추가할 때, 구성 `ADBMobile.winmd`**[!UICONTROL 요소 파일에서]** **모든 파일로 기본 파일 필터를 변경합니다**.

1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 버튼으로 클릭하고 **참조 추가[!UICONTROL 를 선택합니다]**.

   솔루션에 C + + 프로젝트가 있는 경우 이 단계를 건너뜁니다.

1. 왼쪽의 **Windows** 탭에서 **[!UICONTROL 확장을]**&#x200B;선택한 다음 Windows 용 **[!UICONTROL Microsoft Visual C + + 2013 런타임 패키지를 선택합니다]**.

1. 다음 줄을 클래스에 추가합니다.

   ```
   using ADBMobile;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. `ADBMobileConfig.json` 파일을 찾아 ****&#x200B;추가를 클릭합니다.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. **[!UICONTROL 빌드 작업을]** 콘텐츠로 ****&#x200B;변경

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Visual Studio를 시작하고 솔루션을 엽니다.
1. **[!UICONTROL 솔루션 탐색기에서]**&#x200B;프로젝트를 마우스 오른쪽 버튼으로 클릭하고 **[!UICONTROL 추가]** &gt; **[!UICONTROL 참조를 선택합니다]**.

1. Select the correct version of the library and then add a reference to the associated `ADBMobile.winmd` file.

   자세한 내용은 아래 올바른 버전 *선택* 섹션을 참조하십시오.

1. **[!UICONTROL 추가를 클릭합니다]**.

1. **[!UICONTROL [참조 관리자]** ] 창에서 `ADBMobile.winmd` 선택되었는지 확인하고 **[!UICONTROL [확인]**] 를 클릭합니다.

   >[!TIP]
   >
   >Windows Phone 앱에 참조를 추가할 때, 구성 `ADBMobile.winmd`**[!UICONTROL 요소 파일에서]** **모든 파일로 기본 파일 필터를 변경합니다**.

1. 다음 줄을 클래스에 추가합니다.

   ```
   using namespace ADMS::Measurement;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. `ADBMobileConfig.json` 파일을 찾아 ****&#x200B;추가를 클릭합니다.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. **[!UICONTROL [일반]** ] 탭에서 **[!UICONTROL 콘텐트를]** **[!UICONTROL [예]**] 로 변경한 다음 [ **[!UICONTROL 확인]**] 를 클릭합니다.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Visual Studio를 시작하고 솔루션을 엽니다.
1. **솔루션 탐색기에서****[!UICONTROL 참조를]** 마우스 오른쪽 단추로 클릭하고 **[! Uicontrol 참조를 추가합니다**.

   자세한 내용은 아래 *올바른 버전* 선택 섹션을 참조하십시오.

1. Select the correct version of the library and then browse to the associated `ADBMobile.winmd` file.

1. **[!UICONTROL 추가를 클릭합니다]**.

1. Verify that `ADBMobile.winmd` is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Windows Phone 앱에 참조를 추가할 때, 구성 `ADBMobile.winmd`**[!UICONTROL 요소 파일에서]** **모든 파일로 기본 파일 필터를 변경합니다**.

1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 버튼으로 클릭하고 **참조 추가[!UICONTROL 를 선택합니다]**.

   솔루션에 C + + 프로젝트가 있는 경우 이 단계를 건너뜁니다.

1. 왼쪽의 **[!UICONTROL Windows]** 탭에서 **[!UICONTROL Extension]** 를 선택하고 Windows 용 **[!UICONTROL Microsoft Visual C + + 2013 런타임 패키지를 선택합니다]**.

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. `ADBMobileConfig.json` 파일을 찾아 ****&#x200B;추가를 클릭합니다.

1. Right-click the `ADBMobileConfig.json]` file in your solution and select **[!UICONTROL Properties]**.

1. **[!UICONTROL 파일 속성을]** 선택한 상태에서 **[!UICONTROL 패키지 작업이]** 콘텐츠로 **[!UICONTROL 설정되어 있는지]**&#x200B;확인합니다.

   JavaScript 프로젝트의 경우 기본적으로 파일이 **[!UICONTROL [콘텐트]** ] 로 설정됩니다.

## Update the ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

`ADBMobileConfig.json` 파일은 전역 SDK 설정을 포함하며 *프로젝트* 섹션에 라이브러리 및 구성 파일 추가 섹션의 단계를 완료한 후에 프로젝트 루트에 있습니다. If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

다음은 `ADBMobileConfig.json` 파일 예제입니다.

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
        "privacyDefault" : "optedin", 
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000], 
                    ["santa cruz",36.972935,-122.01725,600] 
                ] 
    }, 
 "target" : { 
  "clientCode" : "myTargetClientCode", 
  "timeout" : 1 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```

최소한 사용 중인 솔루션에 대해 다음 값을 업데이트하십시오.

* **분석**: `rsids` and `server`
* **Target**: `clientCode`
* **대상 관리**: `server`

For more details, see [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## 디버깅 {#section_3A10376A60394A15BEE483323E0CD4AA}

SDK에 디버깅을 사용하려면 `ADBMobile.Config.setDebugLogging(true);`);를 호출해야 합니다.

C Sharp 및 JS 앱의 경우 다음 단계를 완료하여 기본 코드 디버깅을 활성화해야 합니다. 기본 코드 디버깅은 C + + 앱에 대한 기본 설정입니다.

### C Sharp

Right-click the project, select **[!UICONTROL Properties]** &gt; **[!UICONTROL Debug tab]**. 디버거 드롭다운에서 **[!UICONTROL 기본값만 선택합니다]**.

### JS

Right-click the project, select  **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**. 디버거 유형 드롭다운을 **기본**&#x200B;으로 변경합니다.

그러면 됩니다! 이제 Windows 8.1 Universal App Store 앱에서 Analytics, Target 및 고객 관리를 구현할 준비가 되었습니다.
