---
description: 다음은 충돌을 추적하는 방법을 이해하고 허위 충돌을 처리하는 우수 사례를 확인하는 데 유용한 정보입니다.
seo-description: 다음은 충돌을 추적하는 방법을 이해하고 허위 충돌을 처리하는 우수 사례를 확인하는 데 유용한 정보입니다.
seo-title: Track App crashes
solution: Marketing Cloud,Analytics
title: 앱 충돌 추적
topic: 개발자 및 구현
uuid: 4f81988b-198a-4ba9-ad53-78af90e43856
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# 앱 충돌 추적 {#track-app-crashes}

다음은 충돌을 추적하는 방법을 이해하고 허위 충돌을 처리하는 우수 사례를 확인하는 데 유용한 정보입니다.

>[!IMPORTANT]
>
>잘못된 충돌이 보고되지 않도록 중요한 변경 사항이 포함된 iOS SDK 버전 4.8.6으로 업그레이드해야 합니다.

## Adobe는 언제 충돌을 보고합니까?

애플리케이션이 백그라운드로 전환되지 않은 채로 종료되면 SDK는 다음에 앱이 시작될 때 충돌을 보고합니다.

## 충돌 보고는 어떻게 작동합니까?

iOS에서는 개발자가 애플리케이션 라이프사이클에서 다양한 상태와 이벤트를 추적하고 이에 응답할 수 있도록 하는 시스템 알림을 사용합니다.

AdobeMobile iOS SDK에는 `UIApplicationDidEnterBackgroundNotification` 알림에 응답하는 알림 핸들러가 있습니다. 이 코드에서는 사용자가 앱을 백그라운드로 전환했음을 나타내는 값이 설정됩니다. 후속 시작 시 해당 값을 찾을 수 없으면 충돌이 보고됩니다.

## Adobe에서 이 방법으로 충돌을 측정하는 이유는 무엇입니까?

이 충돌 측정 방식은 *사용자가 의도적으로 내 앱을 종료했습니까?*&#x200B;라는 질문에 대한 개략적인 답을 제공합니다.

Apteligent(이전의 Crittercism)와 같은 회사에서 제공하는 충돌 보고 라이브러리는 더 자세한 충돌 보고를 제공하기 위해 전역 `NSException` 핸들러를 사용합니다. 앱에 이러한 유형의 핸들러가 두 개 이상 있을 수는 없습니다. Adobe는 고객이 다른 오류 보고 공급자를 이용 중일 수 있음을 고려하여 빌드 오류 방지를 위해 전역 `NSException` 핸들러를 구현하지 않기로 결정했습니다.

## 허위 충돌이 보고될 수 있는 원인은 무엇입니까?

SDK에서 허위로 충돌을 보고하는 원인이 되는 것으로 알려진 시나리오는 다음과 같습니다.

* Xcode를 사용하여 디버깅 중인 경우 포그라운드에 있을 때 앱을 다시 시작하면 충돌이 발생합니다.

   >[!TIP]
   >
   >Xcode에서 앱을 다시 시작하기 전에 앱을 백그라운드로 전환하여 이 시나리오의 충돌을 방지할 수 있습니다.

* If your app is in the background and sends Analytics hits through a call other than `trackActionFromBackground`, `trackLocation`, or `trackBeacon`, and the app is terminated (manually or by the OS) while in the background, and the next launch will be a crash.

   >[!TIP]
   >
   >Background activity that occurs beyond the `lifecycleTimeout` threshold might also result in an additional false launch.

* 앱이 백그라운드 가져오기, 위치 업데이트 등의 이유로 백그라운드에서 시작된 후 포그라운드로 전환되지 않은 채 OS에 의해 종료되는 경우 다음에 백그라운드나 포그라운드에서 앱이 시작될 때 충돌이 발생합니다.
* 앱이 백그라운드에 있는 동안 `NSUserDefaults`에서 Adobe의 일시 중지 플래그를 프로그래밍 방식으로 삭제하면 다음에 시작하거나 다시 시작할 때 충돌이 발생합니다.

## 허위 충돌이 보고되지 않게 하려면 어떻게 해야 합니까?

다음 방법을 통해 허위 충돌이 보고되지 않도록 할 수 있습니다.

* iOS SDK 4.8.6에서는 새로운 라이프사이클 세션이 실제로 필요한지 여부를 더 잘 판단할 수 있도록 코드가 추가되었습니다.

   이 코드는 이전 섹션에 설명한 허위 충돌 #2 및 #3을 수정합니다.

* 허위 충돌 #1이 발생하지 않도록, 비프로덕션 보고서 세트에 대해 개발을 수행해야 합니다.
* AdobeMobile SDK가 `NSUserDefaults`에 입력하는 값을 삭제하거나 수정하지 마십시오.

   If these values are modified outside the SDK, the reported data will be invalid.

