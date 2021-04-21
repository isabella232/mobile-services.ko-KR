---
description: 유니버설 Windows 플랫폼 라이브러리를 구현하는 방법에 대한 정보입니다.
solution: Experience Cloud,Analytics
title: 개발자 빠른 시작
topic-fix: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
exl-id: 28fc2a96-907e-41fc-a798-3e8d43fc7616
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 3%

---

# 개발자 빠른 시작{#developer-quick-start}

다음은 범용 Windows 플랫폼 라이브러리를 구현하는 방법에 대한 몇 가지 정보입니다.

>[!IMPORTANT]
>
>SDK를 구현하려면 Visual Studio 2013 이상이 필요합니다.

## SDK {#section_99FE1A17A36D4A2C943939023CF6265C} 가져오기

[SDK 다운로드](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) 파일의 압축을 풀면 지원되는 각 아키텍처 및 플랫폼 조합에 대해 별도의 폴더를 갖게 됩니다. `ADBMobileConfig.json` 파일도 있습니다. 이 파일에 대한 자세한 내용은 [ADBMobileConfig.json 구성 파일](/help/universal-windows/c-configuration/c.json.md)을 참조하십시오.

## 올바른 버전 {#section_E53C5AA7D5474824A89BB32C003865A1} 선택

지원되는 각 아키텍처(x86, x64, ARM)에 대해 서로 다른 `.dll/.winmd` 파일이 제공됩니다.

>[!IMPORTANT]
>
>`ADBMobile.winmd` 버전은 라이브러리 버전을 반영하지 않습니다. `.winmd` 파일에는 메타데이터만 들어 있으며 Microsoft에 따라 허용되는 비헤이비어의 `255.255.255.255` 버전 번호가 있습니다. 자세한 내용은 [WinRT C++/CX 구성 요소 dll에 대한 어셈블리 정보를 어떻게 추가합니까?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode) 질문에 답합니다. 사용 중인 라이브러리 버전을 확인하려면 기본 `ADBMobile.dll` 파일의 버전을 확인하십시오.

## 구문 차이 {#section_A02DE120B6D240F5AFFE7509755C4F14}

유니버설 Windows 플랫폼 라이브러리는 여러 프로그래밍 언어에서 사용할 수 있습니다. 이 안내서의 예는 WinJS(JavaScript)에서 다른 언어를 사용하는 경우 수정해야 할 수 있습니다. winJS에서 winmd 메서드를 사용하면 모든 메서드에서 첫 번째 문자가 자동으로 소문자로 바뀝니다.

구현 간의 주요 차이점은 컨텍스트 데이터에 사용되는 데이터 구조입니다. 또한 WinJS 프로젝트에서 SDK를 사용할 때는 빈 문자열 값에 대해 `null` 대신 빈 문자열( `""` 또는 `''`)을 사용하십시오.

## 프로젝트에 라이브러리 및 구성 파일 추가 - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Visual Studio를 실행하고 솔루션을 엽니다.
1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 참조 추가]**&#x200B;를 선택합니다.

1. 올바른 버전의 라이브러리를 선택하고 연결된 ADBMobile.winmd 파일을 찾습니다.

   자세한 내용은 이 페이지에서 *올바른 버전* 섹션 선택을 참조하십시오.

1. **추가를 클릭합니다**.

1. ADBMobile.winmd 파일이 **[!UICONTROL 참조 관리자]** 창에서 체크 인되었는지 확인하고 **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 참조 추가]**&#x200B;를 선택합니다.

   솔루션에 C++ 프로젝트도 있는 경우 이 단계를 건너뛰십시오.

1. 왼쪽의 **[!UICONTROL Windows]** 탭에서 **[!UICONTROL 확장]**&#x200B;을 선택하고 **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows 플랫폼 앱]**&#x200B;을 선택하고 추가합니다.

1. 다음 줄을 클래스에 추가합니다.

   ```csharp
   using ADBMobile;
   ```

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 추가]** > **[!UICONTROL 기존 항목]**&#x200B;을 클릭합니다.

1. `ADBMobileConfig.json` 파일을 탐색하고 **[!UICONTROL 추가]**&#x200B;를 클릭합니다.

1. 솔루션에서 `ADBMobileConfig.json` 파일을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 속성]**&#x200B;을 선택합니다.

1. **[!UICONTROL 빌드 작업]**&#x200B;을 **[!UICONTROL 컨텐트]**&#x200B;로 변경합니다.

## 프로젝트에 라이브러리 및 구성 파일 추가 - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Visual Studio를 실행하고 솔루션을 엽니다.
1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 추가]** > **[!UICONTROL 참조]**&#x200B;를 선택합니다.

