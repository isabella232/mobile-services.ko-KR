---
description: Apple 알림에 이미지 파일을 첨부할 수 있습니다. 시각적 구성 요소를 추가하면 푸시 알림을 통한 사용자 참여도를 크게 높일 수 있습니다.
seo-description: Apple 알림에 이미지 파일을 첨부할 수 있습니다. 시각적 구성 요소를 추가하면 푸시 알림을 통한 사용자 참여도를 크게 높일 수 있습니다.
seo-title: 리치 푸시 알림 수신
title: 리치 푸시 알림 수신
uuid: 0 DBDA 409-CF 49-4 EB 8-90 EE-BAF 27911 DC 07
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Receive rich push notifications {#receive-rich-push-notifications}

Apple 알림에 이미지 파일을 첨부할 수 있습니다. 시각적 구성 요소를 추가하면 푸시 알림을 통한 사용자 참여도를 크게 높일 수 있습니다.

iOS 앱에서 리치 푸시 알림을 받으려면

1. 앱의 푸시 메시지를 구현합니다. [푸시 메시지](/help/ios/messaging-main/push-messaging/push-messaging.md).
1. 앱에 텍스트 푸시 메시지를 보낼 수 있는지 확인합니다.
1. 다음 단계를 완료하여 알림 서비스 확장 프로그램을 추가합니다.

   1. In your Xcode project, select  **[!UICONTROL File]** &gt; **[!UICONTROL New]** &gt; **[!UICONTROL Target]**.
   1. **[!UICONTROL 알림 서비스 확장을 선택합니다]**.
   1. `NotificationService.m` 파일이 있는지 확인합니다.

1. `NotificationService.m` 파일을 열고 다음 위임 메서드가 있는지 확인하십시오.

   * 알림 요청을 수신하는 메서드 한 개
   * 서비스 확장 프로그램의 만료를 처리하는 메서드 한 개

      리치 푸시 알림을 받는 데는 첫 번째 메서드가 사용됩니다.

      ```objective-c
      (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent *contentToDeliver))contentHandler;
      ```

      이 방식에서는 키를 사용하여 미디어 `userInfo` URL를 가져올 `attachment-url` 수 있습니다. 파일을 로컬 디렉토리에 다운로드한 `bestAttemptContent.attachments`후 로컬 경로를 추가합니다.

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


iOS에서 사용하는 리치 푸시 알림에 대한 자세한 내용은 [UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment)를 참조하십시오.
