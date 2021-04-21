---
description: 개발자 빠른 시작 문서
solution: Experience Cloud,Analytics
title: 개발자 빠른 시작
topic-fix: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
exl-id: dd3262b1-e211-4758-9b4a-9dc7c4920c10
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 2%

---

# 개발자 빠른 시작 {#developer-quick-start}

SDK를 구현하려면 Visual Studio 2013 이상이 필요합니다.

## SDK {#section_99FE1A17A36D4A2C943939023CF6265C} 가져오기

[SDK 다운로드](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)의 압축을 풀면 지원되는 각 아키텍처 및 플랫폼 조합에 대해 별도의 폴더를 갖게 됩니다. 이 안내서의 뒷부분에 있는 `ADBMobileConfig.json` 파일도 있습니다.

## 올바른 버전 {#section_E53C5AA7D5474824A89BB32C003865A1} 선택

각 대상 플랫폼(Windows 8.1, Windows Phone 8.1)과 지원되는 아키텍처(x86, x64, ARM)에 대해 서로 다른 `.dll`/ `.winmd` 파일이 제공됩니다. 파일은 다음과 같이 폴더 구조로 분리됩니다.

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>`ADBMobile.winmd` 버전은 라이브러리 버전을 반영하지 않습니다. `.winmd` 파일에는 메타데이터만 들어 있으며, 이와 같이 Microsoft에 따라 허용되는 비헤이비어의 `255.255.255.255` 버전 번호가 지정됩니다( [WinRT C++ / CX 구성 요소 dll에 대한 어셈블리 정보를 추가하려면 어떻게 합니까?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode) 참조). 사용 중인 라이브러리 버전을 확인하려면 기본 `ADBMobile.dll` 파일의 버전을 확인하십시오.

## 구문 차이 {#section_A02DE120B6D240F5AFFE7509755C4F14}

Windows 8.1 Universal App Store 라이브러리는 여러 프로그래밍 언어에서 사용할 수 있습니다. 이 안내서의 예는 WinJS(JavaScript)에 있으며 다른 언어를 사용하는 경우 수정해야 할 수 있습니다. winJS(JavaScript)에서 winmd 메서드를 사용하는 경우 모든 메서드는 자동으로 첫 번째 문자를 소문자로 바꿉니다.

구현 간의 주요 차이점은 컨텍스트 데이터에 사용되는 데이터 구조입니다.

또한 WinJS 프로젝트에서 SDK를 사용할 때는 빈 문자열 값에 대해 `null` 대신 빈 문자열( `""` 또는 `''`)을 사용하십시오.

## 프로젝트에 라이브러리 및 구성 파일 추가 - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Visual Studio를 실행하고 솔루션을 엽니다.
1. **솔루션 탐색기**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 참조 추가]**&#x200B;를 선택합니다.

1. 올바른 버전의 라이브러리를 선택하고 연결된 `ADBMobile.winmd` 파일을 찾습니다.

   자세한 내용은 아래의 *올바른 버전* 섹션 선택을 참조하십시오.

1. **[!UICONTROL 추가를 클릭합니다]**.

1. `ADBMobile.winmd`참조 관리자&#x200B;]**창에서**[!UICONTROL &#x200B;이 선택되었는지 확인하고 **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

   >[!NOTE]
   >
   >Windows Phone 앱에 참조를 추가할 때 `ADBMobile.winmd`을 선택하려면 기본 파일 필터를 **[!UICONTROL 구성 요소 파일]**&#x200B;에서 **모든 파일**&#x200B;로 변경하십시오.

1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 참조 추가]**&#x200B;를 선택합니다.

   솔루션에 C++ 프로젝트도 있는 경우 이 단계를 건너뛸 수 있습니다.

1. 왼쪽의 **Windows** 탭에서 **[!UICONTROL 확장]**&#x200B;을 선택한 다음 **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**&#x200B;를 선택하고 추가합니다.

1. 다음 줄을 클래스에 추가합니다.

   ```
   using ADBMobile;
   ```

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 추가]** > **[!UICONTROL 기존 항목]**&#x200B;을 선택합니다.

1. `ADBMobileConfig.json` 파일을 찾아 **[!UICONTROL 추가]**&#x200B;를 클릭합니다.

1. 솔루션에서 `ADBMobileConfig.json` 파일을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 속성]**&#x200B;을 선택합니다.

1. **[!UICONTROL 빌드 작업]**&#x200B;을 **[!UICONTROL 컨텐트]**&#x200B;로 변경합니다.

## 프로젝트에 라이브러리 및 구성 파일 추가 - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Visual Studio를 실행하고 솔루션을 엽니다.
1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 추가]** > **[!UICONTROL 참조]**&#x200B;를 선택합니다.

1. 올바른 버전의 라이브러리를 선택한 다음 연결된 `ADBMobile.winmd` 파일에 참조를 추가합니다.

   자세한 내용은 아래의 *올바른 버전 선택* 섹션을 참조하십시오.

1. **[!UICONTROL 추가를 클릭합니다]**.

