---
description: Experience Cloud 솔루션용 iOS SDK 4.x에 대한 릴리스 노트 및 알려진 문제
solution: Experience Cloud Services,Analytics
title: 릴리스 노트
topic-fix: Developer and implementation
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
exl-id: dd1e6bab-65e7-4a68-b3ec-21fb1a08aca2
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 99%

---

# 릴리스 정보 {#release-notes}

다음은 Experience Cloud 솔루션용 iOS SDKs 4.x에 대한 릴리스 노트, 알려진 문제 및 핫픽스 정보입니다.

## 2021년 4월 13일: 버전 4.21.2

* Visitor ID 서비스 - 비어 있는 광고 식별자가 Visitor ID 서비스에 동기화되는 관련 문제가 수정되었습니다.

## 2021년 1월 13일: 버전 4.21.1

* 일반 - 앱을 종료하는 동안 SQLite 예외가 발생할 수 있는 문제를 수정했습니다.

## 2020년 12월 15일: 버전 4.21.0

* 일반 - SDK는 기존 Intel 아키텍처에 대한 지원을 유지하면서 새로운 Apple M1 아키텍처로 하드웨어를 지원하기 위해 XCFrameworks를 사용하여 배포됩니다.
   * 중요: AdobeMobile XCFramworks로 업그레이드하려면 Xcode 12.0 이상이 필요합니다.
   * 중요: Cocoapods를 사용하는 경우 AdobeMobile XCFramworks로 업그레이드하려면 Cocoapods 1.10.0 이상이 필요합니다.

## 2020년 11월 4일: 버전 4.20.0

* 방문자 ID 서비스 - 광고 추적이 활성화/비활성화된 후 setAdvertisingIdentifier가 호출될 때 device_consent 상태 매개 변수가 추가되었습니다.
* Analytics - iAd.framework가 연결되어 있고 장치에서 &quot;광고 추적 제한&quot;이 활성화되어 있을 때 설치하면 Analytics 히트의 전송이 지연되는 버그가 수정되었습니다.

## 2020년 7월 16일: 버전 4.19.3

* 일반 - 쿼리 매개 변수에서 같음 기호가 있는 URL이 올바르게 처리되지 않는 버그를 수정했습니다.

## 2020년 3월 24일: 버전 4.19.2

* 일반 - 타겟 코드에서 일부 누수가 수정되었습니다.

## 2020년 3월 12일: 버전 4.19.1

* 일반 - Swift 열거형이 추적 호출을 위한 컨텍스트 데이터에 포함될 때 발생할 수 있는 충돌을 해결했습니다.
* 이제 세션 ID가 Adobe Analytics로 전송된 내부 타겟 분석 히트에서 컨텍스트 데이터 매개 변수 ‘a.target.sessionId’로 추가됩니다.

## 2020년 2월 4일: 버전 4.19.0

* 라이프사이클 - 일부 이전 iOS 장치에서 보고된 비정상적인 세션 길이 데이터를 완화하도록 새 API인 pauseCollectingLifecycleData를 추가했습니다.

## 2019년 11월 8일: 버전 4.18.9

* 앱 메시지 - 캐시된 이미지나 번들 이미지를 전체 화면 메시지에서 로드할 수 없는 버그를 수정했습니다.

## 2019년 9월 20일: 버전 4.18.8

* 앱 메시징:

   * iOS 10 이상을 실행하는 장치에서 이제 `UserNotifications` 프레임워크를 사용하여 `UserNotifications.framework`에 연결해야 하는 로컬 알림을 예약합니다.
   * 이제 전체 화면 메시지는 `WebKit.framework`의 WKWebViews를 사용합니다. WKWebViews를 사용하려면 Xcode 프로젝트에 연결되어 있어야 합니다.
   * 푸시 클릭스루 페이로드를 인앱 메시지의 트레이트로 사용할 수 없는 버그가 수정되었습니다.
   * 충돌 문제가 해결되었습니다.

* 일반 - SDK 데이터가 모든 Analytics 호출 시 쌍으로 연결된 watchOS 앱과 동기화되는 버그가 수정되었습니다.

## 2019년 8월 2일: 버전 4.18.7

* 일부 환경에서 11.0 이전 버전의 iOS를 실행하는 장치에서 충돌을 일으킨 버전 4.18.6에 도입된 변경 사항을 되돌렸습니다.

* Adobe Target: Target 요청으로 impressionId를 전송할 수 있는 `requestLocationParameters` 속성이 `ADBTargetRequestObject`에 추가되었습니다.

## 2019년 7월 18일: 버전 4.18.6

* Adobe Target: 이제 모든 요청에 클라이언트와 `sessionId` 매개 변수가 URL 쿼리 매개 변수에 포함됩니다.
* Adobe Target: 메모리 누수가 수정되었습니다.
* 방문자 ID 서비스: `visitorAppendToURL` 및 `visitorGetUrlVariablesAsync` API는 더 이상 반환 값을 이중 인코딩하지 않습니다.

   이중 인코딩으로 해당 API의 반환 값에 특정 보안 검토에 의한 플래그가 지정되었습니다.

## 2019년 6월 5일: 버전 4.18.5

* Analytics - 푸시 알림이 활성화되면 푸시 옵트인 상태가 라이프사이클 데이터에 추가됩니다.

## 2019년 5월 24일: 버전 4.18.4

* 방문자 ID 서비스 - 
   `visitorGetUrlVariablesAsync` API에 대한 반환 제한 시간이 30초로 늘어났습니다.

* 방문자 ID 서비스 - 이제 `setPushIdentifier` API가 호출될 때마다 방문자 ID 서비스에 동기화 호출을 보냅니다.

모든 솔루션의 현재 및 과거 릴리스 노트에 대한 자세한 내용은 [Adobe Experience Cloud 릴리스 노트](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=ko-KR)를 참조하십시오.
