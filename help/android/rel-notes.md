---
description: Experience Cloud 솔루션용 Android SDK 4.x를 위한 릴리스 노트 및 알려진 문제.
seo-description: Experience Cloud 솔루션용 Android SDK 4.x를 위한 릴리스 노트 및 알려진 문제.
seo-title: 릴리스 노트
solution: Marketing Cloud, Analytics
title: 릴리스 노트
topic: 개발자 및 구현
uuid: 16 BB 4 DE 8-A 216-47 A 8-928 C -0 B 1 E 1421 ADCF
translation-type: tm+mt
source-git-commit: 4c68e3fb3687a555fc7fdfa50a42e837b76a7d88

---


# 릴리스 노트 {#release-notes}

다음은 Experience Cloud 솔루션용 Android SDK 4. x에 대한 릴리스 노트, 알려진 문제 및 핫픽스 정보입니다.

**2019 년 8 월 2 일: 버전 4.17.9**

* 방문자 ID 서비스: Syncidentifiers를 호출할 때 `StrictMode` 위반이 수정되었습니다.

   이 문제는 주 스레드에서 공유 기본 설정을 읽음으로써 발생했습니다.

* Adobe Target: target 요청과 함께 impressionid를 보낼 수 있는에 `requestLocationParameters``TargetRequestObject`속성이 추가되었습니다.

**2019 년 7 월 18 일: 버전 4.17.8**

* Adobe Target: 이제 모든 요청이 URL 쿼리 매개 변수에 클라이언트 및 sessionid를 포함합니다.
* 인앱 메시징: 메시지가 빈 클릭 광고 URL로 인해 트리거되면 Android 앱이 충돌하던 문제가 수정되었습니다.
* 방문자 ID 서비스: `Visitor.appendToURL` 및 `Visitor.getUrlVariablesAsync` API는 더 이상 반환 값을 이중 인코딩하지 않습니다.

   이중 인코딩으로 해당 API의 반환 값에 특정 보안 검토에 의한 플래그가 지정되었습니다.

**2019 년 6 월 6 일: 버전 4.17.7**

* 일반 - 20 보다 낮은 Android API 수준의 네트워크 호출은 이제 TLS 1.1 또는 TLS 1.2를 사용합니다.
* Analytics - 푸시 알림이 활성화되면 라이프사이클 데이터에 푸시 옵트인 상태가 추가되었습니다.

**2019 년 5 월 24 일: 버전 4.17.6**

* 방문자 ID 서비스 -
   `setPushIdentifier` 이제 API 호출이 호출될 때마다 방문자 ID 서비스에 동기화 호출을 보냅니다.

* 방문자 ID 서비스 - 2 초에서 5 초로 연결 및 읽기
시간을 늘렸습니다.


모든 솔루션의 현재 및 과거 릴리스 노트에 대한 자세한 내용은 [Adobe Experience Cloud 릴리스 노트](https://marketing.adobe.com/resources/help/en_US/whatsnew/)를 참조하십시오.
