---
description: Android 알림에 이미지 파일을 첨부할 수 있습니다. 시각적 구성 요소를 추가하면 푸시 알림을 통한 사용자 참여도를 크게 높일 수 있습니다.
seo-description: Android 알림에 이미지 파일을 첨부할 수 있습니다. 시각적 구성 요소를 추가하면 푸시 알림을 통한 사용자 참여도를 크게 높일 수 있습니다.
seo-title: 리치 푸시 알림 수신
title: 리치 푸시 알림 수신
uuid: 4 A 0340 A 6-666 B -49 B 6-907 A -9 AFC 966 DFDBA
translation-type: tm+mt
source-git-commit: dca3663986b3ecc6e9fb736cc99513279715225c

---


# Receive rich push notifications {#receive-rich-push-notifications}

Android 알림에 이미지 파일을 첨부할 수 있습니다. 시각적 구성 요소를 추가하면 푸시 알림을 통한 사용자 참여도를 크게 높일 수 있습니다.

## Handle the incoming rich push message (FCM) {#section_AF1A3BC2312C4E1DA517CC90296C11E2}

앱이 포그라운드에 있는 경우 푸시 메시지는 `FirebaseMessagingService` 클래스를 확장하는 앱에서 처리되며 매니페스트 파일에서 다음과 같은 방법으로 선언됩니다.

```java
<service
    android:name=".MyFirebaseMessagingService"
    android:exported="false">
    <intent-filter>
        <action android:name="com.google.firebase.MESSAGING_EVENT" />
    </intent-filter>
</service>
```

>[!IMPORTANT]
>
>`onMessageReceived()` 구현이 포함된 클래스는 수신한 데이터를 처리합니다.

If the push message contains a Media URL, the URL will be available in the `RemoteMessage` parameter that is passed to the `onMessageReceived()` function. 사용할 키는 다음 코드 샘플에서와 같이 `attachment-url`입니다.

```java
public class MyFirebaseMessagingService extends FirebaseMessagingService {
        @Override
        public void onMessageReceived(RemoteMessage remoteMessage) {
      Log.d("Remote Message", "RemoteMessage: " + remoteMessage.toString());
            // Check if message contains a data payload.
            if (remoteMessage.getData().size() > 0) {
                Log.d("Remote Message", "RemoteMessage: " + remoteMessage.getData());
                sendNotification(remoteMessage);
            }
    }
 
private void sendNotification(RemoteMessage message) {
        Intent intent = new Intent(this, MainActivity.class);
    intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
    PendingIntent pendingIntent = PendingIntent.getActivity(this, 0 /* Request code */, intent, PendingIntent.FLAG_ONE_SHOT);

     String channelId = getString(R.string.default_notification_channel_id);
     Uri defaultSoundUri = RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION);
     NotificationCompat.Builder notificationBuilder =
                new NotificationCompat.Builder(this, channelId)
                        .setSmallIcon(R.drawable.ic_stat_ic_notification)
                        .setContentTitle(getString(R.string.fcm_message))
                        .setContentText(message.getData().get("body"))
                        .setAutoCancel(true)
                        .setSound(defaultSoundUri)
                        .setContentIntent(pendingIntent);
  
    //Handle image url if present in the push message 
        String attachmentUrl = message.getData().get("attachment-url");
  
    if (attachmentUrl != null) { 
    Bitmap image = getBitmapFromURL(attachmentUrl); 
    if (image != null) { 
      notificationBuilder.setStyle(new        NotificationCompat.BigPictureStyle().bigPicture(image)); 
        } 
        } 

     NotificationManager notificationManager =
              (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);

     // Since android Oreo notification channel is needed.
     if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
        NotificationChannel channel = new NotificationChannel(channelId,
                    "Channel human readable title",
                    NotificationManager.IMPORTANCE_DEFAULT);
            notificationManager.createNotificationChannel(channel);
     }

     notificationManager.notify(0 /* ID of notification */, notificationBuilder.build());
    }
}
```

>[!IMPORTANT]
>
>When you set `NotificationCompat.BigPictureStyle`, large images might not be displayed. 대형 이미지가 항상 표시되도록 하려면 기본 `Notification.BigPictureStyle`을 설정하십시오.

## Sample rich push notification {#section_6819316BEDDE45108413B541CA2BB2DC}

다음은 이미지가 포함된 리치 푸시 알림의 예입니다.

![](assets/rich-push-notification_example.png)

Android에서 사용하는 리치 푸시 알림에 대한 자세한 내용은 [다양한 알림으로 참여 유도](https://developer.android.com/distribute/best-practices/engage/rich-notifications.html)를 참조하십시오.
