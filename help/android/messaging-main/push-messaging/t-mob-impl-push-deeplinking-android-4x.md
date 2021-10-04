---
description: Adobe Mobile Services UI에서 딥링크 URL을 구성하면 이 URL은 adb_deeplink 키를 사용하여 푸시 페이로드에 저장됩니다.
title: 딥 링크로 푸시 메시지 구현
uuid: e24f9248-8d48-4e57-84af-3a05b72e2a09
exl-id: ab97db32-d9d2-41ec-aae8-a951c7745df8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 74%

---

# 딥링크로 푸시 메시지 구현 {#implement-push-messaging-with-deep-linking}

Adobe Mobile Services UI에서 딥링크 URL을 구성하면 이 URL은 adb_deeplink 키를 사용하여 푸시 페이로드에 저장됩니다.

URL은 `FirebaseMessagingService`에서 `remoteMessage.getData().get("adb_deeplink")`을 호출하여 가져올 수 있습니다.

>[!TIP]
>
>페이로드에 딥링크 URL이 있는지 여부에 따라 다양한 의도를 정의할 수 있습니다.

1. 다음 작업 중 하나를 완료하십시오.

   * 딥링크 URL이 푸시 페이로드 내에 **있을** 경우 URL이 포함된 `ACTION_VIEW` 인텐트를 생성하십시오.

      사용자가 푸시 메시지를 클릭하면 딥 링크가 트리거됩니다.

   * 푸시 페이로드에서 딥 연결 URL **이**&#x200B;이 아닌 경우 활동 중 하나를 여는 의도를 만드십시오.

## 예

다음은 `FirebaseMessagingService`에서 확장하는 클래스에 대한 샘플 구현입니다.

```java
public void onMessageReceived(RemoteMessage message) { 
 
       Map<String, String> data = message.getData(); 
       String messageStr = data.get("message"); 
       String deepLink = data.get("adb_deeplink"); 
 
       sendNotification(deepLink, messageStr, data); 
    } 
 
private void sendNotification(String deeplink, String message, Map<String, String> data) { 
       Intent intent; 
 
       if (deeplink!=null) { 
           intent = new Intent(Intent.ACTION_VIEW, Uri.parse(deeplink)); 
       } else { 
           intent = new Intent(this, MainActivity.class); 
       } 
 
       intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP); 
 
       //put the data map into the intent to track clickthroughs 
       Bundle pushData = new Bundle(); 
       Set<String> keySet = data.keySet(); 
       for (String key : keySet) { 
           pushData.putString(key, data.get(key)); 
       } 
 
       intent.putExtras(pushData); 
 
       PendingIntent pendingIntent = PendingIntent.getActivity(this, 0, intent, 
               PendingIntent.FLAG_ONE_SHOT); 
 
       Uri defaultSoundUri= RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION); 
 
       NotificationCompat.Builder notificationBuilder = new NotificationCompat.Builder(this) 
                .setSmallIcon(R.drawable.icon) 
                .setContentTitle("FCM Deep Link Push") 
                .setContentText(message) 
                .setAutoCancel(true) 
                .setSound(defaultSoundUri) 
                .setContentIntent(pendingIntent); 
 
       NotificationManager notificationManager =  
       (NotificationManager)getApplicationContext().getSystemService(Context.NOTIFICATION_SERVICE); 
           notificationManager.notify(0, notificationBuilder.build()); 
       } 
```
