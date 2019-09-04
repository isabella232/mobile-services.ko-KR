---
description: 'null'
seo-description: 'null'
seo-title: 개발자 빠른 시작
solution: Marketing Cloud, Analytics
title: 개발자 빠른 시작
topic: 개발자 및 구현
uuid: 11 c 06 fcf-d 5 e 4-4858-9 a 4 e -3 bf 66 cdd 2 a 48
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start{#developer-quick-start}

다음은 유니버설 Windows 플랫폼 라이브러리를 구현하는 방법에 대한 몇 가지 정보입니다.

>[!IMPORTANT]
>
>SDK를 구현하려면 Visual Studio 2013 이상이 필요합니다.

## SDK 가져오기 {#section_99FE1A17A36D4A2C943939023CF6265C}

[SDK 다운로드](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) 파일의 압축을 풀면 지원되는 각 아키텍처 및 플랫폼 조합에 대해 별도의 폴더가 생깁니다. 또한 파일이 있어야 합니다. `ADBMobileConfig.json` 이 파일에 대한 자세한 내용은 [Adbmobileconfig. json 구성 파일을 참조하십시오](/help/universal-windows/c-configuration/c.json.md).

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll/.winmd` files are provided for each supported architecture (x86, x64, ARM).

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. `.winmd` 이 파일에는 메타데이터만 포함되어 있으며 Microsoft에 `255.255.255.255`따라 허용되는 비헤이비어인 버전 번호가 있습니다. 자세한 내용은 Winrt C + +/CX [구성 요소 DLL에 대한 어셈블리 정보를 추가하는 방법을 참조하십시오.](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode) 구문을 사용하는 키-값 쌍으로 전달됩니다. To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## 구문 차이 {#section_A02DE120B6D240F5AFFE7509755C4F14}

Universal Windows Platform 라이브러리는 여러 프로그래밍 언어로 사용할 수 있습니다. 다른 언어를 사용하는 경우 이 안내서의 예제를 Winjs (JavaScript) 에 수정해야 할 수 있습니다. Winjs에서 winmd 메서드를 사용하는 경우 모든 메서드에는 첫 번째 문자가 밑줄로 표시됩니다.

구현 간의 주요 차이점은 컨텍스트 데이터에 사용되는 데이터 구조입니다. Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Visual Studio를 시작하고 솔루션을 엽니다.
1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 버튼으로 클릭하고 **참조 추가[!UICONTROL 를 선택합니다]**.

1. 라이브러리의 올바른 버전을 선택하고 연결된 Adbmobile. winmd 파일을 탐색합니다.

   자세한 내용은 이 페이지에서 *올바른 버전* 섹션 선택을 참조하십시오.

1. **추가**&#x200B;를 클릭합니다.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 버튼으로 클릭하고 **참조 추가[!UICONTROL 를 선택합니다]**.

   솔루션에 C + + 프로젝트가 있는 경우 이 단계를 건너뜁니다.

1. 왼쪽의 **[!UICONTROL Windows]** 탭에서 **[!UICONTROL 확장 기능을]**&#x200B;선택하고 Universal Windows 플랫폼 앱에 **[!UICONTROL 대해 Visual C + + 2015 런타임을 선택합니다]**.

1. 다음 줄을 클래스에 추가합니다.

   ```csharp
   using ADBMobile;
   ```

1. Right-click your project and click **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. `ADBMobileConfig.json` 파일을 찾아 ****&#x200B;추가를 클릭합니다.

1. 솔루션에서 `ADBMobileConfig.json` 파일을 마우스 오른쪽 버튼으로 클릭하고 **[!UICONTROL 속성을 선택합니다]**.

1. **[!UICONTROL 빌드 작업을]** 콘텐츠로 ****&#x200B;변경

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Visual Studio를 시작하고 솔루션을 엽니다.
1. **[!UICONTROL 솔루션 탐색기에서]**&#x200B;프로젝트를 마우스 오른쪽 버튼으로 클릭하고 **[!UICONTROL 추가]** &gt; **[!UICONTROL 참조를 선택합니다]**.

1. 라이브러리의 올바른 버전을 선택하고 연결된 Adbmobile. winmd 파일에 참조를 추가합니다.

   자세한 내용은 이 페이지에서 *올바른 버전* 섹션 선택을 참조하십시오.

1. **[!UICONTROL 추가를 클릭합니다]**.

1. Verify that `ADBMobile.winmd` is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. 다음 줄을 클래스에 추가합니다.

   ```c++
   using namespace ADBMobile;
   ```

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. `ADBMobileConfig.json` 파일을 찾아 ****&#x200B;추가를 클릭합니다.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. **[!UICONTROL 일반]** 탭에서 **[!UICONTROL 컨텐츠를]** **[!UICONTROL 예로]** 변경하고 **[!UICONTROL 확인을]**&#x200B;클릭합니다.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Visual Studio를 시작하고 솔루션을 엽니다.

1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 버튼으로 클릭하고 **참조 추가[!UICONTROL 를 선택합니다]**.

1. 라이브러리의 올바른 버전을 선택하고 연결된 Adbmobile. winmd 파일을 탐색합니다.

1. **[!UICONTROL 추가를 클릭합니다]**.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 버튼으로 클릭하고 **참조 추가[!UICONTROL 를 선택합니다]**.

   솔루션에 C + + 프로젝트가 있는 경우 이 단계를 건너뜁니다.

1. 왼쪽의 **[!UICONTROL Windows]** 탭에서 **[!UICONTROL 확장 기능을]** 선택하고 Universal Windows 플랫폼 앱에 **[!UICONTROL 대해 Visual C + + 2015 런타임을 선택합니다]**.

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. `ADBMobileConfig.json` 파일을 찾아 ****&#x200B;추가를 클릭합니다.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. **[!UICONTROL 파일 속성을]** 선택한 상태에서 **[!UICONTROL 패키지 작업이]** 콘텐츠로 **[!UICONTROL 설정되어 있는지]**&#x200B;확인합니다.

   JavaScript 프로젝트의 경우 기본적으로 파일이 [콘텐트] 로 설정됩니다.

## Update The ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

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

최소한 사용 중인 솔루션에 대해 다음 값을 업데이트합니다.

* **Adobe Analytics**: `rsids` and `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

자세한 내용은 [SDK 메서드를](/help/universal-windows/c-configuration/methods.md)참조하십시오.

## 디버깅 {#section_3A10376A60394A15BEE483323E0CD4AA}

SDK에 대한 디버깅을 활성화하려면을 호출합니다 `ADBMobile.Config.setDebugLogging(true);`.

C Sharp 및 JavaScript 앱의 경우 다음 단계를 완료하여 기본 코드 디버깅을 활성화해야 합니다. 기본 코드 디버깅은 C + + 앱에 대한 기본 설정입니다.

### C Sharp

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 속성]** &gt; **[!UICONTROL 디버그 탭을]**&#x200B;클릭합니다.

1. 디버거 유형 드롭다운을 **기본**&#x200B;으로 변경합니다.

### JavaScript

1. Right-click the project, click **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**.

1. 디버거 유형 드롭다운을 **[!UICONTROL 기본으로 변경합니다]**.

그러면 됩니다! 이제 Universal Windows Platform 앱에서 Analytics, Target 및 고객 관리를 구현할 준비가 되었습니다.

