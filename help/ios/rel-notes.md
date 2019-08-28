---
description: Experience Cloud 솔루션용 iOS SDK 4.x에 대한 릴리스 노트 및 알려진 문제입니다.
seo-description: Experience Cloud 솔루션용 iOS SDK 4.x에 대한 릴리스 노트 및 알려진 문제입니다.
seo-title: 릴리스 노트
solution: Marketing Cloud, Analytics
title: 릴리스 노트
topic: 개발자 및 구현
uuid: E 1613 DC 5-02 A 4-43 A 7-997 A -29 B 4 DE 98 B 4 D 1
translation-type: tm+mt
source-git-commit: 80a60276f9926177c8958b8e87e9393a83e7e6a9

---


# 릴리스 노트 {#release-notes}

다음은 Experience Cloud 솔루션용 iOS SDK 4. x에 대한 릴리스 노트, 알려진 문제 및 핫픽스 정보입니다.

**2019 년 8 월 2 일: 버전 4.18.7**

* 일부 환경에서 11.0 이전 버전을 실행하는 장치에서 충돌이 발생하던 4.18.6 버전에서 도입된 변경 사항을 되돌렸습니다.

* Adobe Target: Target 요청과 함께 impressionid를 보낼 수 있는에 `requestLocationParameters``ADBTargetRequestObject`속성이 추가되었습니다.

**2019 년 7 월 18 일: 버전 4.18.6**

* Adobe Target: 이제 모든 요청에 클라이언트와 `sessionId` 매개 변수가 URL 쿼리 매개 변수에 포함됩니다.
* Adobe Target: 메모리 누수가 수정되었습니다.
* 방문자 ID 서비스: `visitorAppendToURL` 및 `visitorGetUrlVariablesAsync` API는 더 이상 반환 값을 이중 인코딩하지 않습니다.

   이중 인코딩으로 해당 API의 반환 값에 특정 보안 검토에 의한 플래그가 지정되었습니다.

**2019 년 6 월 5 일: 버전 4.18.5**

* 분석 - 푸시 알림이 활성화되면 라이프사이클 데이터에 푸시 옵트인 상태를 추가합니다.

**2019 년 5 월 24 일: 버전 4.18.4**

* 방문자 ID 서비스 -
   `visitorGetUrlVariablesAsync` API는 30 초입니다.

* 방문자 ID 서비스 - 이제 `setPushIdentifier` API 호출이 호출될 때마다 방문자 ID 서비스에 동기화 호출을 보냅니다.

모든 솔루션의 현재 및 과거 릴리스 노트에 대한 자세한 내용은 [Adobe Experience Cloud 릴리스 노트](https://marketing.adobe.com/resources/help/en_US/whatsnew/)를 참조하십시오.
