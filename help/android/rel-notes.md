---
description: Experience Cloud 솔루션용 Android SDK 4.x를 위한 릴리스 노트 및 알려진 문제.
seo-description: Experience Cloud 솔루션용 Android SDK 4.x를 위한 릴리스 노트 및 알려진 문제.
seo-title: 릴리스 노트
solution: Marketing Cloud,Analytics
title: 릴리스 노트
topic: 개발자 및 구현
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
translation-type: tm+mt
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# 릴리스 노트 {#release-notes}

다음은 Experience Cloud 솔루션용 Android SDK 4.x에 대한 릴리스 노트, 알려진 문제 및 핫픽스 정보입니다.

**2019년 9월 20일:버전 4.17.10**

* 일반:Android API 레벨 21 이상에서 일부 영역에 대한 로케일 문자열 생성을 수정했습니다.

**2019년 7월 18일:버전 4.17.8**

* Adobe Target:이제 모든 요청에 URL 쿼리 매개 변수에 클라이언트와 sessionId가 포함됩니다.
* 인앱 메시징: 메시지가 빈 클릭 광고 URL로 인해 트리거되면 Android 앱이 충돌하던 문제가 수정되었습니다.
* 방문자 ID 서비스: `Visitor.appendToURL` 및 `Visitor.getUrlVariablesAsync` API는 더 이상 반환 값을 이중 인코딩하지 않습니다.

   이중 인코딩으로 해당 API의 반환 값에 특정 보안 검토에 의한 플래그가 지정되었습니다.

**2019년 6월 6일:버전 4.17.7**

* 일반 - Android API 수준 20보다 낮은 네트워킹 호출은 이제 TLS 1.1 또는 TLS 1.2를 사용합니다.
* Analytics - 푸시 알림이 활성화되면 푸시 옵트인 상태를 라이프사이클 데이터에 추가합니다.

**2019년 5월 24일:버전 4.17.6**

* 방문자 ID 서비스 -
   `setPushIdentifier` 이제 API 호출이 호출될 때마다 방문자 ID 서비스로 비동기 호출을 전송합니다.

* 방문자 ID 서비스 - 연결 및 읽기 제한을 2초에서 5초로 늘렸습니다.


모든 솔루션의 현재 및 과거 릴리스 노트에 대한 자세한 내용은 [Adobe Experience Cloud 릴리스 노트](https://marketing.adobe.com/resources/help/en_US/whatsnew/)를 참조하십시오.
