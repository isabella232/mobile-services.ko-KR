---
description: Android 알림에 이미지 파일을 첨부할 수 있습니다. 시각적 구성 요소를 추가하면 푸시 알림을 통해 사용자의 참여도가 크게 높아질 수 있습니다.
seo-description: Android 알림에 이미지 파일을 첨부할 수 있습니다. 시각적 구성 요소를 추가하면 푸시 알림을 통해 사용자의 참여도가 크게 높아질 수 있습니다.
seo-title: 풍부한 푸시 알림 받기
title: 풍부한 푸시 알림 받기
uuid: 4a0340a6-666b-49b6-907a-9afc966dfdba
translation-type: tm+mt
source-git-commit: dca3663986b3ecc6e9fb736cc99513279715225c
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 60%

---


# 리치 푸시 알림 수신 {#receive-rich-push-notifications}

Android 알림에 이미지 파일을 첨부할 수 있습니다. 시각적 구성 요소를 추가하면 푸시 알림을 통해 사용자의 참여도가 크게 높아질 수 있습니다.

## 수신되는 리치 푸시 메시지 처리(FCM) {#section_AF1A3BC2312C4E1DA517CC90296C11E2}

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
>`onMessageReceived()` 구현이 포함된 클래스는 수신되는 데이터를 처리합니다.

푸시 메시지에 미디어 URL이 포함된 경우 해당 URL은 `onMessageReceived()` 함수에 전달되는 `RemoteMessage` 매개 변수에서 사용할 수 있습니다. 사용할 키는 다음 코드 샘플에서와 같이 `attachment-url`입니다.

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
>`NotificationCompat.BigPictureStyle`을 설정하면 큰 이미지가 표시되지 않을 수 있습니다. 대형 이미지가 항상 표시되도록 하려면 기본 `Notification.BigPictureStyle`을 설정하십시오.

## 리치 푸시 알림 샘플 {#section_6819316BEDDE45108413B541CA2BB2DC}

다음은 이미지가 포함된 리치 푸시 알림의 예입니다.

![](assets/rich-push-notification_example.png)

For more information about rich push notifications with Android, see [Engage with Rich Notifications](https://developer.android.com/distribute/best-practices/engage/rich-notifications.html).
