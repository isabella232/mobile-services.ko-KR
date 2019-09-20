---
description: Experience Cloud 솔루션용 iOS SDK 4.x에 대한 릴리스 노트 및 알려진 문제입니다.
seo-description: Experience Cloud 솔루션용 iOS SDK 4.x에 대한 릴리스 노트 및 알려진 문제입니다.
seo-title: 릴리스 노트
solution: Marketing Cloud,Analytics
title: 릴리스 노트
topic: 개발자 및 구현
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
translation-type: tm+mt
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# 릴리스 노트 {#release-notes}

다음은 Experience Cloud 솔루션용 iOS SDK 4.x에 대한 릴리스 노트, 알려진 문제 및 핫픽스 정보입니다.

**2019년 9월 20일:버전 4.18.8**

* 앱 메시지:

   * iOS 10 이상을 실행하는 장치에서 이제 프레임워크를 사용하여 앱에 연결된 앱에 대한 로컬 알림을 예약합니다 `UserNotifications` `UserNotifications.framework`.
   * 이제 전체 화면 메시지는 WKWebViews를 사용합니다. `WebKit.framework`이 보고서는 Xcode 프로젝트에 연결되어 있어야 합니다.
   * 푸시 클릭스루 페이로드를 인앱 메시징의 트레이트로 사용할 수 없었던 버그가 수정되었습니다.
   * 충돌 문제가 수정되었습니다.

* 일반 - 모든 Analytics 호출에서 SDK 데이터가 쌍으로 설정된 watchOS 앱과 동기화된 버그를 수정했습니다.

**2019년 8월 2일:버전 4.18.7**

* 일부 환경에서 11.0 이전 버전의 iOS를 실행하는 장치에서 충돌이 발생하던 버전 4.18.6에 도입된 변경을 되돌렸습니다.

* Adobe Target:Target 요청과 함께 impressionId를 전송할 수 `requestLocationParameters` `ADBTargetRequestObject`있는 속성을 에 추가했습니다.

**2019년 7월 18일:버전 4.18.6**

* Adobe Target: 이제 모든 요청에 클라이언트와 `sessionId` 매개 변수가 URL 쿼리 매개 변수에 포함됩니다.
* Adobe Target: 메모리 누수가 수정되었습니다.
* 방문자 ID 서비스: `visitorAppendToURL` 및 `visitorGetUrlVariablesAsync` API는 더 이상 반환 값을 이중 인코딩하지 않습니다.

   이중 인코딩으로 해당 API의 반환 값에 특정 보안 검토에 의한 플래그가 지정되었습니다.

**2019년 6월 5일:버전 4.18.5**

* Analytics - 푸시 알림이 활성화되면 푸시 옵트인 상태를 라이프사이클 데이터에 추가합니다.

**2019년 5월 24일:버전 4.18.4**

* 방문자 ID 서비스 -
   `visitorGetUrlVariablesAsync` API에서 30초 사이

* 방문자 ID 서비스 - `setPushIdentifier` 이제 API 호출이 호출될 때마다 방문자 ID 서비스에 동기화 호출을 보냅니다.

모든 솔루션의 현재 및 과거 릴리스 노트에 대한 자세한 내용은 [Adobe Experience Cloud 릴리스 노트](https://marketing.adobe.com/resources/help/en_US/whatsnew/)를 참조하십시오.
