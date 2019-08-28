---
description: 이 정보를 통해 푸시 메시지 문제를 해결할 수 있습니다.
keywords: mobile
seo-description: 이 정보를 통해 푸시 메시지 문제를 해결할 수 있습니다.
seo-title: 푸시 메시지 문제 해결
solution: Marketing Cloud, Analytics
title: 푸시 메시지 문제 해결
topic: 지표
uuid: c 7 be 4 ab 7-0 cfe -4296-84 a 8-01412 f 4 fd 93 f
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Troubleshooting push messaging{#troubleshooting-push-messaging}

이 정보를 통해 푸시 메시지 문제를 해결할 수 있습니다.

## 푸시 메시지를 보내는 데 가끔 지연되는 이유는 무엇입니까?

다음 유형의 지연이 Mobile Services의 푸시 메시지와 관련 있을 수 있습니다.

* **Analytics 히트 대기 중**

   모든 보고서 세트에는 들어오는 Analytics 히트를 처리할 시기를 결정하는 설정이 있습니다. 기본값은 1시간마다입니다.

   Analytics 히트를 실제로 처리하는 데 최대 30분이 소요될 수 있지만, 일반적으로 15~20분 정도 걸립니다. 예를 들어, 보고서 세트는 매시간 히트를 처리합니다. 필요한 처리 시간을 최대 30분으로 계산하면 푸시 메시지에 수신 히트를 사용하는 데 최대 90분이 소요될 수 있습니다. 사용자가 오전 9:01에 앱을 시작했다면, 히트는 오전 10:15과 오전 10:30 사이에 새 고유 사용자로 Mobile Services UI에 표시됩니다.

* **푸시 서비스 대기**

   푸시 서비스(APNS 또는 GCM)가 메시지를 바로 전송하지 않을 수 있습니다. 드문 경우이지만, 최대 5~10분까지 대기 시간이 발생하는 경우가 있습니다. 푸시 메시지의 **[!UICONTROL 보고서]** 보기를 보고, **[!UICONTROL 메시지 내역]테이블에서 메시지를 찾고,**&#x200B;게시된] 수를 확인하여 푸시 메시지가 푸시 서비스에 전송되었는지 확인할 수 있습니다.**[!UICONTROL **

   >[!TIP]
   >
   >이 횟수는 푸시 서비스에 성공한 전송 수입니다. 푸시 서비스는 메시지가 전송될 것임을 보장하지 않습니다.

   서비스의 신뢰성에 대한 자세한 내용은 다음을 참조하십시오.

   * [서비스 품질](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5l)
   * [메시지 라이프타임](https://developers.google.com/cloud-messaging/concept-options#lifetime).

## Android GCM API 키가 유효하지 않은 이유는 무엇인가요?

* **잘못된 API 키**

   다음과 같은 이유로 API 키가 유효하지 않을 수 있습니다.

   * 제공한 API 키가 올바른 GCM API 키 값을 가진 서버 키가 아닙니다.
   * 서버 키는 IP를 허용 목록에 추가했으며, Adobe 서버가 푸시 메시지를 전송하지 않도록 차단하고 있습니다.

* **API 키의 유효성 확인**

   API 키의 유효성을 확인하려면 다음 명령을 실행하십시오.

   **Android**

   ```java
   # api_key=YOUR_API_KEY
   #curl--header"Authorization:key=$api_key"\
       --headerContent-Type:"application/json"\ 
       https://gcm-http.googleapis.com/gcm/send\
       -d"{\"registration_ids\":[\"ABC\"]}"
   ```

   401 HTTP 상태 코드가 반환되면 API 키가 유효하지 않은 것입니다. 아니면 다음 메시지와 유사한 메시지가 표시됩니다.

   ```java
   {"multicast_id":6782339717028231855,"success":0,"failure":1,
   canonical_ids":0,"results":[{"error":"InvalidRegistration"}]}
   ```

   You can also check the validity of a registration token by replacing `"ABC"` with the token.

## 내 APNS 인증서가 작동하지 않는 이유는 무엇입니까?

다음과 같은 이유로 APNS 인증서가 올바르지 않을 수 있습니다.

* 프로덕션 인증서 대신 샌드박스 인증서를 사용했을 수 있습니다.
* 지원되지 않는 새 프로덕션/샌드박스 인증서를 사용 중입니다.
* You are using `.p8` file instead of a `.p12` file.

## 푸시 메시지 오류 해결

**예**

다음 예는 VRS를 사용할 때 푸시 오류를 해결하는 방법을 보여 줍니다.

다음 고객에게는 두 개의 iOS 앱이 제공됩니다.

* 앱 이름: PhotoShop_app_iOS
   * 상위 RSID: AllAdobe PhotoShop_apps
   * VRSID: PhotoShop_iOS_app_SF
   * VRSID 정의 세그먼트: `a.appid contains “PhotoShop_iOS_app_SF”`
* 앱 이름: PhotoShop_app_iOS
   * 상위 RSID: AllAdobe PhotoShop_apps
   * RSID: photoshop_ ios_ app_ la
   * VRSID 정의 세그먼트: `a.os contains “iOS”`

In this example, if a Photoshop employee sends a push to the *PhotoShop_iOS_app_SF* app, all *PhotoShop_iOS_app_SF app* users receive the push message as expected. But, if the employee sends a message to the *PhotoShop_iOS_app_LA* app, because its VRSID Definition Segment is incorrect (`iOS` instead of `a.os contains "PhotoShop_iOS_app_LA"`), the message is sent to **all** iOS users in *AllAdobe PhotoShop_apps*. Although the message still goes to *PhotoShop_iOS_app_LA* users, the message also blacklists the push IDs for *PhotoShop_iOS_app_SF* users because the *PhotoShop_iOS_app_SF* app has a different certificate. If the segment had been defined as `a.os contains “PhotoShop_iOS_app_LA”`, the push message would have been sent to only *PhotoShop_iOS_app_LA* users.

*photoshop_ ios_ app_ la* 푸시 인증서와 함께 전달된 경우 *photoshop_ ios_ app_ sf에 대한 푸시 식별자는 다른 이름으로* `invalid`돌아옵니다.

>[!CAUTION]
>
>After you create a push message for an app that is using a VRS and click **[!UICONTROL Save &amp; Send]**, an alert appears that reminds you ensure that each app that is listed **must** have a valid certificate. 각 앱에 유효한 인증서가 **없으면** 대상 세그먼트가 무한정 차단된 상태일 수 있으므로 이후 푸시 메시지를 영향을 받는 사용자에게 보내지 못할 수 있습니다. 대상 세그먼트에 대한 자세한 내용은 [대상을 참조하십시오. 푸시 메시지의 대상 옵션을 정의하고 구성합니다](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).
