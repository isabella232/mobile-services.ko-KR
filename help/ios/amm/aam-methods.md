---
description: 다음은 iOS 라이브러리에서 제공하는 Audience Manager 메서드 목록입니다.
seo-description: 다음은 iOS 라이브러리에서 제공하는 Audience Manager 메서드 목록입니다.
seo-title: Audience Manager 메서드
solution: Experience Cloud,Analytics
title: Audience Manager 메서드
topic: Developer and implementation
uuid: 97658bd6-4c4f-4875-abe9-36dad4ec8bae
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '363'
ht-degree: 100%

---


# Audience Manager 메서드 {#audience-manager-methods}

다음은 iOS 라이브러리에서 제공하는 Audience Manager 메서드 목록입니다.

현재 SDK는 Analytics, Target, Audience Manager 및 Adobe Experience Platform ID 서비스 등 여러 Adobe Experience Cloud 솔루션을 지원합니다. 메서드는 솔루션에 따라 접두사가 사용되고 Manager 메서드 앞에는 &quot;`audience`audience&quot; 접두사가 붙습니다.

Audience Manager가 JSON 파일에 구성되어 있으면 `application:didFinishLaunchingWithOptions:`:와 함께 라이프사이클 지표가 포함된 신호가 전송됩니다.

* **audienceVisitorProfile**

   가장 최근에 얻은 방문자 프로필을 반환하고, 전송된 신호가 없는 경우에는 `null`을 반환합니다. 방문자 프로필은 앱이 여러 번 시작되는 경우에도 쉽게 액세스할 수 있도록 `NSUserDefaults`에 저장됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (NSDictionary *) audienceVisitorProfile;
      ```

   * 다음은 이 메뉴의 코드 샘플입니다.

      ```objective-c
      NSDictionary *profile = [ADBMobile audienceVisitorProfile]; 
      ```

* **audienceDpid**

   현재 DPID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      +(NSString *) audience Dpid;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSString *currentDpid = [ADBMobileaudience Dpid]; 
      ```

* **audienceDpuuid**

   현재 DPUUID를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      +(NSString *) audienceDpuuid;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      NSString *currentDpuuid = [ADBMobileaudience Dpuuid]; 
      ```

* **audienceSetDpid:&#x200B;dpuuid:**

   DPID 및 DPUUID를 설정합니다. 설정할 때 둘 다 각 신호에 추가됩니다.

   * **데이터 공급자 ID**(DPID)는 Audience Manager에서 할당하는 데이터 파트너 ID입니다.
   * **데이터 공급자 고유 사용자 ID(DPUUID)**&#x200B;는 해당 사용자에 대한 데이터 공급자의 고유 ID입니다.

      >[!IMPORTANT]
      >
      >버전 4.13.x 이전에서는 DPUUID가 자동으로 인코딩되지 않았습니다. 버전 4.13.x부터 SDK는 먼저 전달된 값을 인코딩한 후 이 값을 다시 인코딩합니다. 이 프로세스에서는 SDK가 이전 버전과의 호환성을 벗어나지 않습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) audienceSetDpid: (NSString*)   
                      dpiddpuuid:(NSString*)dpuuid;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-
      [ADBMobile audienceSetDpid:@"290"
                        dpuuid:@"99301393920493"];
      ```

* **audienceReset**

   Audience Manager UUID를 재설정하고 현재 방문자 프로필을 삭제합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      +(void) audienceReset;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile audienceReset]; 
      ```

* **audienceSignalWithData::&#x200B;callback:**

   Audience Management에 트레이트와 함께 신호를 보내고 콜백에서 반환된 일치 세그먼트를 받습니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
      + (void) audienceSignalWithData:(NSDictionary*)data
                            callback:(void(^)(NSDictionary
      *response))callback; 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile audienceSignalWithData:traits
                               callback:^(NSDictionary*response){
                                 //do something with returned segments
                               }];
      ```

## 예

```objective-c
// setup your traits dictionary 
NSDictionary *traits = @{@"trait":@"b"}; 
// submit your signal and take action on results 
[ADBMobile audienceSignalWithData:traits  
                         callback:^(NSDictionary *response) { 
                             // do something with visitor segments here 
                             if ([response[@"gender"] isEqualToString:@"male"]) { 
                             // do something with gender  
                             } 
                         }];
```
