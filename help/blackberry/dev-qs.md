---
title: 개발자 빠른 시작
seo-title: Adobe Mobile Services를 위한 BlackBerry 개발자 빠른 시작
description: BlackBerry 개발자 빠른 시작 안내서를 통해 Adobe Mobile Services용 BlackBerry 라이브러리를 구현하는 프로세스를 이해할 수 있습니다.
seo-description: BlackBerry 개발자 빠른 시작 안내서를 통해 Adobe Mobile Services용 BlackBerry 라이브러리를 구현하는 프로세스를 이해할 수 있습니다.
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# 개발자 빠른 시작

이 정보는 BlackBerry 라이브러리를 구현하는 프로세스를 이해하는 데 도움이 됩니다.

## SDK 가져오기

**SDK에는 BlackBerry 10 이상이 필요합니다.**

다운로드된 SDK의 압축을 해제한 후 다음 파일이 `AdobeMobile` 폴더에 있는지 확인합니다.

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

1. Right-click on your project and select **[!UICONTROL Configure]** &gt; **[!UICONTROL Add Library]**.
1. Select **[!UICONTROL External library]** and click **[!UICONTROL Next]**.
1. **[!UICONTROL 장치 라이브러리]필드 옆의****검색[!UICONTROL 을 클릭합니다.]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. In the `Device-Debug` folder, select `libADBMobileShared.so` and click **[!UICONTROL Open]**.
1. **[!UICONTROL 시뮬레이터 라이브러리]** 필드 옆의 **검색[!UICONTROL 을 클릭합니다.]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. In the `Device-Debug` folder, select `libADBMobileShared.so` and click **[!UICONTROL Open]**.
1. **[!UICONTROL 폴더 포함]** 필드 옆의 **추가[!UICONTROL 를 클릭합니다.]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. Add the `public` folder to your includes.
1. In the `ADBMobile-4.0.0BETA-BlackBerry` folder, there is a `.json` config file named `ADBMobileConfig.json`.

   해당 파일을 프로젝트의 루트에 복사하십시오.
1. 프로젝트를 마우스 오른쪽 버튼으로 클릭하고 **[!UICONTROL 새로 고침을 선택합니다]**.

   The `.json` file should now be visible in your **[!UICONTROL Project Explorer]**.
1. 프로젝트의 `bar-descriptor.xml` 파일을 엽니다.
1. 창 하단에서 **[!UICONTROL 자산]탭을 선택합니다.**
1. **[!UICONTROL (모든 구성)]**&#x200B;이 선택되어 있는지 확인한 다음 창의 **[!UICONTROL 자산]섹션에서**&#x200B;파일 추가&#x200B;**를 클릭합니다.**
   >[!TIP]
   >
   >QNX Momentics IDE에 버그가 있어 이러한 단추가 보이지 않는 경우가 있습니다. If you can't see the buttons, resize the windows until they appear.

1. 작업 공간을 **[!UICONTROL 클릭합니다]**.
1. Find the `ADBMobileConfig.json` file in your project and click **[!UICONTROL OK]**.

Your application can import the classes/interfaces from the `adobeMobileLibrary.jar` library by using `#include <ADBMobile.hpp>`.

## 앱 권한 추가

In `bar-descriptor.xml` in the project directory, add the line `<permission>access_internet</permission>`, or in the QNX Momentics IDE, select the **[!UICONTROL Internet]** box on the permissions section of the **[!UICONTROL Application]** tab.

## Update the `ADBMobileConfig.json` config file

`ADBMobileConfig.json` 파일에는 글로벌 SDK 설정이 포함됩니다. 시작하려면 몇 가지 값을 업데이트해야 합니다.

다음은 `ADBMobileConfig.json` 파일 예제입니다.

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

You must at least update the `rsids` and `server` parameters. 자세한 내용은 Adobe Mobile [클래스 및 메서드 참조를](/help/blackberry/methods.md)참조하십시오.

이제 BlackBerry 10 앱에서 Analytics을 구현할 수 있습니다.
