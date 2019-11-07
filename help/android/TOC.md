---
product: mobile-services
audience: 최종 사용자
user-guide-title: Mobile Services Android 도움말
translation-type: ht
source-git-commit: e3bbde6c27d583ff3ee8b7e86c8e6e73595f5067

---


# Mobile Services Android 도움말{#android}

+ [Experience Cloud 솔루션용 Android SDK 4.x](overview.md)
+ [릴리스 노트](rel-notes.md)
+ 시작하기{#getting-started-android}
   + [시작하기](getting-started/getting-started.md)
   + [시작하기 전에](getting-started/requirements.md)
   + [핵심 구현 및 라이프사이클](getting-started/dev-qs.md)
   + [처리 규칙 및 컨텍스트 데이터](getting-started/proc-rules.md)
   + [Android 4.x 라이브러리로 마이그레이션](getting-started/migration-v3.md)
+ 구성{#configuration-android}
   + [구성 개요](configuration/configuration.md)
   + [ADBMobile JSON 구성 파일](configuration/json-config/json-config.md)
   + [ADBMobile JSON 구성 경로 재정의](configuration/json-config/json-config-remote.md)
   + [히트 배치 처리](configuration/hit-batching.md)
   + [구성 메서드](configuration/methods.md)
+ [라이프사이클 지표](metrics.md)
+ Analytics{#analytics-android}
   + [Analytics 개요](analytics-main/analytics-main.md)
   + [앱 상태 추적](analytics-main/states.md)
   + [앱 작업 추적](analytics-main/actions.md)
   + [앱 충돌 추적](analytics-main/crashes.md)
   + [시간 작업](analytics-main/timed-actions.md)
   + [방문자 라이프타임 값](analytics-main/lifetime-value.md)
   + Products 변수{#products-variable}
      + [Products 변수](analytics-main/products/products.md)
      + [머천다이징 eVar 및 제품별 이벤트가 포함된 Products 변수](analytics-main/products/products-variable-evars-events.md)
   + [이벤트 정리](analytics-main/event-serialization.md)
   + [Video Analytics](analytics-main/video-qs.md)
   + 포스트백{#postbacks}
      + [포스트백 개요](analytics-main/postbacks/postbacks.md)
      + [포스트백 예시](analytics-main/postbacks/postback-example.md)
      + [PII 포스트백](analytics-main/postbacks/c-pii-postbacks.md)
   + [Analytics 메서드](analytics-main/analytics-methods.md)
+ 획득{#acquisition-android}
   + [획득 개요](acquisition-main/acquisition-main-android.md)
   + [모바일 앱 획득](acquisition-main/acquisition.md)
   + [획득 메서드](acquisition-main/acquisition-methods.md)
   + 딥링크 추적{#tracking-deep-links}
      + [딥링크 추적](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [타사의 지연된 딥링크 추적](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deferred-deep-links.md)
   + [마케팅 링크 획득 테스트](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [V3 획득 테스트](acquisition-main/t-testing-version-3-acquisition.md)
   + [기존 획득 테스트 ](acquisition-main/t-testing-acquisition.md)
   + [획득 테스트 문제 해결](acquisition-main/troubleshoot-acquisition-testing.md)
+ 메시징{#messaging-android}
   + [메시징 개요](messaging-main/messaging-main-android.md)
   + 인앱 메시징{#inapp-messaging}
      + [인앱 메시징](messaging-main/messaging/messaging.md)
      + [인앱 메시징 문제 해결](messaging-main/messaging/in-apps-ts.md)
   + 푸시 메시지{#push-messaging}
      + [푸시 메시지](messaging-main/push-messaging/push-messaging.md)
      + [딥링크로 푸시 메시지 구현](messaging-main/push-messaging/t-mob-impl-push-deeplinking-android-4x.md)
      + [리치 푸시 알림 수신](messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
      + [푸시 메시지 문제 해결](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ 위치{#location}
   + [위치 개요](location/location.md)
   + [지리적 위치 및 관심 영역](location/geo-poi.md)
   + [비콘 추적](location/beacon.md)
+ Target{#target-android}
   + [Target 개요](target-main/target-main.md)
   + [Target 구성](target-main/target.md)
   + [Target 메서드](target-main/c-target-methods.md)
   + [Android에서 오퍼 콘텐츠 미리 가져오기](target-main/c-mob-target-prefetch-android.md)
   + [Android에서 타겟 미리 보기](target-main/c-mob-target-preview-android.md)
+ Experience Cloud{#experience-cloud-android}
   + [Experience Cloud 개요](c-marketing-cloud/c-marketing-cloud.md)
   + [Experience Cloud ID 구성](c-marketing-cloud/mcvid.md)
   + [Adobe Experience Platform ID 서비스 메서드](c-marketing-cloud/mc-methods.md)
   + [Experience Cloud Device Co-op](c-marketing-cloud/t-mob-mc-device-coop-android-.md)
+ Audience Manager{#audience-manager-android}
   + [Audience Manager 개요](audience-manager/audience-manager.md)
   + [Audience Manager 구성](audience-manager/audiencemgmt.md)
   + [Audience Manager 메서드](audience-manager/c-audience-manager-methods.md)
+ 웨어러블{#wearables-android}
   + [웨어러블 개요](wearables/wearables.md)
   + [Android 웨어러블 기기: 시작하기](wearables/android-wearable.md)
   + [Android 웨어러블 기기: 추가 참고 사항](wearables/c-android-wearables--additional-notes.md)
+ Android SDK 참조{#sdk-reference-android}
   + [Android SDK 참조 개요](/help/android/reference/reference.md)
   + [앱 ID](/help/android/reference/app-ids.md)
   + [앱과 모바일 웹 간 방문자 추적](/help/android/reference/hybrid-app.md)
   + [Android 위젯](/help/android/reference/widgets.md)
+ 개인 정보 및 일반 데이터 보호 규정{#gdpr-privacy-android}
   + [개인 정보 및 GDPR 개요](c-mob-privacy-gdpr-android/c-mob-privacy-gdpr-android.md)
   + [저장된 식별자 검색](c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)
   + [사용자의 옵트 상태 설정](c-mob-privacy-gdpr-android/privacy.md)
+ PhoneGap 플러그인{#phonegap-android}
   + [PhoneGap 플러그인 개요](phonegap/phonegap.md)
   + [PhoneGap 플러그인 메서드](phonegap/phonegap-methods.md)