1. **[!UICONTROL 참조 관리자]** 창에서 `ADBMobile.winmd`가 선택되었는지 확인하고 **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

   >[!TIP]
   >
   >Windows Phone 앱에 참조를 추가할 때 `ADBMobile.winmd`을 선택하려면 기본 파일 필터를 **[!UICONTROL 구성 요소 파일]**&#x200B;에서 **모든 파일**&#x200B;로 변경하십시오.

1. 다음 줄을 클래스에 추가합니다.

   ```
   using namespace ADMS::Measurement;
   ```

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 추가]** > **[!UICONTROL 기존 항목]**&#x200B;을 선택합니다.

1. `ADBMobileConfig.json` 파일을 탐색하고 **[!UICONTROL 추가]**&#x200B;를 클릭합니다.

1. 솔루션에서 `ADBMobileConfig.json` 파일을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 속성]**&#x200B;을 선택합니다.

1. **[!UICONTROL 일반]** 탭에서 **[!UICONTROL 컨텐트]**&#x200B;를 **[!UICONTROL 예]**&#x200B;로 변경하고 **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

## 프로젝트에 라이브러리 및 구성 파일 추가 - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Visual Studio를 실행하고 솔루션을 엽니다.
1. **솔루션 탐색기**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 참조 추가]**&#x200B;를 선택합니다.

   자세한 내용은 아래의 *올바른 버전* 섹션 선택을 참조하십시오.

1. 올바른 버전의 라이브러리를 선택한 다음 연결된 `ADBMobile.winmd` 파일을 찾습니다.

1. **[!UICONTROL 추가를 클릭합니다]**.

1. `ADBMobile.winmd`참조 관리자&#x200B;]**창에서**[!UICONTROL &#x200B;이(가) 선택되었는지 확인하고 **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

   >[!TIP]
   >
   >Windows Phone 앱에 참조를 추가할 때 `ADBMobile.winmd`을 선택하려면 기본 파일 필터를 **[!UICONTROL 구성 요소 파일]**&#x200B;에서 **모든 파일**&#x200B;로 변경하십시오.

1. **[!UICONTROL 솔루션 탐색기]**&#x200B;에서 **[!UICONTROL 참조]**&#x200B;를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 참조 추가]**&#x200B;를 선택합니다.

   솔루션에 C++ 프로젝트도 있는 경우 이 단계를 건너뛸 수 있습니다.

1. 왼쪽의 **[!UICONTROL Windows]** 탭에서 **[!UICONTROL Extensions]**&#x200B;을 선택하고 **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**&#x200B;를 선택하여 추가합니다.

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 추가]** > **[!UICONTROL 기존 항목]**&#x200B;을 선택합니다.

1. `ADBMobileConfig.json` 파일을 탐색하고 **[!UICONTROL 추가]**&#x200B;를 클릭합니다.

1. 솔루션에서 `ADBMobileConfig.json]` 파일을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 속성]**&#x200B;을 선택합니다.

1. **[!UICONTROL 파일 속성]**&#x200B;이 선택된 상태에서 **[!UICONTROL 패키지 작업]**&#x200B;이 **[!UICONTROL 컨텐트]**&#x200B;로 설정되어 있는지 확인합니다.

   JavaScript 프로젝트의 경우 기본적으로 파일이 **[!UICONTROL Content]**&#x200B;로 설정됩니다.

## ADBMobileConfig.json 구성 파일 {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE} 업데이트

`ADBMobileConfig.json` 파일은 전역 SDK 설정을 포함하며 *프로젝트* 섹션에 라이브러리 및 구성 파일 추가 단계를 완료한 후 프로젝트 루트에 있습니다. Adobe Mobile Services에서 `ADBMobileConfig.json` 파일을 미리 구성하지 않은 경우 시작하려면 몇 개의 값을 업데이트해야 합니다.

다음은 `ADBMobileConfig.json` 파일의 예입니다.

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

* **분석**: `rsids` and  `server`
* **Target**: `clientCode`
* **대상 관리**: `server`

자세한 내용은 [ADBMobileConfig.json 구성](/help/windows-appstore/c-configuration/methods.md)을 참조하십시오.

## 디버깅 {#section_3A10376A60394A15BEE483323E0CD4AA}

SDK에 대한 디버깅을 활성화하려면 `ADBMobile.Config.setDebugLogging(true);`을(를) 호출해야 합니다.

C Sharp 및 JS 앱의 경우 다음 단계를 완료하여 기본 코드 디버깅을 활성화해야 합니다(기본 코드 디버깅은 C++ 앱의 기본 설정).

### C 샤프

프로젝트를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 속성]** > **[!UICONTROL 디버그 탭]**&#x200B;을 선택합니다. 디버거 드롭다운에서 **[!UICONTROL 기본 전용]**&#x200B;을 선택합니다.

### JS

프로젝트를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 속성]** > **[!UICONTROL 구성 속성]** > **[!UICONTROL 디버그 탭]**&#x200B;을 선택합니다. 디버거 유형 드롭다운을 **기본 전용**&#x200B;으로 변경합니다.

됐습니다. 이제 Windows 8.1 유니버설 앱 스토어 앱에서 분석, Target 및 고객 관리를 구현할 준비가 되었습니다.
