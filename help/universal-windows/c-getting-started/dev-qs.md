---
description: 'null'
seo-description: 'null'
seo-title: 개발자 빠른 시작
solution: Marketing Cloud,Analytics
title: 개발자 빠른 시작
topic: 개발자 및 구현
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start{#developer-quick-start}

다음은 범용 Windows 플랫폼 라이브러리를 구현하는 방법에 대한 몇 가지 정보입니다.

>[!IMPORTANT]
>
>SDK 파섹

## SDK 가져오기 {#section_99FE1A17A36D4A2C943939023CF6265C}

After you unzip the [SDK download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) file, you will have a separate folder for each supported architecture and platform combination. 또한 `ADBMobileConfig.json` 파일이 있습니다. 이 파일에 대한 자세한 내용은 ADBMobileConfig.json [구성 파일을](/help/universal-windows/c-configuration/c.json.md)참조하십시오.

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll/.winmd` files are provided for each supported architecture (x86, x64, ARM).

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. 이 `.winmd` 파일에는 메타데이터만 들어 있고 버전 번호가 `255.255.255.255`있으며 Microsoft에 따라 허용되는 비헤이비어가 있습니다. 자세한 내용은 WinRT [C++/CX 구성 요소 dll에 대한 어셈블리 정보를 어떻게 추가합니까?를 참조하십시오.](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode) 구문을 사용하는 키-값 쌍으로 전달됩니다. To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## 구문 차이 {#section_A02DE120B6D240F5AFFE7509755C4F14}

Universal Windows Platform 라이브러리는 여러 프로그래밍 언어로 사용할 수 있습니다. 이 안내서의 예는 WinJS(JavaScript)에서 찾을 수 있으며, 다른 언어를 사용하는 경우 수정해야 할 수 있습니다. winJS에서 winmd 메서드를 사용할 경우 모든 메서드는 자동으로 첫 번째 문자를 소문자로 바꿉니다.

구현 간의 주요 차이점은 컨텍스트 데이터에 사용되는 데이터 구조입니다. Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Visual Studio를 시작하고 솔루션을 엽니다.
1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 버튼으로 클릭하고 **참조 추가[!UICONTROL 를 선택합니다]**.

1. 올바른 버전의 라이브러리를 선택하고 연결된 ADBMobile.winmd 파일을 찾습니다.

   자세한 내용은 *이 페이지에서 올바른 버전* 선택 섹션을 참조하십시오.

1. **추가**&#x200B;를 클릭합니다.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 버튼으로 클릭하고 **참조 추가[!UICONTROL 를 선택합니다]**.

   솔루션에 C++ 프로젝트가 있는 경우 이 단계를 건너뜁니다.

1. 왼쪽의 **[!UICONTROL Windows]** 탭에서 확장을 선택하고 **[!UICONTROL Universal Windows 플랫폼 앱용 Visual]** C++ 2015 **[!UICONTROL 런타임을 선택하여 추가합니다]**.

1. 다음 줄을 클래스에 추가합니다.

   ```csharp
   using ADBMobile;
   ```

1. Right-click your project and click **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. 파일을 `ADBMobileConfig.json` 찾아 추가를 **[!UICONTROL 클릭합니다]**.

1. 솔루션의 `ADBMobileConfig.json` 파일을 마우스 오른쪽 버튼으로 클릭하고 속성을 **[!UICONTROL 선택합니다]**.

1. Change **[!UICONTROL Build Action]** to **[!UICONTROL Content]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Visual Studio를 시작하고 솔루션을 엽니다.
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. 올바른 버전의 라이브러리를 선택하고 연결된 ADBMobile.winmd 파일에 참조를 추가합니다.

   For more information, see *Select the correct version* section on this page.

1. **[!UICONTROL 추가를 클릭합니다]**.

1. Verify that `ADBMobile.winmd` is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. 다음 줄을 클래스에 추가합니다.

   ```c++
   using namespace ADBMobile;
   ```

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. On the **[!UICONTROL General]** tab, change **[!UICONTROL Content]** to **[!UICONTROL Yes]** and click **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Visual Studio를 시작하고 솔루션을 엽니다.

1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 버튼으로 클릭하고 **참조 추가[!UICONTROL 를 선택합니다]**.

1. 올바른 버전의 라이브러리를 선택하고 연결된 ADBMobile.winmd 파일을 찾습니다.

1. **[!UICONTROL 추가를 클릭합니다]**.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 버튼으로 클릭하고 **참조 추가[!UICONTROL 를 선택합니다]**.

   If you also have a C++ project in your solution, skip this step.

1. In the Windows tab on the left, select Extensions and select and add Visual C++ 2015 Runtime for Universal Windows Platform Apps.************

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the  file and click Add.`ADBMobileConfig.json`****

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. With **[!UICONTROL File Properties]** selected, ensure **[!UICONTROL Package Action]** is set to **[!UICONTROL Content]**.

   For JavaScript projects, the file is set to Content by default.

## Update The ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

The `ADBMobileConfig.json` file contains global SDK settings and is located at your project root after you complete the steps in the *Add the library and config file to your project* section. If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

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

* **Adobe Analytics**: `rsids` and `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

For more information, see [SDK methods](/help/universal-windows/c-configuration/methods.md).

## 디버깅 {#section_3A10376A60394A15BEE483323E0CD4AA}

To enable debugging for the SDK, call .`ADBMobile.Config.setDebugLogging(true);`

C Sharp 및 JavaScript 앱의 경우 다음 단계를 완료하여 기본 코드 디버깅을 활성화해야 합니다(기본 코드 디버깅은 C++ 앱에 대한 기본 설정).

### C Sharp

1. Right-click the project, click  **[!UICONTROL Properties]** &gt; **[!UICONTROL Debug tab]**.

1. 디버거 유형 드롭다운을 **기본**&#x200B;으로 변경합니다.

### JavaScript

1. Right-click the project, click **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**.

1. 디버거 유형 드롭다운을 **[!UICONTROL 기본으로 변경합니다]**.

그러면 됩니다! 이제 Universal Windows Platform 앱에서 Analytics, Target 및 고객 관리를 구현할 준비가 되었습니다.

