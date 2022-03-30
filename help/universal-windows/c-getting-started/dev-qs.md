---
description: 유니버설 Windows 플랫폼 라이브러리를 구현하는 방법에 대한 정보입니다.
solution: Experience Cloud Services,Analytics
title: 개발자 빠른 시작
topic-fix: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
exl-id: 28fc2a96-907e-41fc-a798-3e8d43fc7616
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 3%

---

# 개발자 빠른 시작{#developer-quick-start}

다음은 Universal Windows Platform 라이브러리를 구현하는 방법에 대한 정보입니다.

>[!IMPORTANT]
>
>SDK를 구현하려면 Visual Studio 2013 이상이 필요합니다.

## SDK 가져오기 {#section_99FE1A17A36D4A2C943939023CF6265C}

압축을 푼 후에 [SDK 다운로드](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) 파일에서는 지원되는 각 아키텍처와 플랫폼 조합에 대해 별도의 폴더가 제공됩니다. 또한 `ADBMobileConfig.json` 파일. 이 파일에 대한 자세한 내용은 [ADBMobileConfig.json 구성 파일](/help/universal-windows/c-configuration/c.json.md).

## 올바른 버전을 선택합니다 {#section_E53C5AA7D5474824A89BB32C003865A1}

다름 `.dll/.winmd` 파일은 지원되는 각 아키텍처(x86, x64, ARM)에 대해 제공됩니다.

>[!IMPORTANT]
>
>버전 `ADBMobile.winmd` 는 라이브러리 버전을 반영하지 않습니다. 다음 `.winmd` 파일에 메타데이터만 들어 있고 버전 번호 `255.255.255.255`: Microsoft에 따라 허용되는 동작입니다. 자세한 내용은 [WinRT C++ / CX 구성 요소 dll에 대한 어셈블리 정보를 추가하려면 어떻게 해야 합니까?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode) 질문에 답합니다. 사용 중인 라이브러리의 버전을 확인하려면 기본 버전의 라이브러리를 확인합니다 `ADBMobile.dll` 파일.

## 구문 차이 {#section_A02DE120B6D240F5AFFE7509755C4F14}

유니버설 Windows 플랫폼 라이브러리는 여러 프로그래밍 언어로 사용할 수 있습니다. 이 안내서의 예는 WinJS(JavaScript)에서 다른 언어를 사용하는 경우 을 수정해야 할 수 있습니다. winJS에서 winmd 메서드를 사용하면 모든 메서드가 자동으로 첫 번째 문자를 소문자로 바꿉니다.

구현 간의 주요 차이점은 컨텍스트 데이터에 사용되는 데이터 구조입니다. 또한 WinJS 프로젝트에서 SDK를 사용할 때는 빈 문자열( `""` 또는 `''`) 대신 `null` 를 반환합니다.

## 프로젝트에 라이브러리 및 구성 파일 추가 - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Visual Studio를 실행하고 솔루션을 엽니다.
1. 에서 **[!UICONTROL 솔루션 탐색기]**, 마우스 오른쪽 단추 클릭 **[!UICONTROL 참조]** 을(를) 선택합니다. **[!UICONTROL 참조 추가]**.

1. 라이브러리의 올바른 버전을 선택하고 관련 ADBMobile.winmd 파일을 찾습니다.

   자세한 내용은 *올바른 버전을 선택합니다* 섹션을 참조하십시오.

1. **추가를 클릭합니다**.

1. ADBMobile.winmd 파일이 **[!UICONTROL 참조 관리자]** 을(를) 클릭하고 **[!UICONTROL 확인]**.

1. 에서 **[!UICONTROL 솔루션 탐색기]**, 마우스 오른쪽 단추 클릭 **[!UICONTROL 참조]** 을(를) 선택합니다. **[!UICONTROL 참조 추가]**.

   솔루션에 C++ 프로젝트도 있는 경우 이 단계를 건너뜁니다.

1. 에서 **[!UICONTROL Windows]** 왼쪽의 탭에서 을 선택합니다. **[!UICONTROL 확장]**, 선택 및 추가 **[!UICONTROL 유니버설 Windows 플랫폼 앱용 Visual C++ 2015 런타임]**.

1. 다음 줄을 클래스에 추가합니다.

   ```csharp
   using ADBMobile;
   ```

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 추가]** > **[!UICONTROL 기존 항목]**.

1. 다음 위치로 이동합니다. `ADBMobileConfig.json` 를 클릭하고 **[!UICONTROL 추가]**.

1. 을(를) 마우스 오른쪽 단추로 클릭합니다. `ADBMobileConfig.json` 파일에 파일을 넣고 **[!UICONTROL 속성]**.

1. 변경 **[!UICONTROL 빌드 작업]** to **[!UICONTROL 컨텐츠]**.

## 프로젝트에 라이브러리 및 구성 파일 추가 - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Visual Studio를 실행하고 솔루션을 엽니다.
1. 에서 **[!UICONTROL 솔루션 탐색기]**&#x200B;를 클릭하고 프로젝트를 마우스 오른쪽 단추로 클릭한 다음 을 선택합니다. **[!UICONTROL 추가]** > **[!UICONTROL 참조]**.

