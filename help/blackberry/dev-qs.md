---
title: 개발자 빠른 시작
seo-title: Adobe 모바일 서비스를 위한 BlackBerry Developer Quick Start
description: BlackBerry 개발자 빠른 시작 안내서는 Adobe 모바일 서비스용 BlackBerry 라이브러리를 구현하는 프로세스를 파악하는 데 도움이 됩니다.
seo-description: BlackBerry 개발자 빠른 시작 안내서는 Adobe 모바일 서비스용 BlackBerry 라이브러리를 구현하는 프로세스를 파악하는 데 도움이 됩니다.
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 1%

---


# 개발자 빠른 시작

이 정보는 BlackBerry 라이브러리를 구현하는 프로세스를 이해하는 데 도움이 됩니다.

## SDK 다운로드

**SDK를 사용하려면 BlackBerry 10 이상이 필요합니다.**

다운로드한 SDK의 압축을 푼 후 다음 파일이 `AdobeMobile` 폴더에 있는지 확인합니다.

* `Device-Coverage/libADBMobileShared.so`
* `Device-Debug/libADBMobileShared.so`
* `Device-Profile/libADBMobileShared.so`
* `Device-Release/libADBMobileShared.so`
* `public/ADBMediaAnalytics.hpp`
* `public/ADBMediaSharedHeader.hpp`
* `public/ADBMediaState.hpp`
* `public/ADBMobile.hpp`
* `Simulator-Coverage/libADBMobileShared.so`
* `Simulator-Debug/libADBMobileShared.so`
* `Simulator-Profile/libADBMobileShared.so`

## 프로젝트에 SDK 추가

1. 프로젝트를 마우스 오른쪽 버튼으로 클릭하고 구성 **[!UICONTROL > 라이브러리]** **[!UICONTROL 추가]**&#x200B;를 선택합니다.
1. [ **[!UICONTROL 외부 라이브러리]** ]를 선택하고 [다음]을 **[!UICONTROL 클릭합니다]**.
1. 장치 **[!UICONTROL 라이브러리]** 필드 옆에 있는 **[!UICONTROL 찾아보기를]** 클릭합니다.
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. 폴더에서 `Device-Debug` 를 선택하고 열기 `libADBMobileShared.so` 를 **[!UICONTROL 클릭합니다]**.
1. 시뮬레이터 **[!UICONTROL 라이브러리]** 필드 옆에 있는 **[!UICONTROL 찾아보기를]** 클릭합니다.
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. 폴더에서 `Device-Debug` 를 선택하고 열기 `libADBMobileShared.so` 를 **[!UICONTROL 클릭합니다]**.
1. 폴더 **[!UICONTROL 포함]** 필드 옆에 있는 **[!UICONTROL 추가를]** 클릭합니다.
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. 포함에 `public` 폴더를 추가합니다.
1. 폴더 `ADBMobile-4.0.0BETA-BlackBerry` 에 이름이 `.json` 있는 구성 파일이 있습니다 `ADBMobileConfig.json`.

   프로젝트의 루트에 해당 파일을 복사합니다.
1. 프로젝트를 마우스 오른쪽 버튼으로 클릭하고 새로 **[!UICONTROL 고침을 선택합니다]**.

   이제 프로젝트 `.json` 탐색기에서 **[!UICONTROL 파일이 표시됩니다]**.
1. 프로젝트의 `bar-descriptor.xml` 파일을 엽니다.
1. 창 하단에서 자산 **[!UICONTROL 탭을]** 선택합니다.
1. 모든 구성 **[!UICONTROL (모든 구성)]** 이 선택되었는지 **[!UICONTROL 확인한 다음 창의]** 자산 **[!UICONTROL 섹션에서 파일]** 추가를클릭합니다.
   >[!TIP]
   >
   >QNX Momentics IDE에 버그가 있어 이러한 단추가 보이지 않는 경우도 있습니다. 단추가 보이지 않으면 표시될 때까지 창 크기를 조정합니다.

1. 작업 공간 **[!UICONTROL 을 클릭합니다]**.
1. 프로젝트에서 `ADBMobileConfig.json` 파일을 찾아 확인을 **[!UICONTROL 클릭합니다]**.

응용 프로그램은 를 사용하여 라이브러리에서 클래스/인터페이스를 가져올 수 `adobeMobileLibrary.jar` 있습니다 `#include <ADBMobile.hpp>`.

## 앱 권한 추가

프로젝트 디렉터리 `bar-descriptor.xml` 에서 줄을 `<permission>access_internet</permission>`추가하거나 QNX Momentics IDE에서 **[!UICONTROL 응용 프로그램]** 탭의 권한 섹션에 있는 **[!UICONTROL 인터넷]** 상자를선택합니다.

## 구성 `ADBMobileConfig.json` 파일 업데이트

이 `ADBMobileConfig.json` 파일에는 전역 SDK 설정이 포함되어 있습니다. 시작하려면 몇 개의 값을 업데이트해야 합니다.

The following is an example of an `ADBMobileConfig.json` file:

```json
{
    "version" : "1.0",
    "analytics" : {
        "rsids" : "coolApp",
        "server" : "my.CoolApp.com",
        "charset" : "UTF-8",
        "ssl" : true,
        "offlineEnabled" : true,
        "lifecycleTimeout" : 5,
        "privacyDefault" : "optedin",
    }
}
```

적어도 `rsids` 및 `server` 매개 변수를 업데이트해야 합니다. 자세한 내용은 [Adobe Mobile 클래스 및 메서드 참조를 참조하십시오](/help/blackberry/methods.md).

이제 BlackBerry 10 앱에서 Analytics를 구현할 수 있습니다.
