---
description: 이 정보를 통해 푸시 메시지 문제를 해결할 수 있습니다.
keywords: mobile
seo-description: 이 정보를 통해 푸시 메시지 문제를 해결할 수 있습니다.
seo-title: 푸시 메시지 문제 해결
solution: Marketing Cloud,Analytics
title: 푸시 메시지 문제 해결
topic: Metrics
uuid: c7be4ab7-0cfe-4296-84a8-01412f4fd93f
translation-type: ht
source-git-commit: 86ba045b44bf6553e80727c0d61ccdd9a552d16c
workflow-type: ht
source-wordcount: '735'
ht-degree: 100%

---


# 푸시 메시지 문제 해결{#troubleshooting-push-messaging}

이 정보를 통해 푸시 메시지 문제를 해결할 수 있습니다.

## 푸시 메시지를 보내는 데 가끔 지연되는 이유는 무엇입니까?

다음 유형의 지연이 Mobile Services의 푸시 메시지와 관련 있을 수 있습니다.

* **Analytics 히트 대기 중**

   모든 보고서 세트에는 들어오는 Analytics 히트를 처리할 시기를 결정하는 설정이 있습니다. 기본값은 1시간마다입니다.

   Analytics 히트를 실제로 처리하는 데 최대 30분이 소요될 수 있지만, 일반적으로 15~20분 정도 걸립니다. 예를 들어, 보고서 세트는 매 시간마다 히트를 처리합니다. 최대 30분의 필요한 처리 시간을 평가하는 경우 푸시 메시지에 사용할 수 있는 수신 히트에 대해 최대 90분이 소요될 수 있습니다. 사용자가 오전 9:01에 앱을 시작했다면, 히트는 오전 10:15과 오전 10:30 사이에 새 고유 사용자로 Mobile Services UI에 표시됩니다.

* **푸시 서비스 대기 중**

   푸시 서비스(APNS 또는 GCM)가 메시지를 곧바로 발송하지 않을 수 있습니다. 드문 경우이지만, 최대 5~10분까지 대기 시간이 발생하는 경우가 있습니다. 푸시 메시지의 **[!UICONTROL 보고서]** 보기를 보고, **[!UICONTROL 메시지 내역]** 테이블에서 메시지를 찾고, **[!UICONTROL 게시된]** 수를 확인하여 푸시 메시지가 푸시 서비스에 전송되었는지 확인할 수 있습니다.

   >[!TIP]
   >
   >이 수는 푸시 서비스에 성공적으로 전송된 수입니다. 푸시 서비스는 메시지가 전송될 것임을 보장하지 않습니다.

   서비스의 안정성에 대한 자세한 내용은 다음을 참조하십시오.

   * [서비스 품질](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5l)
   * [메시지 수명](https://developers.google.com/cloud-messaging/concept-options#lifetime).

## Android GCM API 키가 유효하지 않은 이유는 무엇입니까?

* **유효하지 않은 API 키**

   다음 이유로 인해 API 키가 유효하지 않을 수 있습니다.

   * 제공한 API 키가 올바른 GCM API 키 값을 가진 서버 키가 아닙니다.
   * 서버 키는 IP를 허용하고 Adobe 서버에서 푸시 메시지를 전송하지 못하도록 차단합니다.

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

   반환된 401 HTTP 상태 코드에 따르면 API 키가 유효하지 않습니다. 그렇지 않으면, 다음과 유사한 메시지가 제공됩니다.

   ```java
   {"multicast_id":6782339717028231855,"success":0,"failure":1,
   canonical_ids":0,"results":[{"error":"InvalidRegistration"}]}
   ```

   `"ABC"`를 토큰으로 대체하여 등록 토큰의 유효성을 확인할 수도 있습니다.

## 내 APNS 인증서가 작동하지 않는 이유는 무엇입니까?

다음 이유로 인해 APNS 인증서가 유효하지 않을 수 있습니다.

* 프로덕션 인증서 대신 샌드박스 인증서를 사용하고 있을 수 있습니다.
* 지원되지 않는 새 프로덕션/샌드박스 인증서를 사용하고 있습니다.
* `.p12` 파일 대신 `.p8` 파일을 사용 중입니다.

## 푸시 메시지 오류 해결

**예제**

다음 예에서는 VRS를 사용할 때 푸시 오류를 해결하는 방법을 보여 줍니다.

다음 고객에게는 두 개의 iOS 앱이 있습니다.

* 앱 이름: PhotoShop_app_iOS
   * 상위 RSID: AllAdobe PhotoShop_apps
   * VRSID: PhotoShop_iOS_app_SF
   * VRSID 정의 세그먼트: `a.appid contains “PhotoShop_iOS_app_SF”`
* 앱 이름: PhotoShop_app_iOS
   * 상위 RSID: AllAdobe PhotoShop_apps
   * RSID: PhotoShop_iOS_app_LA
   * VRSID 정의 세그먼트: `a.os contains “iOS”`

이 예에서는 Photoshop 직원이 *PhotoShop_iOS_app_SF* 앱으로 푸시를 보내면 모든 *PhotoShop_iOS_app_SF* 앱 사용자가 예상대로 푸시 메시지를 받습니다. 그러나 직원이 *PhotoShop_iOS_app_LA* 앱으로 메시지를 보내는 경우 해당 VRSID 정의 세그먼트가 올바르지 않기 때문에(`a.os contains "PhotoShop_iOS_app_LA"` 대신 `iOS`) *AllAdobe PhotoShop_apps*&#x200B;의 **모든** iOS 사용자에게 메시지가 전송됩니다. 메시지가 여전히 *PhotoShop_iOS_app_LA* 사용자에게 이동하지만, *PhotoShop_iOS_app_SF* 앱에는 다른 인증서가 있으므로 메시지는 *PhotoShop_iOS_app_SF* 사용자의 푸시 ID를 차단 목록에 추가합니다. 세그먼트가 `a.os contains “PhotoShop_iOS_app_LA”`로 정의된 경우 푸시 메시지가 *PhotoShop_iOS_app_LA* 사용자에게만 전송되었을 수 있습니다.

*PhotoShop_IOS_app_LA* 푸시 인증서와 함께 전달된 경우 *PhotoShop_iOS_app_SF*&#x200B;에 대한 푸시 식별자가 다시 `invalid`으로 표시됩니다.

>[!CAUTION]
>
>VRS를 사용하는 앱에 대한 푸시 메시지를 만들고 **[!UICONTROL 저장 및 보내기]**&#x200B;를 클릭하면 나열된 각 앱에 올바른 인증서가 **있는지** 확인하라는 경고가 표시됩니다. 각 앱에 유효한 인증서가 **없으면** 대상 세그먼트가 무한정 차단된 상태일 수 있으므로 이후 푸시 메시지를 영향을 받는 사용자에게 보내지 못할 수 있습니다. 대상 세그먼트에 대한 자세한 내용은 [대상: 푸시 메시지에 대한 대상 옵션 정의 및 구성](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md)을 참조하십시오.
