---
product: mobile-services
audience: 최종 사용자
user-guide-title: Mobile Services Android 도움말
translation-type: tm+mt
source-git-commit: e3bbde6c27d583ff3ee8b7e86c8e6e73595f5067

---


# Mobile Services Android Help{#android}

+ [Experience Cloud 솔루션용 Android SDK 4.x](overview.md)
+ [릴리스 노트](rel-notes.md)
+ 시작하기{#getting-started-android}
   + [시작하기](getting-started/getting-started.md)
   + [시작하기 전에](getting-started/requirements.md)
   + [Core implementation and lifecycle](getting-started/dev-qs.md)
   + [Processing rules and context data](getting-started/proc-rules.md)
   + [Android 4.x 라이브러리로 마이그레이션](getting-started/migration-v3.md)
+ 구성{#configuration-android}
   + [Configuration overview](configuration/configuration.md)
   + [ADBMobile JSON config file](configuration/json-config/json-config.md)
   + [ADBMobile JSON 구성 경로 재정의](configuration/json-config/json-config-remote.md)
   + [히트 배치 처리](configuration/hit-batching.md)
   + [구성 방법](configuration/methods.md)
+ [라이프사이클 지표](metrics.md)
+ Analytics{#analytics-android}
   + [Analytics overview](analytics-main/analytics-main.md)
   + [앱 상태 추적](analytics-main/states.md)
   + [앱 작업 추적](analytics-main/actions.md)
   + [앱 충돌 추적](analytics-main/crashes.md)
   + [시간 작업](analytics-main/timed-actions.md)
   + [Visitor lifetime value](analytics-main/lifetime-value.md)
   + Products variable{#products-variable}
      + [제품 변수](analytics-main/products/products.md)
      + [머천다이징 eVar 및 제품별 이벤트가 포함된 제품 변수](analytics-main/products/products-variable-evars-events.md)
   + [이벤트 정리](analytics-main/event-serialization.md)
   + [Video Analytics](analytics-main/video-qs.md)
   + 포스트백{#postbacks}
      + [포스트백 개요](analytics-main/postbacks/postbacks.md)
      + [포스트백 예](analytics-main/postbacks/postback-example.md)
      + [PII 포스트백](analytics-main/postbacks/c-pii-postbacks.md)
   + [분석 방법](analytics-main/analytics-methods.md)
+ 획득{#acquisition-android}
   + [Acquisition overview](acquisition-main/acquisition-main-android.md)
   + [모바일 앱 확보](acquisition-main/acquisition.md)
   + [획득 방법](acquisition-main/acquisition-methods.md)
   + Tracking deep links{#tracking-deep-links}
      + [딥 링크 추적](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Tracking third-party deferred deep links](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deferred-deep-links.md)
   + [Marketing Link 획득 테스트](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [테스트 V3 획득](acquisition-main/t-testing-version-3-acquisition.md)
   + [기존 고객 확보 테스트](acquisition-main/t-testing-acquisition.md)
   + [획득 테스트 문제 해결](acquisition-main/troubleshoot-acquisition-testing.md)
+ 메시징{#messaging-android}
   + [Messaging overview](messaging-main/messaging-main-android.md)
   + 인앱 메시징{#inapp-messaging}
      + [인앱 메시징](messaging-main/messaging/messaging.md)
      + [Troubleshoot in-app messaging](messaging-main/messaging/in-apps-ts.md)
   + Push messaging{#push-messaging}
      + [푸시 메시지](messaging-main/push-messaging/push-messaging.md)
      + [Implement push messaging with deep linking](messaging-main/push-messaging/t-mob-impl-push-deeplinking-android-4x.md)
      + [Receive rich push notifications](messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
      + [푸시 메시지 문제 해결](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ 위치{#location}
   + [위치 개요](location/location.md)
   + [지리적 위치 및 관심 영역](location/geo-poi.md)
   + [비콘 추적](location/beacon.md)
+ Target{#target-android}
   + [Target 개요](target-main/target-main.md)
   + [타겟 구성](target-main/target.md)
   + [Target 메서드](target-main/c-target-methods.md)
   + [Android에서 오퍼 컨텐츠 미리 가져오기](target-main/c-mob-target-prefetch-android.md)
   + [Android에서 타겟 미리 보기](target-main/c-mob-target-preview-android.md)
+ Experience Cloud{#experience-cloud-android}
   + [Experience Cloud 개요](c-marketing-cloud/c-marketing-cloud.md)
   + [Experience Cloud ID 구성](c-marketing-cloud/mcvid.md)
   + [Adobe Experience Platform Identity Service methods](c-marketing-cloud/mc-methods.md)
   + [Experience Cloud Device Co-op](c-marketing-cloud/t-mob-mc-device-coop-android-.md)
+ Audience Manager{#audience-manager-android}
   + [Audience Manager 개요](audience-manager/audience-manager.md)
   + [Audience Manager configuration](audience-manager/audiencemgmt.md)
   + [Audience Manager 메서드](audience-manager/c-audience-manager-methods.md)
+ 웨어러블{#wearables-android}
   + [웨어러블 개요](wearables/wearables.md)
   + [Android 웨어러블:시작하기](wearables/android-wearable.md)
   + [Android 웨어러블:추가 참고 사항](wearables/c-android-wearables--additional-notes.md)
+ Android SDK reference{#sdk-reference-android}
   + [Android SDK 참조 개요](/help/android/reference/reference.md)
   + [앱 ID](/help/android/reference/app-ids.md)
   + [앱과 모바일 웹 간의 방문자 추적](/help/android/reference/hybrid-app.md)
   + [Android widgets](/help/android/reference/widgets.md)
+ 개인 정보 및 일반 데이터 보호 규정{#gdpr-privacy-android}
   + [개인 정보 및 GDPR 개요](c-mob-privacy-gdpr-android/c-mob-privacy-gdpr-android.md)
   + [Retrieving stored identifiers](c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)
   + [Setting the user's opt status](c-mob-privacy-gdpr-android/privacy.md)
+ PhoneGap 플러그인{#phonegap-android}
   + [PhoneGap 플러그인 개요](phonegap/phonegap.md)
   + [PhoneGap 플러그인 메서드](phonegap/phonegap-methods.md)
