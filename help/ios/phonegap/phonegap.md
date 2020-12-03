---
description: 이 플러그인을 사용하여 PhoneGap 프로젝트에서 iOS AppMeasurement 호출을 전송할 수 있습니다.
keywords: phonegap
seo-description: 이 플러그인을 사용하여 PhoneGap 프로젝트에서 iOS AppMeasurement 호출을 전송할 수 있습니다.
seo-title: PhoneGap 플러그인
solution: Experience Cloud,Analytics
title: PhoneGap 플러그인
topic: Developer and implementation
uuid: f88bcf10-1f9e-4c97-b348-40db797c9923
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 100%

---


# PhoneGap 플러그인{#phonegap-plug-in}

이 플러그인을 사용하여 PhoneGap 프로젝트에서 iOS AppMeasurement 호출을 전송할 수 있습니다.

## 새로운 Adobe Experience Platform Mobile SDK 릴리스

Adobe Experience Platform Mobile SDK와 관련된 정보 및 설명서를 찾고 계십니까? [여기](https://aep-sdks.gitbook.io/docs/)를 클릭하여 최신 설명서를 확인하십시오.

2018년 9월 일자로 SDK의 새로운 주요 버전을 릴리스하였습니다. 이러한 새로운 Adobe Experience Platform Mobile SDK는 [Experience Platform Launch](https://www.adobe.com/kr/experience-platform/launch.html)를 통해 구성할 수 있습니다.

* 시작하려면 Adobe Experience Platform Launch로 이동합니다.
* Experience Platform SDK 리포지토리의 항목을 보려면 [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)로 이동하십시오.


## PhoneGap 프로젝트 만들기

PhoneGap 프로젝트를 만들려면 [PhoneGap](https://helpx.adobe.com/kr/experience-manager/6-4/mobile/using/phonegap.html)을 참조하십시오.

## npm으로 플러그인 설치: {#section_43229E57C16944C0B51531CB92089189}

1. 다음 명령을 실행합니다.

   ```
   cordova plugin add adobe-mobile-services
   ```

## 수동으로 플러그인 설치 {#section_D53BA60D488C4DB8AD2BDF90439C180A}

### AppMeasurement 라이브러리 포함

AppMeasurement를 포함하려면

1. `ADBMobile_PhoneGap.h`와 `ADBMobile_PhoneGap.m`을 Xcode 프로젝트의 **[!UICONTROL Plugins]** 폴더로 드래그합니다.
1. 다음 설정을 완료합니다.

   1. **[!UICONTROL 대상 그룹의 폴더로 항목 복사를 선택합니다(필요한 경우)]**.
   1. AppMeasurement 코드를 사용할 대상을 선택합니다.

1. `ADB_Helper.js`를 프로젝트의 `www` 폴더로 드래그합니다.
1. `res/xml` 폴더에서 `config.xml`을 열고 다음을 추가하여 새 플러그인을 등록합니다.

   ```
   <feature name="ADBMobile_PhoneGap"> 
     <param name="ios-package" value="ADBMobile_PhoneGap" /> 
   </feature>
   ```

### 앱 권한 추가

AppMeasurement 라이브러리에는 다음이 필요합니다.

1. Xcode IDE를 실행하고 앱을 엽니다.
1. **[!UICONTROL AdobeMobile]** 폴더를 Xcode 프로젝트로 드래그하고 다음 설정을 완료합니다.

   1. **[!UICONTROL 대상 그룹의 폴더로 항목 복사를 선택합니다(필요한 경우)]**.
   1. **[!UICONTROL 추가된 폴더에 대해 그룹 만들기를 선택합니다]**.
   1. AppMeasurement 코드를 사용할 대상을 선택하고 **[!UICONTROL 완료를 클릭합니다]**.

   ![](assets/xcode-settings.png){width=&quot;672&quot;}

1. 프로젝트 타겟의 **[!UICONTROL 빌드 단계]** 탭에서 **[!UICONTROL 바이너리를 라이브러리와 연결]** 섹션을 확장하고 다음 라이브러리를 추가합니다.

   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. 예기치 않은 오류 없이 앱이 빌드되는지 확인합니다.

## 사용자 지정 추적 구현 {#section_FD102B3CDAA4492FB04E56BF17E28663}

추적 기능을 사용할 `html` 파일의 `<head>` 태그에 다음을 추가하십시오.

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

