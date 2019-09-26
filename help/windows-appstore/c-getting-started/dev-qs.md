---
description: 'null'
seo-description: 'null'
seo-title: 개발자 빠른 시작
solution: Marketing Cloud,Analytics
title: Developer quick start
topic: 개발자 및 구현
uuid: b368959b-d985-436e-8b3e-97e355a97951
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
>The version of `ADBMobile.winmd` does not reflect the version of the library. The `.winmd` file contains metadata only, and as such will have a version number of `255.255.255.255` which is accepted behavior according to Microsoft (see [How do I add assembly information for a WinRT C++ / CX component dll?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode) 참조). To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## Syntax differences {#section_A02DE120B6D240F5AFFE7509755C4F14}

Windows 8.1 Universal App Store 라이브러리는 여러 프로그래밍 언어로 사용할 수 있습니다. 이 가이드의 예는 WinJS(JavaScript)로 작성되어 있으므로 다른 언어를 사용하는 경우에는 수정해야 할 수 있습니다. winJS(JavaScript)에서 winmd 메서드를 사용할 때 모든 메서드에서 첫 번째 문자가 자동으로 소문자가 됩니다.

구현 간의 주요 차이점은 컨텍스트 데이터에 사용되는 데이터 구조입니다.

Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config file to your project - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Visual Studio를 시작하고 솔루션을 엽니다.
1. In the **Solution Explorer**, right-click **[!UICONTROL References]** and select **[!UIUCONTROL Add Reference]**.

1. Select the correct version of the library and browse to the associated `ADBMobile.winmd` file.

   자세한 내용은 아래 올바른 *버전* 선택 섹션을 참조하십시오.

1. **[!UICONTROL 추가를 클릭합니다]**.

1. Verify that `ADBMobile.winmd` is selected in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Windows Phone 앱에 대한 참조를 추가할 때 `ADBMobile.winmd`선택하려면 기본 파일 필터를 구성 요소 파일에서 **[!UICONTROL 모든]** 파일로 **변경하십시오**.

1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 버튼으로 클릭하고 **참조 추가[!UICONTROL 를 선택합니다]**.

   솔루션에 C++ 프로젝트가 있는 경우 이 단계를 건너뛸 수 있습니다.

1. In the Windows tab on the left, select Extensions, then select and add Microsoft Visual C++ 2013 Runtime Package for Windows.************

1. 다음 줄을 클래스에 추가합니다.

   ```
   using ADBMobile;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. 파일을 찾아 `ADBMobileConfig.json` 추가를 **[!UICONTROL 클릭합니다]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. Change **[!UICONTROL Build Action]** to **[!UICONTROL Content]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Visual Studio를 시작하고 솔루션을 엽니다.
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. Select the correct version of the library and then add a reference to the associated `ADBMobile.winmd` file.

   자세한 내용은 아래 올바른 *버전 선택* 섹션을 참조하십시오.

1. **[!UICONTROL 추가를 클릭합니다]**.

1. In the Reference Manager window, verify that  is selected and click OK.****`ADBMobile.winmd`****

   >[!TIP]
   >
   >When adding a reference to a Windows Phone app, to select , change the default file filter from Component Files to All Files.`ADBMobile.winmd`********

1. 다음 줄을 클래스에 추가합니다.

   ```
   using namespace ADMS::Measurement;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. 파일을 `ADBMobileConfig.json` 찾아 추가를 **[!UICONTROL 클릭합니다]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. On the **[!UICONTROL General]** tab, change **[!UICONTROL Content]** to **[!UICONTROL Yes]**, and click **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Visual Studio를 시작하고 솔루션을 엽니다.
1. In the **Solution Explorer**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference**.

   자세한 내용은 아래 올바른 *버전 선택* 섹션을 참조하십시오.

1. Select the correct version of the library and then browse to the associated `ADBMobile.winmd` file.

1. **[!UICONTROL 추가를 클릭합니다]**.

1. Verify that `ADBMobile.winmd` is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Windows Phone 앱에 대한 참조를 추가할 때 `ADBMobile.winmd`선택하려면 기본 파일 필터를 구성 요소 파일에서 **[!UICONTROL 모든]** 파일로 **변경하십시오**.

1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 버튼으로 클릭하고 **참조 추가[!UICONTROL 를 선택합니다]**.

   솔루션에 C++ 프로젝트가 있는 경우 이 단계를 건너뛸 수 있습니다.

1. 왼쪽의 **[!UICONTROL Windows]** 탭에서 **[!UICONTROL 확장을]** 선택하고 Windows용 Microsoft **[!UICONTROL Visual C++ 2013 런타임]**&#x200B;패키지를선택하여 추가합니다.

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. 파일을 `ADBMobileConfig.json` 찾아 추가를 **[!UICONTROL 클릭합니다]**.

1. Right-click the `ADBMobileConfig.json]` file in your solution and select **[!UICONTROL Properties]**.

1. [ **[!UICONTROL 파일 속성]** ]을 선택한 상태에서 [패키지 **[!UICONTROL 작업]** ]을 **[!UICONTROL [컨텐트]로]**&#x200B;설정해야 합니다.

   JavaScript 프로젝트의 경우 기본적으로 파일이 **[!UICONTROL 컨텐츠로]** 설정됩니다.

## Update the ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

The `ADBMobileConfig.json` file contains global SDK settings, and is located at your project root after you complete the steps in the *Add the Library and Config File to your Project* section. If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

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

* **분석**: `rsids` 및 `server`
* **Target**: `clientCode`
* **대상 관리**: `server`

For more details, see [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## 디버깅 {#section_3A10376A60394A15BEE483323E0CD4AA}

SDK에 디버깅을 사용하려면 `ADBMobile.Config.setDebugLogging(true);`);를 호출해야 합니다.

C Sharp 및 JS 앱의 경우 다음 단계를 완료하여 기본 코드 디버깅을 활성화해야 합니다(기본 코드 디버깅은 C++ 앱의 기본 설정).

### C Sharp

Right-click the project, select **[!UICONTROL Properties]** &gt; **[!UICONTROL Debug tab]**. In the debugger drop-down, select Native Only.****

### JS

Right-click the project, select  **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**. 디버거 유형 드롭다운을 **기본**&#x200B;으로 변경합니다.

그러면 됩니다! 이제 Windows 8.1 Universal App Store 앱에서 Analytics, Target 및 고객 관리를 구현할 준비가 되었습니다.
