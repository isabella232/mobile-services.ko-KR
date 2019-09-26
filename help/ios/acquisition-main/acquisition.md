---
description: Adobe Mobile Services에서 고유한 추적 코드가 있는 획득 링크를 생성할 수 있습니다. 사용자가 생성된 링크를 클릭한 후 Apple App Store에서 앱을 다운로드하여 실행하면, SDK에서는 자동으로 획득 데이터를 수집하여 Adobe Mobile Services로 보냅니다.
seo-description: Adobe Mobile Services에서 고유한 추적 코드가 있는 획득 링크를 생성할 수 있습니다. 사용자가 생성된 링크를 클릭한 후 Apple App Store에서 앱을 다운로드하여 실행하면, SDK에서는 자동으로 획득 데이터를 수집하여 Adobe Mobile Services로 보냅니다.
seo-title: Mobile app acquisition
solution: Marketing Cloud,Analytics
title: Mobile app acquisition
topic: 개발자 및 구현
uuid: 5fece619-e4b8-4d06-9250-dcb66fa32ce0
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Mobile app acquisition {#mobile-app-acquisition}

Adobe Mobile Services에서 고유한 추적 코드가 있는 획득 링크를 생성할 수 있습니다. 사용자가 생성된 링크를 클릭한 후 Apple App Store에서 앱을 다운로드하여 실행하면, SDK에서는 자동으로 획득 데이터를 수집하여 Adobe Mobile Services로 보냅니다.

획득을 사용하려면 **반드시** SDK 버전 4.1 이상이 있어야 합니다.

획득 링크는 Adobe Mobile Services에서 만들어야 합니다. For more information, see [Acquisition](/help/using/acquisition-main/acquisition-main.md).

이 섹션의 정보를 통해 SDK가 획득 링크에서 획득 데이터를 전송할 수 있습니다.

## Tracking mobile app acquisition {#section_CEA30C652AC8470784B8054E299B80FA}

1. 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다.

   For more information, see Add the SDK and Config File to your Project in Core Implementation and Lifecycle.**[](/help/ios/getting-started/dev-qs.md)
1. 라이브러리를 가져옵니다:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required acquisition settings:

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
   > 여러 보고서 세트로 데이터를 보내는 경우 보고서 세트 ID 목록의 첫 번째 보고서 세트와 연결된 앱의 획득 설정(획득 서버 및 appid)을 사용하십시오.

   `acquisition` 설정은 Adobe Mobile Services에 의해 생성되므로 변경해서는 안 됩니다. For more information about how to download a customized `ADBMobileConfig.json` file with the `acquisition` settings pre-configured, see [Before You Start](/help/ios/getting-started/requirements.md).

이 설정을 사용하면 첫 번째 앱 시작 이후 초기 라이프사이클 호출과 함께 획득 데이터가 자동으로 전송됩니다.

>[!CAUTION]
>
>`referrerTimeout`  앱 획득을 사용하려면 을 0보다 큰 값으로 설정해야 합니다.

## Enabling your iOS app for Universal Links

If you are using Universal Links in your app, add your Adobe Marketing Links domain to the Associated Domains list for your app.

In Xcode, to add your Adobe Marketing Links domain to the Associated Domains list:

1. Go to your project target and click the Capabilities tab.****
2. Scroll down to Associated Domains section and toggle it on.****
3. Add an entry in the Domains list for your Marketing Links domain from your Marketing Links URL.****

Your entry will look something like  .`applinks:5848561889a02a6996aea62b.c00.adobe.com`