1. 라이브러리의 올바른 버전을 선택하고 연결된 ADBMobile.winmd 파일에 참조를 추가합니다.

   자세한 내용은 *올바른 버전을 선택합니다* 섹션을 참조하십시오.

1. **[!UICONTROL 추가를 클릭합니다]**.

1. 확인 `ADBMobile.winmd` 체크 인 **[!UICONTROL 참조 관리자]** 을(를) 클릭하고 **[!UICONTROL 확인]**.

1. 다음 줄을 클래스에 추가합니다.

   ```c++
   using namespace ADBMobile;
   ```

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 를 선택합니다 **[!UICONTROL 추가]** > **[!UICONTROL 기존 항목]**.

1. 찾아보기 `ADBMobileConfig.json` 를 클릭하고 **[!UICONTROL 추가]**.

1. 마우스 오른쪽 단추를 클릭합니다. `ADBMobileConfig.json` 파일에 파일을 넣고 **[!UICONTROL 속성]**.

1. 설정 **[!UICONTROL 일반]** 탭, 변경 **[!UICONTROL 컨텐츠]** to **[!UICONTROL 예]** 을(를) 클릭합니다. **[!UICONTROL 확인]**.

## 프로젝트에 라이브러리 및 구성 파일 추가 - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Visual Studio를 실행하고 솔루션을 엽니다.

1. 에서 **[!UICONTROL 솔루션 탐색기]**, 마우스 오른쪽 단추 클릭 **[!UICONTROL 참조]** 을(를) 선택합니다. **[!UICONTROL 참조 추가]**.

1. 라이브러리의 올바른 버전을 선택하고 관련 ADBMobile.winmd 파일을 찾습니다.

1. **[!UICONTROL 추가를 클릭합니다]**.

1. ADBMobile.winmd 파일이 **[!UICONTROL 참조 관리자]** 을(를) 클릭하고 **[!UICONTROL 확인]**.

1. 에서 **[!UICONTROL 솔루션 탐색기]**, 마우스 오른쪽 단추 클릭 **[!UICONTROL 참조]** 을(를) 선택합니다. **[!UICONTROL 참조 추가]**.

   솔루션에 C++ 프로젝트도 있는 경우 이 단계를 건너뜁니다.

1. 에서 **[!UICONTROL Windows]** 왼쪽의 탭에서 을 선택합니다. **[!UICONTROL 확장]** 을(를) 선택하고 추가합니다. **[!UICONTROL 유니버설 Windows 플랫폼 앱용 Visual C++ 2015 런타임]**.

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 를 선택합니다 **[!UICONTROL 추가]** > **[!UICONTROL 기존 항목]**.

1. 다음 위치로 이동합니다. `ADBMobileConfig.json` 를 클릭하고 **[!UICONTROL 추가]**.

1. 마우스 오른쪽 단추를 클릭합니다. `ADBMobileConfig.json` 파일에 파일을 넣고 **[!UICONTROL 속성]**.

1. 사용 **[!UICONTROL 파일 속성]** 선택, 확인 **[!UICONTROL 패키지 작업]** 가 로 설정되어 있습니다. **[!UICONTROL 컨텐츠]**.

   JavaScript 프로젝트의 경우 기본적으로 파일이 콘텐츠 로 설정됩니다.

## ADBMobileConfig.json 구성 파일 업데이트 {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

다음 `ADBMobileConfig.json` 파일에는 글로벌 SDK 설정이 포함되어 있으며, *프로젝트에 라이브러리 및 구성 파일 추가* 섹션을 참조하십시오. 만약 `ADBMobileConfig.json` Mobile 서비스 Adobe이 파일을 미리 구성하지 않았으므로 시작하려면 몇 가지 값을 업데이트해야 합니다.

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

* **Adobe Analytics**: `rsids` 및 `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

자세한 내용은 [SDK 메서드](/help/universal-windows/c-configuration/methods.md).

## 디버깅 {#section_3A10376A60394A15BEE483323E0CD4AA}

SDK에 대한 디버깅을 활성화하려면 `ADBMobile.Config.setDebugLogging(true);`.

C Sharp 및 JavaScript 앱의 경우 다음 단계를 완료하여 네이티브 코드 디버깅을 활성화해야 합니다(기본 코드 디버깅은 C++ 앱의 기본 설정).

### C 샤프

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고  **[!UICONTROL 속성]** > **[!UICONTROL 디버그 탭]**.

1. 디버거 유형 드롭다운을 로 변경합니다. **네이티브 전용**.

### JavaScript

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 속성]** > **[!UICONTROL 구성 속성]** > **[!UICONTROL 디버그 탭]**.

1. 디버거 유형 드롭다운을 로 변경합니다. **[!UICONTROL 네이티브 전용]**.

됐습니다. 이제 유니버설 Windows 플랫폼 앱에서 Analytics, Target 및 고객 관리를 구현할 준비가 되었습니다.