1. 올바른 버전의 라이브러리를 선택하고 관련 ADBMobile.winmd 파일에 대한 참조를 추가합니다.

   자세한 내용은 이 페이지에서 *올바른 버전* 섹션 선택을 참조하십시오.

1. **[!UICONTROL 추가를 클릭합니다]**.

1. `ADBMobile.winmd`참조 관리자&#x200B;]**창에서**[!UICONTROL &#x200B;이(가) 선택되었는지 확인하고 **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

1. 다음 줄을 클래스에 추가합니다.

   ```c++
   using namespace ADBMobile;
   ```

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 추가]** > **[!UICONTROL 기존 항목]**&#x200B;을 선택합니다.

1. `ADBMobileConfig.json` 파일을 찾아 **[!UICONTROL 추가]**&#x200B;를 클릭합니다.

1. 솔루션에서 `ADBMobileConfig.json` 파일을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 속성]**&#x200B;을 선택합니다.

1. **[!UICONTROL 일반]** 탭에서 **[!UICONTROL 컨텐트]**&#x200B;를 **[!UICONTROL 예]**&#x200B;로 변경하고 **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

## 프로젝트에 라이브러리 및 구성 파일 추가 - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Visual Studio를 실행하고 솔루션을 엽니다.

1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 참조 추가]**&#x200B;를 선택합니다.

1. 올바른 버전의 라이브러리를 선택하고 연결된 ADBMobile.winmd 파일을 찾습니다.

1. **[!UICONTROL 추가를 클릭합니다]**.

1. ADBMobile.winmd 파일이 **[!UICONTROL 참조 관리자]** 창에서 체크 인되었는지 확인하고 **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 참조 추가]**&#x200B;를 선택합니다.

   솔루션에 C++ 프로젝트도 있는 경우 이 단계를 건너뛰십시오.

1. 왼쪽의 **[!UICONTROL Windows]** 탭에서 **[!UICONTROL 확장]**&#x200B;을 선택하고 **[!UICONTROL 유니버설 Windows 플랫폼 앱용 Visual C++ 2015 런타임]**&#x200B;을 선택하고 추가합니다.

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 추가]** > **[!UICONTROL 기존 항목]**&#x200B;을 선택합니다.

1. `ADBMobileConfig.json` 파일을 탐색하고 **[!UICONTROL 추가]**&#x200B;를 클릭합니다.

1. 솔루션에서 `ADBMobileConfig.json` 파일을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 속성]**&#x200B;을 선택합니다.

1. **[!UICONTROL 파일 속성]**&#x200B;이 선택된 상태에서 **[!UICONTROL 패키지 작업]**&#x200B;이 **[!UICONTROL 컨텐트]**&#x200B;로 설정되어 있는지 확인합니다.

   JavaScript 프로젝트의 경우 기본적으로 파일이 컨텐츠로 설정됩니다.

## ADBMobileConfig.json 구성 파일 {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE} 업데이트

`ADBMobileConfig.json` 파일은 전역 SDK 설정을 포함하며 *프로젝트* 섹션에 라이브러리 및 구성 파일을 추가하는 단계를 완료한 후 프로젝트 루트에 있습니다. Adobe Mobile Services에서 `ADBMobileConfig.json` 파일을 미리 구성하지 않은 경우 시작하려면 몇 개의 값을 업데이트해야 합니다.

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

* **Adobe Analytics**: `rsids` and  `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

자세한 내용은 [SDK 메서드](/help/universal-windows/c-configuration/methods.md)를 참조하십시오.

## 디버깅 {#section_3A10376A60394A15BEE483323E0CD4AA}

SDK에 대한 디버깅을 사용하려면 `ADBMobile.Config.setDebugLogging(true);`을(를) 호출합니다.

C Sharp 및 JavaScript 앱의 경우 다음 단계를 완료하여 기본 코드 디버깅을 활성화해야 합니다(기본 코드 디버깅은 C++ 앱의 기본 설정).

### C 샤프

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 속성]** > **[!UICONTROL 디버그 탭]**&#x200B;을 클릭합니다.

1. 디버거 유형 드롭다운을 **기본 전용**&#x200B;으로 변경합니다.

### JavaScript

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 속성]** > **[!UICONTROL 구성 속성]** > **[!UICONTROL 디버그 탭]**&#x200B;을 클릭합니다.

1. 디버거 유형 드롭다운을 **[!UICONTROL 기본 전용]**&#x200B;으로 변경합니다.

됐습니다. 이제 유니버설 Windows 플랫폼 앱에서 분석, Target 및 고객 관리를 구현할 준비가 되었습니다.
