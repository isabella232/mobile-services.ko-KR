---
description: iOS 10부터 Apple에서는 포함된 앱 없이 배포할 수 있는 독립 실행형 확장이라는 확장을 만들 수 있습니다. 이 확장 기능을 사용하면 데이터를 공유하는 포함 앱이 없으므로 앱 그룹이 필요하지 않습니다.
seo-description: iOS 10부터 Apple에서는 포함된 앱 없이 배포할 수 있는 독립 실행형 확장이라는 확장을 만들 수 있습니다. 이 확장 기능을 사용하면 데이터를 공유하는 포함 앱이 없으므로 앱 그룹이 필요하지 않습니다.
seo-title: 독립형 확장 프로그램 구현
solution: Experience Cloud,Analytics
title: 독립형 확장 프로그램 구현
topic-fix: Developer and implementation
uuid: 9b47f082-b78f-4611-968d-014c32ede6bc
exl-id: b51247b6-c4ba-4a00-9ba0-1824450ac067
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 100%

---

# 독립형 확장 프로그램 구현 {#stand-alone-extension-implementation}

iOS 10부터 Apple에서는 포함된 앱 없이 배포할 수 있는 독립 실행형 확장이라는 확장을 만들 수 있습니다. 이 확장 기능을 사용하면 데이터를 공유하는 포함 앱이 없으므로 앱 그룹이 필요하지 않습니다.

>[!IMPORTANT]
>
>독립형 확장 프로그램을 사용하려면 Mobile SDK 버전 4.13.0 이상이 있어야 합니다.

## SDK에서 사용할 독립형 확장 프로그램 구성 {#section_B7A84603BB9D4B48BB46BE8D3B9E3CF0}

독립형 확장 프로그램을 구성하려면

1. `ADBMobileConfig.json` 파일이 확장 프로그램의 타겟 구성원인지 확인합니다.
1. 다음 라이브러리 및 프레임워크를 연결합니다.

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. 확장 프로그램의 기본 보기 컨트롤러에서 SDK의 확장 유형을 `ADBMobileAppExtensionTypeStandAlone`으로 설정한 후에 SDK 관련 활동을 완료합니다.

   ```objective-c
   [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone];
   ```

1. 예기치 않은 오류 없이 앱이 빌드되는지 확인합니다.

## 추가 참고 사항 {#section_1C9A55E2309A44BF842310F735702B3D}

다음은 몇 가지 추가 정보입니다.

* 컨텍스트 데이터 값 `a.RunMode`가 추가되었으며, 이 값은 데이터의 출처가 포함 앱인지 아니면 확장 프로그램인지 나타냅니다.

   * `a.RunMode = Application`

      이 값은 포함 앱에서 히트가 발생했음을 의미합니다.
   * `a.RunMode = Extension`

      이 값은 확장에서 히트가 발생했음을 의미합니다.

* iOS 확장 앱에서는 라이프사이클 호출이 트리거되지 않습니다.
