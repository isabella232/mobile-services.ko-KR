---
description: 'iOS 라이브러리에서 다음 획득 방법을 제공합니다. '
seo-description: 'iOS 라이브러리에서 다음 획득 방법을 제공합니다. '
seo-title: 획득 메서드
solution: Marketing Cloud, Analytics
title: 획득 메서드
uuid: 6 F 88 DE 57-793 D -4 D 33-9 A 54-F 6714289 FD 2 C
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Acquisition methods {#acquisition-methods}

다음은 iOS 라이브러리에서 제공하는 Acquisition 메서드입니다.

다음 메서드가 지원됩니다.

* **acquisitionCampaignStartForApp:data:**

   사용자가 링크를 클릭한 것처럼 개발자가 앱 획득 캠페인을 시작할 수 있도록 해줍니다. 이 메서드는 `SKStoreView`를 사용하여 작업하는 경우처럼, 획득 링크를 수동으로 만들고 직접 앱스토어 리디렉션을 처리하는 데 유용합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void)acquisitionCampaignStartForApp:(NSString *) appId data:(NSDictionary *)data; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile acquisitionCampaignStartForApp:@"0652024f-adcd-49f9-9bd7-2552a4564d2f" data:@{@"custom.key":@"value"}]; 
      ```


