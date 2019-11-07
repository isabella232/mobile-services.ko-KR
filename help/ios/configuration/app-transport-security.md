---
description: 다음 정보는 iOS 9에 대한 새로운 보안 요구 사항 세트인 앱 전송 보안(ATS)으로 작업하는 데 유용한 정보입니다.
seo-description: 다음 정보는 iOS 9에 대한 새로운 보안 요구 사항 세트인 앱 전송 보안(ATS)으로 작업하는 데 유용한 정보입니다.
seo-title: 앱 전송 보안
solution: Marketing Cloud,Analytics
title: 앱 전송 보안
topic: 개발자 및 구현
uuid: e9ee13cf-9802-492e-8b11-95f028e34e61
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# 앱 전송 보안 {#app-transport-security}

다음 정보는 iOS 9에 대한 새로운 보안 요구 사항 세트인 앱 전송 보안(ATS)으로 작업하는 데 유용한 정보입니다.

Apple에서는 iOS 9부터 안전한 연결을 위해 우수 사례를 따르는 요구 사항 세트인 앱 전송 보안 기능을 도입했습니다. 자세한 내용은 [정보 속성 목록 키 참조](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/)에서 *NSAppTransportSecurity*&#x200B;를 참조하십시오.

Adobe Mobile SDK 버전 4.7 이상에서 ATS로 원활하게 작업하려면 앱 설정 관리 페이지에서 SSL 사용 옵션을 사용합니다. 자세한 내용은 [앱 설정 관리](/help/using/c-manage-app-settings/c-manage-app-settings.md) 또는 [ADBMobile JSON 구성](/help/ios/configuration/json-config/json-config.md)을 참조하십시오.

Adobe Mobile Services의 앱 설정 관리 페이지에서 **[!UICONTROL HTTPS 사용]** 옵션을 선택하면 HTTPS를 통해 Analytics, Audience Manager, Target 및 Adobe Experience Platform ID 서비스의 모든 히트가 전송됩니다.

또는 다음 서버를 허용 목록에 추가할 수도 있습니다.

| 제품 | 지침 |
|--- |--- |
| Analytics | Analytics 서버를 허용하려면 info.plist 파일에 ATS용 예외 도메인으로 추적 서버 도메인을 추가하십시오.  추적 서버 도메인은 `ADBMobileConfig.json` 파일의 Analytics 섹션이나 앱 설정 관리 페이지의 Analytics 섹션에 있습니다. |
| Audience Manager | Audience Manager 도메인은 파일의 `ADBMobileConfig.json`audienceManager 개체 서버 속성에 있습니다.  앱에서 Audience Manager를 사용 중인데 SSL이 활성화되어 있지 않은 경우에는 이 서버를 `Info.plist` 파일에 ATS에 대한 예외 도메인으로 추가하십시오. |
| Target | Target 종단점을 Info.plist 파일에 ATS용 예외 도메인으로 추가할 수 있습니다.  Target 종단점을 찾으려면 `clientCodeproperty` 파일의 타겟 개체에서 `ADBMobileConfig.json`를 찾도록 하십시오. 엔드포인트는 `https://{clientCode}.tt.omtrdc.net`입니다. 예를 들어 `clientCodeproperty`가 `“myCompany”`이면 엔드포인트는 `https://myCompany.tt.omtrdc.net`이 됩니다. |
| Adobe Experience Platform ID 서비스 | Experience Cloud 서버를 `Info.plist` 파일에 ATS에 대한 예외 도메인으로 추가할 수 있습니다. 도메인은 `dpm.demdex.net`입니다. |
| Mobile Services: Acquisition | `Info.plist` 파일에서 ATS에 대한 예외 도메인으로서 획득 서버를 허용 목록에 추가합니다. 도메인은 `c00.adobe.com`입니다. |
| Mobile Services: 인앱 메시지 | 인앱 메시지를 사용하는 경우 HTTPS가 아닌 각 URL에 대해 ATS용 예외 도메인에 항목을 추가해야 할 수 있습니다. 이 목록에는 호스팅된 이미지 및 사용자 지정 전체 화면 메시지 HTML에 포함된 URL이 포함되어 있습니다. `info.plist` 파일에서 예외 도메인 설정에 대한 자세한 내용은 *표 2: 앱 전송 보안 사전 기본 키*&#x200B;의 *NSExceptionDomains* 행을 참조하십시오. [정보 속성 목록 키 참조](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/)/에서 *표 3 예외 도메인 사전 키*&#x200B;도 참조하십시오. |

>[!TIP]
>
>이러한 고려 사항은 Adobe Mobile SDK에서 수행한 연결에 영향을 주며 웹 보기 또는 다른 앱에서 수행한 연결에는 영향을 주지 않습니다.

