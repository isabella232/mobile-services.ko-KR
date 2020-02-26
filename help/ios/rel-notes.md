---
description: Experience Cloud 솔루션용 iOS SDK 4.x에 대한 릴리스 노트 및 알려진 문제입니다.
seo-description: Experience Cloud 솔루션용 iOS SDK 4.x에 대한 릴리스 노트 및 알려진 문제입니다.
seo-title: 릴리스 노트
solution: Marketing Cloud,Analytics
title: 릴리스 노트
topic: Developer and implementation
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
translation-type: ht
source-git-commit: b608516b0103db3ae0eed1deaa4fb9733a98f7fa

---


# 릴리스 노트 {#release-notes}

다음은 Experience Cloud 솔루션용 iOS SDKs 4.x에 대한 릴리스 노트, 알려진 문제 및 핫픽스 정보입니다.

**2020년 2월 4일: 버전 4.19.0**

* 라이프사이클 - 일부 이전 iOS 장치에서 보고된 비정상적인 세션 길이 데이터를 완화하도록 새 API인 pauseCollectingLifecycleData를 추가했습니다.

**2019년 11월 8일: 버전 4.18.9**

* 앱 메시지 - 캐시된 이미지나 번들 이미지를 전체 화면 메시지에서 로드할 수 없는 버그를 수정했습니다.

**2019년 9월 20일: 버전 4.18.8**

* 앱 메시징:

   * iOS 10 이상을 실행하는 장치에서 이제 `UserNotifications` 프레임워크를 사용하여 `UserNotifications.framework`에 연결해야 하는 로컬 알림을 예약합니다.
   * 이제 전체 화면 메시지는 `WebKit.framework`의 WKWebViews를 사용합니다. WKWebViews를 사용하려면 Xcode 프로젝트에 연결되어 있어야 합니다.
   * 푸시 클릭스루 페이로드를 인앱 메시지의 트레이트로 사용할 수 없는 버그가 수정되었습니다.
   * 충돌 문제가 해결되었습니다.

* 일반 - SDK 데이터가 모든 Analytics 호출 시 쌍으로 연결된 watchOS 앱과 동기화되는 버그가 수정되었습니다.

**2019년 8월 2일: 버전 4.18.7**

* 일부 환경에서 11.0 이전 버전의 iOS를 실행하는 장치에서 충돌을 일으킨 버전 4.18.6에 도입된 변경 사항을 되돌렸습니다.

* Adobe Target: Target 요청으로 impressionId를 전송할 수 있는 `requestLocationParameters` 속성이 `ADBTargetRequestObject`에 추가되었습니다.

**2019년 7월 18일: 버전 4.18.6**

* Adobe Target: 이제 모든 요청에 클라이언트와 `sessionId` 매개 변수가 URL 쿼리 매개 변수에 포함됩니다.
* Adobe Target: 메모리 누수가 수정되었습니다.
* 방문자 ID 서비스: `visitorAppendToURL` 및 `visitorGetUrlVariablesAsync` API는 더 이상 반환 값을 이중 인코딩하지 않습니다.

   이중 인코딩으로 해당 API의 반환 값에 특정 보안 검토에 의한 플래그가 지정되었습니다.

**2019년 6월 5일: 버전 4.18.5**

* Analytics - 푸시 알림이 활성화되면 푸시 옵트인 상태가 라이프사이클 데이터에 추가됩니다.

**2019년 5월 24일: 버전 4.18.4**

* 방문자 ID 서비스 - 
   `visitorGetUrlVariablesAsync` API에 대한 반환 제한 시간이 30초로 늘어났습니다.

* 방문자 ID 서비스 - 이제 `setPushIdentifier` API가 호출될 때마다 방문자 ID 서비스에 동기화 호출을 보냅니다.

모든 솔루션의 현재 및 과거 릴리스 노트에 대한 자세한 내용은 [Adobe Experience Cloud 릴리스 노트](https://marketing.adobe.com/resources/help/ko_KR/whatsnew/)를 참조하십시오.
