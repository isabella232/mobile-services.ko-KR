---
description: Adobe Mobile 및 Adobe Mobile SDK를 사용하면 푸시 메시지를 사용자에게 보낼 수 있습니다. 또한 SDK를 사용하면 푸시 메시지를 통해 클릭하여 앱을 연 사용자를 쉽게 보고할 수 있습니다.
seo-description: Adobe Mobile 및 Adobe Mobile SDK를 사용하면 푸시 메시지를 사용자에게 보낼 수 있습니다. 또한 SDK를 사용하면 푸시 메시지를 통해 클릭하여 앱을 연 사용자를 쉽게 보고할 수 있습니다.
seo-title: 푸시 메시지
solution: Experience Cloud,Analytics
title: 푸시 메시지
topic: Developer and implementation
uuid: 729d4010-3733-4dff-b188-ad45bd3e7cc4
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '439'
ht-degree: 100%

---


# 푸시 메시지 {#push-messaging}

Adobe Mobile 및 Adobe Mobile SDK를 사용하면 푸시 메시지를 사용자에게 보낼 수 있습니다. 또한 SDK를 사용하면 푸시 메시지를 통해 클릭하여 앱을 연 사용자를 쉽게 보고할 수 있습니다.

푸시 메시지를 사용하려면 **반드시** SDK 버전 4.6 이상이 있어야 합니다.

>[!IMPORTANT]
>
>앱 내의 Experience Cloud ID를 수동으로 설정하지 마십시오. 이로 인해 옵트인 상태 때문에 푸시 메시지를 받지 않는 고유한 사용자가 새로 생성됩니다. 예를 들어, 푸시 메시지를 수신하도록 옵트인한 사용자가 앱에 로그인합니다. 로그인 후 앱 내에서 ID를 수동으로 설정하는 경우 푸시 메시지 수신을 선택하지 않은 새로운 고유 사용자가 만들어집니다. 이 새로운 사용자는 푸시 메시지를 수신하지 않습니다.
>
>앱을 새 보고서 세트로 이동할 수 없습니다. 새 보고서 세트로 마이그레이션하는 경우 푸시 구성이 중단되고 메시지가 전송되지 않을 수 있습니다.

## 푸시 메시지 활성화 {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

>[!TIP]
>
>FCM(Firebase Cloud Messaging)을 통해 메시지를 사용하도록 앱을 이미 설정했을 경우 다음 단계 중 일부가 이미 완료되었을 수 있습니다.

1. `ADBMobileConfig.json` 파일에 푸시 메시지에 대한 필수 설정이 포함되어 있는지 확인합니다.

   `"marketingCloud"` 개체에는 푸시 메시지용으로 구성된 `"org"` 속성이 있어야 합니다.

   ```js
   "marketingCloud": { 
     "org": <org-id-string> 
    }
   ```

1. Firebase Cloud Messaging(FCM) API를 사용하여 등록 ID/토큰을 얻습니다.

   * FCM 설정에 대한 자세한 내용은 [Android용 Firebase Cloud 메시지 클라이언트 앱 설정](https://firebase.google.com/docs/cloud-messaging/android/client)을 참조하십시오.

   ```js
   String token = FirebaseInstanceId.getInstance().getToken();
   ```

1. 등록 ID/토큰은 `Config.setPushIdentifier(final String registrationId)` 메서드를 사용하여 SDK에 전달해야 합니다.

   ```js
   Config.setPushIdentifier(token); // token was obtained in step 2
   ```

1. `collectLifecycleData` 메서드의 활동을 전달하여 보고 기능을 활성화합니다.

   푸시 클릭스루 보고 기능을 활성화하기 위한 요구 사항은 다음과 같습니다.

   * `FireBaseMessageService` 구현 시 RemoteMessage 개체와 함께 `onMessageReceived` 메서드에 전달된 메시지 데이터가 포함된 번들 개체를 클릭스루시 타겟 활동을 여는 데 사용하는 인텐트에 추가해야 합니다. 이 작업은 `putExtras` 메서드를 사용하여 수행할 수 있습니다. 자세한 내용은 [putExtras](https://developer.android.com/reference/android/content/Intent.html#putExtras(android.os.Bundle))를 참조하십시오.

   ```java
   Intent intent = new Intent(this, MainActivity.class);
      intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
   // get the bundle from the RemoteMessage object
      intent.putExtras(message.toIntent().getExtras());
   ```

   * 클릭스루 타겟 활동에서 `collectLifecycleData` 호출을 사용하여 해당 활동을 SDK에 전달해야 합니다.

      다음 정보를 숙지하십시오.

      * `Config.collectLifecycleData(this)` 또는 `Config.collectLifecycleData(this, contextData)`를 사용합니다.

      * `Config.collectLifecycleData()`를 사용하지 **마십시오**.



