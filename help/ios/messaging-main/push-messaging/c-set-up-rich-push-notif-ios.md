---
description: Apple 알림에 이미지 파일을 첨부할 수 있습니다. 시각적 구성 요소를 추가하면 푸시 알림에 대한 사용자의 참여가 크게 늘어날 수 있습니다.
title: 리치 푸시 알림 수신
uuid: 0dbda409-cf49-4eb8-90ee-baf27911dc07
exl-id: 1167ae4b-04ad-4c0d-a9db-67d30693f697
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 33%

---

# 리치 푸시 알림 수신 {#receive-rich-push-notifications}

Apple 알림에 이미지 파일을 첨부할 수 있습니다. 시각적 구성 요소를 추가하면 푸시 알림에 대한 사용자의 참여가 크게 늘어날 수 있습니다.

iOS 앱에서 푸시 알림을 받으려면 다음을 수행하십시오.

1. [푸시 메시지](/help/ios/messaging-main/push-messaging/push-messaging.md)의 단계를 완료하여 앱에 대한 푸시 메시지를 구현합니다.
1. 앱에 텍스트 푸시 메시지를 보낼 수 있는지 확인합니다.
1. 다음 단계를 완료하여 알림 서비스 확장을 추가합니다.

   1. Xcode 프로젝트에서 **[!UICONTROL 파일]** > **[!UICONTROL 새]** > **[!UICONTROL Target]**&#x200B;을 선택합니다.
   1. **[!UICONTROL 알림 서비스 확장을 선택합니다]**.
   1. `NotificationService.m` 파일이 있는지 확인합니다.

1. `NotificationService.m` 파일을 열고 다음 위임 메서드가 있는지 확인하십시오.

   * 알림 요청을 받는 하나의 방법입니다.
   * 서비스 확장 만료를 처리하는 한 가지 방법입니다.

      리치 푸시 알림을 수신하려면 첫 번째 방법이 사용됩니다.

      ```objective-c
      (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent *contentToDeliver))contentHandler;
      ```

      이 메서드에서는 `attachment-url` 키를 사용하여 `userInfo`에서 미디어 URL을 가져올 수 있습니다. 파일을 로컬 디렉토리에 다운로드한 후 로컬 경로를 `bestAttemptContent.attachments`에 추가합니다.

      다음은 이 메서드의 코드 예입니다.

      ```objective-c
      - (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
      self.contentHandler = contentHandler;
      self.bestAttemptContent = [request.content mutableCopy];
         NSDictionary* userInfo = request.content.userInfo;
      if(userInfo[@"attachment-url"]){
         NSURL* url = [[NSURL alloc] initWithString:userInfo[@"attachment-url"]];
         NSURLSessionDownloadTask* task = [[NSURLSession sharedSession] downloadTaskWithURL:url completionHandler:^(NSURL * _Nullable location, NSURLResponse * _Nullable response, NSError * _Nullable error) {
             if(!location){
                 return;
             }
             NSString* tmpDirectory = NSTemporaryDirectory();
             NSString* tmpFilePath = [NSString stringWithFormat:@"file://%@%d%d%@", tmpDirectory, arc4random_uniform(100000),
                                    arc4random_uniform(100000), [url lastPathComponent]];
             NSURL* tmpUrl = [[NSURL alloc] initWithString:tmpFilePath];
             NSError * fileError = nil;
             [[NSFileManager defaultManager] moveItemAtURL:location toURL:tmpUrl error:&amp;fileError];
             if(fileError){
                 return;
             }
             UNNotificationAttachment* attachment = [UNNotificationAttachment attachmentWithIdentifier:@"video" URL:tmpUrl options:nil error:&amp;fileError];
             if(fileError){
                 return;
             }
             self.bestAttemptContent.attachments = @[attachment];
             self.contentHandler(self.bestAttemptContent);
         }];
         [task resume];
       }
      }
      ```


iOS의 리치 푸시 알림에 대한 자세한 내용은 [UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment) 를 참조하십시오.
