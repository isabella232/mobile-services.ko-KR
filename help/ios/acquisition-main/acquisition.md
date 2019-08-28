---
description: Adobe Mobile Services에서 고유한 추적 코드가 있는 획득 링크를 생성할 수 있습니다. 사용자가 생성된 링크를 클릭한 후 Apple App Store에서 앱을 다운로드하여 실행하면, SDK에서는 자동으로 획득 데이터를 수집하여 Adobe Mobile Services로 보냅니다.
seo-description: Adobe Mobile Services에서 고유한 추적 코드가 있는 획득 링크를 생성할 수 있습니다. 사용자가 생성된 링크를 클릭한 후 Apple App Store에서 앱을 다운로드하여 실행하면, SDK에서는 자동으로 획득 데이터를 수집하여 Adobe Mobile Services로 보냅니다.
seo-title: 모바일 앱 확보
solution: Marketing Cloud, Analytics
title: 모바일 앱 확보
topic: 개발자 및 구현
uuid: 5 FECE 619-E 4 B 8-4 D 06-9250-DCB 66 FA 32 CE 0
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Mobile app acquisition {#mobile-app-acquisition}

Adobe Mobile Services에서 고유한 추적 코드가 있는 획득 링크를 생성할 수 있습니다. 사용자가 생성된 링크를 클릭한 후 Apple App Store에서 앱을 다운로드하여 실행하면, SDK에서는 자동으로 획득 데이터를 수집하여 Adobe Mobile Services로 보냅니다.

획득을 사용하려면 **반드시** SDK 버전 4.1 이상이 있어야 합니다.

획득 링크는 Adobe Mobile Services에서 만들어야 합니다. 자세한 내용은 [획득을 참조하십시오.](/help/using/acquisition-main/acquisition-main.md)

이 섹션의 정보는 SDK가 획득 링크에서 획득 데이터를 전송하도록 허용합니다.

## Tracking mobile app acquisition {#section_CEA30C652AC8470784B8054E299B80FA}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   자세한 내용은 핵심 구현 *및* 라이프사이클에서 [프로젝트에 SDK 및 구성 파일 추가를](/help/ios/getting-started/dev-qs.md)참조하십시오.
1. 라이브러리를 가져옵니다:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. `ADBMobileConfig.json` 파일에 필수 획득 설정이 포함되어 있는지 확인합니다.

   ```xml
   "acquisition": { 
      "server": "c00.adobe.com", 
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f" 
   }, 
   "analytics": { 
     "referrerTimeout": 5, 
     ...
   ```

   >[!IMPORTANT]
   >
   >여러 보고서 세트로 데이터를 전송하는 경우, 보고서 세트 ID의 목록에서 첫 번째 보고서 세트와 연관된 앱의 획득 설정 (획득 서버 및 appid) 를 사용합니다.

   `acquisition` 설정은 Adobe Mobile Services에 의해 생성되므로 변경해서는 안 됩니다. For more information about how to download a customized `ADBMobileConfig.json` file with the `acquisition` settings pre-configured, see [Before You Start](/help/ios/getting-started/requirements.md).

이 설정을 사용하면 첫 번째 앱 시작 이후 초기 라이프사이클 호출과 함께 획득 데이터가 자동으로 전송됩니다.

>[!CAUTION]
>
>`referrerTimeout` 앱 확보를 활성화하려면 0 보다 큰 값으로 설정해야 합니다.

## 유니버설 링크를 위한 iOS 앱 활성화

앱에서 범용 링크를 사용하는 경우 Adobe Marketing Links 도메인을 앱에 대한 관련 도메인 목록에 추가합니다.

Xcode에서 Adobe Marketing Links 도메인을 관련 도메인 목록에 추가하려면:

1. 프로젝트 타겟으로 이동하여 **[!UICONTROL 기능]** 탭을 클릭합니다.
2. **[!UICONTROL 연결된 도메인으로 스크롤]** 섹션을 클릭하고 켤 수 있습니다.
3. 마케팅 링크 URL에서 마케팅 링크 도메인의 **[!UICONTROL 도메인]** 목록에 항목을 추가합니다.

`applinks:5848561889a02a6996aea62b.c00.adobe.com`출품작의 모양은