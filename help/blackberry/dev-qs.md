---
title: 개발자 빠른 시작
description: BlackBerry 개발자 빠른 시작 안내서 는 Adobe Mobile Services용 BlackBerry 라이브러리를 구현하는 프로세스를 이해하는 데 도움이 됩니다.
exl-id: 65f39667-541a-4bbd-af9b-823638aa6f42
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 1%

---

# 개발자 빠른 시작

다음은 BlackBerry 라이브러리를 구현하는 프로세스를 이해하는 데 유용한 정보입니다.

## SDK 가져오기

**SDK를 사용하려면 BlackBerry 10 이상이 필요합니다.**

다운로드한 SDK의 압축을 푼 후에 다음 파일이 `AdobeMobile` 폴더에 있는지 확인합니다.

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

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 구성]** > **[!UICONTROL 라이브러리 추가]**&#x200B;를 선택합니다.
1. **[!UICONTROL 외부 라이브러리]**&#x200B;를 선택하고 **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. **[!UICONTROL 장치 라이브러리]** 필드 옆에 있는 **[!UICONTROL 찾아보기]**&#x200B;를 클릭합니다.
1. `ADBMobile-4.0.0BETA-BlackBerry` 폴더로 이동합니다.
1. `Device-Debug` 폴더에서 `libADBMobileShared.so` 을 선택하고 **[!UICONTROL 열기]**&#x200B;를 클릭합니다.
1. **[!UICONTROL 시뮬레이터 라이브러리]** 필드 옆에 있는 **[!UICONTROL 찾아보기]**&#x200B;를 클릭합니다.
1. `ADBMobile-4.0.0BETA-BlackBerry` 폴더로 이동합니다.
1. `Device-Debug` 폴더에서 `libADBMobileShared.so` 을 선택하고 **[!UICONTROL 열기]**&#x200B;를 클릭합니다.
1. **[!UICONTROL 폴더 포함]** 필드 옆에 있는 **[!UICONTROL 추가]**&#x200B;를 클릭합니다.
1. `ADBMobile-4.0.0BETA-BlackBerry` 폴더로 이동합니다.
1. 포함에 `public` 폴더를 추가합니다.
1. `ADBMobile-4.0.0BETA-BlackBerry` 폴더에 `.json` 구성 파일 `ADBMobileConfig.json`이 있습니다.

   해당 파일을 프로젝트의 루트에 복사합니다.
1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL 새로 고침]**&#x200B;을 선택합니다.

   이제 `.json` 파일이 **[!UICONTROL 프로젝트 탐색기]**&#x200B;에 표시됩니다.
1. 프로젝트에 대한 `bar-descriptor.xml` 파일을 엽니다.
1. 창 하단에서 **[!UICONTROL 자산]** 탭을 선택합니다.
1. **[!UICONTROL (모든 구성)]**&#x200B;이 선택되었는지 확인한 다음, 창의 **[!UICONTROL 자산]** 섹션에서 **[!UICONTROL 파일 추가]**&#x200B;를 클릭합니다.
   >[!TIP]
   >
   >QNX Analytics IDE에 버그가 있어 이러한 버튼이 보이지 않는 경우가 있습니다. 단추가 보이지 않으면 창이 나타날 때까지 창의 크기를 조정합니다.

1. **[!UICONTROL 작업 공간]**&#x200B;을 클릭합니다.
1. 프로젝트에서 `ADBMobileConfig.json` 파일을 찾고 **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

`#include <ADBMobile.hpp>` 를 사용하여 `adobeMobileLibrary.jar` 라이브러리에서 클래스/인터페이스를 가져올 수 있습니다.

## 앱 권한 추가

프로젝트 디렉토리의 `bar-descriptor.xml`에서 `<permission>access_internet</permission>` 줄을 추가하거나, QNX Momentics IDE에서 **[!UICONTROL Application]** 탭의 권한 섹션에서 **[!UICONTROL 인터넷]** 상자를 선택합니다.

## `ADBMobileConfig.json` 구성 파일 업데이트

`ADBMobileConfig.json` 파일에 글로벌 SDK 설정이 포함되어 있습니다. 시작하려면 몇 가지 값을 업데이트해야 합니다.

다음은 `ADBMobileConfig.json` 파일의 예입니다.

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

`rsids` 및 `server` 매개 변수 이상을 업데이트해야 합니다. 자세한 내용은 [Adobe 모바일 클래스 및 메서드 참조](/help/blackberry/methods.md)를 참조하십시오.

이제 BlackBerry 10 앱에서 Analytics를 구현할 수 있습니다.
