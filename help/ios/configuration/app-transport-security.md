---
description: 다음 정보는 iOS 9에 대한 새로운 보안 요구 사항 세트인 앱 전송 보안(ATS)으로 작업하는 데 유용한 정보입니다.
seo-description: 다음 정보는 iOS 9에 대한 새로운 보안 요구 사항 세트인 앱 전송 보안(ATS)으로 작업하는 데 유용한 정보입니다.
seo-title: 앱 전송 보안
solution: Marketing Cloud, Analytics
title: 앱 전송 보안
topic: 개발자 및 구현
uuid: E 9 EE 13 CF -9802-492 E -8 B 11-95 F 028 E 34 E 61
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# 앱 전송 보안 {#app-transport-security}

다음 정보는 iOS 9에 대한 새로운 보안 요구 사항 세트인 앱 전송 보안(ATS)으로 작업하는 데 유용한 정보입니다.

Apple에서는 iOS 9부터 안전한 연결을 위해 우수 사례를 따르는 요구 사항 세트인 앱 전송 보안 기능을 도입했습니다. 자세한 내용은 *Nsapptransportsecurity* 를 [참조하십시오](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/).

Adobe Mobile SDK 버전 4.7 이상에서 ATS로 원활하게 작업하려면 앱 설정 관리 페이지에서 SSL 사용 옵션을 사용합니다. 자세한 내용은 앱 설정 [또는](/help/using/c-manage-app-settings/c-manage-app-settings.md) [Adbmobile JSON 구성 관리를 참조하십시오](/help/ios/configuration/json-config/json-config.md).

In Adobe Mobile Services, by selecting the **[!UICONTROL Use HTTPS]** option in the Manage App Settings page, all hits from Analytics, Audience Manager, Target, and Adobe Experience Platform Identity Services are sent via HTTPS.

대안으로서, 다음 서버를 화이트리스트에 연결할 수 있습니다.

| 제품 | 지침 |
|--- |--- |
| Analytics | Analytics 서버를 허용하려면 info.plist 파일에 ATS용 예외 도메인으로 추적 서버 도메인을 추가하십시오.  추적 서버 도메인은 `ADBMobileConfig.json` 파일의 Analytics 섹션이나 앱 설정 관리 페이지의 Analytics 섹션에 있습니다. |
| Audience Manager | Audience Manager 도메인은 파일의 `ADBMobileConfig.json`audienceManager 개체 서버 속성에 있습니다.  앱에서 Audience Manager를 사용 중인데 SSL이 활성화되어 있지 않은 경우에는 이 서버를 `Info.plist` 파일에 ATS에 대한 예외 도메인으로 추가하십시오. |
| Target | Target 종단점을 Info.plist 파일에 ATS용 예외 도메인으로 추가할 수 있습니다.  Target 종단점을 찾으려면 `clientCodeproperty` 파일의 타겟 개체에서 `ADBMobileConfig.json`를 찾도록 하십시오. `https://{clientCode}.tt.omtrdc.net`끝점이 생성됩니다. For example, if your `clientCodeproperty` is `“myCompany”`, your endpoint will be `https://myCompany.tt.omtrdc.net`. |
| Adobe Experience Platform Identity Service | Experience Cloud 서버를 `Info.plist` 파일에 ATS에 대한 예외 도메인으로 추가할 수 있습니다. This domain is `dpm.demdex.net`. |
| Mobile Services: Acquisition | `Info.plist` 파일에서 ATS에 대한 예외 도메인으로서 획득 서버를 허용 목록에 추가합니다. This domain is `c00.adobe.com`. |
| Mobile Services: 인앱 메시지 | 인앱 메시지를 사용하는 경우 HTTPS가 아닌 각 URL에 대해 ATS용 예외 도메인에 항목을 추가해야 할 수 있습니다. 이 목록에는 호스팅된 이미지 및 사용자 지정 전체 화면 메시지 HTML에 포함된 URL이 포함되어 있습니다. `info.plist` 파일에서 Exceptions 도메인을 설정하는 방법에 대한 자세한 내용은 표 2의 *nsexceptiondomains* 행을 *참조하십시오. App Transport Security Dictionary 기본 키를*&#x200B;참조하십시오. 정보 *속성 목록 키* 참조에서 [표 3 예외 도메인 사전 키를 참조하십시오](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/). |

>[!TIP]
>
>이러한 고려 사항은 Adobe Mobile SDK에서 만든 연결에 영향을 미치며, 웹 보기나 앱에서 만든 다른 연결에 영향을 주지 않습니다.

