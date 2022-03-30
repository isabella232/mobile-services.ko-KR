---
description: Experience Cloud 솔루션용 Android SDK 4.x에 대한 릴리스 노트 및 알려진 문제
solution: Experience Cloud Services,Analytics
title: 릴리스 노트
topic-fix: Developer and implementation
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
exl-id: 5cc3d031-5952-4e9b-b551-9402d3c05ccb
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 72%

---

# 릴리스 정보 {#release-notes}

다음은 Experience Cloud 솔루션용 Android SDK 4.x에 대한 릴리스 노트, 알려진 문제 및 핫픽스 정보입니다.

## 2020년 4월 3일: 4.18.2

* 인앱 메시지 - 보안상의 이유로 SDK에서 만든 WebViews는 이제 속성을 설정합니다 `setAllowFileAccess` to `false`.

## 2020년 3월 12일: 4.18.1

* Target - 이제 Target 세션 ID가 컨텍스트 데이터 매개 변수로 추가됩니다 `a.target.sessionId` ( Adobe Analytics으로 전송된 내부 Analytics-for-Target 히트에서).

## 2020년 1월 16일: 4.18.0

* 고객 확보 - Google Play Install Referrer API를 지원하기 위해 새로운 API, `Analytics.processGooglePlayInstallReferrerUrl(final String url)`을 추가했습니다.

   Install Referrer API에 대한 자세한 내용은 [InstallBroadcast를 아직 사용합니까? 2020년 3월 1일까지 Play Referrer API로 전환](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html)을 참조하십시오.

## 2019년 9월 20일: 버전 4.17.10

* 일반: Android API 레벨 21 이상에서 일부 지역의 로케일 문자열 생성이 수정되었습니다.

## 2019년 7월 18일: 버전 4.17.8

* Adobe Target: 이제 모든 요청에 클라이언트와 sessionId가 URL 쿼리 매개 변수에 포함됩니다.
* 인앱 메시징: 빈 클릭 광고 URL로 메시지가 트리거되면 Android 앱이 충돌하던 문제가 수정되었습니다.
* 방문자 ID 서비스: `Visitor.appendToURL` 및 `Visitor.getUrlVariablesAsync` API는 더 이상 반환 값을 이중 인코딩하지 않습니다.

   이중 인코딩으로 해당 API의 반환 값에 특정 보안 검토에 의한 플래그가 지정되었습니다.

## 2019년 6월 6일: 버전 4.17.7

* 일반 - 이제 Android API 레벨 20보다 낮은 네트워킹 호출에는 TLS 1.1 또는 TLS 1.2가 사용됩니다.
* Analytics - 푸시 알림이 활성화되면 라이프사이클 데이터에 푸시 옵트인 상태가 추가됩니다.

## 2019년 5월 24일: 버전 4.17.6

* 방문자 ID 서비스 - `setPushIdentifier` API가 호출될 때마다 방문자 ID 서비스에 동기화 호출을 보냅니다.
* 방문자 ID 서비스 - 연결 및 읽기 제한 시간이 2초에서 5초로 늘어났습니다.

모든 솔루션의 현재 및 과거 릴리스 노트에 대한 자세한 내용은 [Adobe Experience Cloud 릴리스 노트](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html)를 참조하십시오.
