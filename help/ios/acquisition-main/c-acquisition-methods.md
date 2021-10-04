---
description: '다음은 iOS 라이브러리에서 제공하는 획득 메서드입니다. '
solution: Experience Cloud,Analytics
title: 획득 메서드
uuid: 6f88de57-793d-4d33-9a54-f6714289fd2c
exl-id: dd2721ae-b9a6-48b9-bc92-8e12ee551929
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 100%

---

# 획득 메서드 {#acquisition-methods}

다음은 iOS 라이브러리에서 제공하는 Acquisition 메서드입니다.

지원되는 메서드는 다음과 같습니다.

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
