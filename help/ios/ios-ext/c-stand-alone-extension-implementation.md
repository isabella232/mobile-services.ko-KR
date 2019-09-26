---
description: iOS 10부터는 포함 앱 없이 배포할 수 있는 확장 프로그램, 즉 독립형 확장 프로그램을 만들 수 있습니다. 이 확장 프로그램의 경우 데이터를 공유할 포함 앱이 없으므로 앱 그룹이 필요하지 않습니다.
seo-description: iOS 10부터는 포함 앱 없이 배포할 수 있는 확장 프로그램, 즉 독립형 확장 프로그램을 만들 수 있습니다. 이 확장 프로그램의 경우 데이터를 공유할 포함 앱이 없으므로 앱 그룹이 필요하지 않습니다.
seo-title: 독립형 확장 프로그램 구현
solution: Marketing Cloud,Analytics
title: 독립형 확장 프로그램 구현
topic: 개발자 및 구현
uuid: 9b47f082-b78f-4611-968d-014c32ede6bc
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Stand-alone extension implementation {#stand-alone-extension-implementation}

iOS 10부터는 포함 앱 없이 배포할 수 있는 확장 프로그램, 즉 독립형 확장 프로그램을 만들 수 있습니다. 이 확장 프로그램의 경우 데이터를 공유할 포함 앱이 없으므로 앱 그룹이 필요하지 않습니다.

>[!IMPORTANT]
>
>To use stand-alone extensions, you must have Mobile SDK version 4.13.0 or later.

## SDK에서 사용할 독립형 확장 프로그램 구성 {#section_B7A84603BB9D4B48BB46BE8D3B9E3CF0}

독립형 확장 프로그램을 구성하려면

1. Ensure that the `ADBMobileConfig.json` file is a member of your extension's target.
1. 다음 라이브러리 및 프레임워크를 연결합니다.

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. 확장 프로그램의 기본 보기 컨트롤러에서 SDK의 확장 유형을 `ADBMobileAppExtensionTypeStandAlone`으로 설정한 후에 SDK 관련 활동을 완료합니다.

   ```objective-c
   [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone];
   ```

1. 예기치 않은 오류 없이 앱이 빌드되는지 확인합니다.

## Additional notes {#section_1C9A55E2309A44BF842310F735702B3D}

다음은 몇 가지 추가 정보입니다.

* 컨텍스트 데이터 값 `a.RunMode`가 추가되었으며, 이 값은 데이터의 출처가 포함 앱인지 아니면 확장 프로그램인지 나타냅니다.

   * `a.RunMode = Application`

      이 값은 포함 앱에서 히트가 발생했음을 의미합니다.
   * `a.RunMode = Extension`

      이 값은 확장 프로그램에서 히트가 발생했음을 의미합니다.

* iOS 확장 앱에 대해서는 라이프사이클 호출이 트리거되지 않습니다.

