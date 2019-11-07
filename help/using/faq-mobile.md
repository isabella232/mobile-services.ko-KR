---
description: Adobe Mobile Services에 대한 FAQ 및 답변과 기능에 대한 일반 설명.
keywords: mobile
seo-description: Adobe Mobile Services에 대한 FAQ 및 답변과 기능에 대한 일반 설명.
seo-title: FAQ
solution: Marketing Cloud,Analytics
title: FAQ
topic: 지표
uuid: 62a9241c-2ada-483a-a594-b023916cb0b6
translation-type: ht
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# FAQ {#frequently-asked-questions}

다음 표에는 Adobe Mobile Services에 대한 FAQ 목록이 포함되어 있습니다.

## Adobe 모바일 SDK {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### SDK를 자주 업데이트하시나요?

예, 기능이 가장 많고, 표준을 준수하며 보안되는 SDK를 제공하기 위해 지속적으로 업데이트하고 있습니다. 일반적으로 매달 새 버전을 출시합니다. 이러한 SDK 업데이트는 구현하기 쉽도록 드롭인 대체로 제공됩니다(버전 4x의 경우). 업데이트에 대한 자세한 내용은 [릴리스 노트](https://docs.adobe.com/content/help/ko-KR/release-notes/experience-cloud/current.html)를 참조하십시오.

### 사용해야 하는 SDK 버전은 무엇인가요?

당사의 최신 SDK는 버전 4.11을 기반으로 합니다. 자세한 내용은 [릴리스 노트](https://docs.adobe.com/content/help/ko-KR/release-notes/experience-cloud/current.html)를 참조하십시오.

### 어디에서 SDK를 다운로드할 수 있나요?

개별 모바일 플랫폼용 SDK는 [앱 설정 관리](/help/using/c-manage-app-settings/c-manage-app-settings.md) 섹션에서 다운로드할 수 있습니다.

### SDK를 어떻게 구성해야 하나요?

새 앱 보고서 세트를 만든 후에 앱 설정 관리로 이동하여 앱 정보 페이지에서 모든 필수 옵션을 구성합니다. 구성을 저장한 후 앱 설정 관리 페이지 하단에서 필요한 SDK를 다운로드합니다. SDK는 저장한 옵션을 사용하여 사전 구성된 상태로 제공되며 SDK 패키지의 `ADBMobileConfig.json` 파일에서 찾을 수 있습니다. 앱 설정 관리 페이지에서 SDK 설정을 변경하는 경우 SDK 파일을 다시 다운로드하거나 필요한 변경이 포함되도록 `ADBMobileConfig.json` 파일을 업데이트해야 합니다.

### Adobe 모바일 SDK에서 IPv6 for iOS를 지원하나요?

Adobe 모바일 SDK는 iOS 및 Android 표준 네트워크 스택을 사용합니다. SDK는 iOS의 경우 NSURLSession(iOS 버전 7 이상) 및 NSURLConnection(iOS 버전 7 이상)을 사용합니다. 이러한 두 클래스는 IPv6을 완전히 준수합니다. 직접 네트워킹 스택을 구축했거나 그러한 스택을 사용하는 개발자의 경우 이를 완화하기 위한 다른 고려 사항이 있는지 검토해볼 수 있습니다. 다음은 Apple에서 제공한 추가 정보입니다.

*하이레벨 네트워킹 API(예: NSURLSession 및 CFNetwork 프레임워크)를 사용하여 클라이언트 측 앱을 작성하고 이름별로 연결하는 경우 IPv6 주소에서 앱이 작동하려면 아무것도 변경하면 안 됩니다.* 자세한 내용은 [IPv6 DNS64/NAT64 네트워크 지원](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1)을 참조하십시오.


## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### 라이프사이클 지표란 무엇인가요?

라이프사이클 지표란 SDK가 앱으로 처음 구현될 때 자동으로 수집되는 "기본(out-of-the-box)" 지표입니다. 자세한 내용은 [라이프사이클 지표(Android)](/help/android/metrics.md) 및 [라이프사이클 지표(iOS)](/help/ios/metrics.md)를 참조하십시오.

### 처리 규칙 문제는 어떻게 해결해야 하나요?

자세한 내용은 [처리 규칙 팁과 트릭](https://docs.adobe.com/content/help/ko-KR/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html)을 참조하십시오.

### 분석 데이터를 여러 보고서 세트로 전송할 수 있나요?

예. SDK에서 복수의 Adobe Analytics 보고서 세트로 데이터를 전송할 수 있는 기능을 제공합니다. 이미지 요청을 사용하여 여러 보고서 세트의 데이터를 캡처하려면 파일에서 **[!UICONTROL 분석]** 섹션의 **rsids[!UICONTROL 필드에 있는 여러 보고서 세트 ID를 쉼표로(공백 없음) 구분하여 설정합니다.]**`ADBMobileConfig.json` 자세한 내용은 [ADBMobile JSON 구성](/help/ios/configuration/json-config/json-config.md)을 참조하십시오.

### 모바일 방문은 실행과 어떻게 다른가요?

사용자가 앱을 처음 열거나 지정된 시간 제한 값보다 오래 앱을 사용하지 않았다가 앱으로 돌아오면 SDK에서 실행으로 측정합니다. 일반 시간 제한은 `ADBMobileConfig.json` 파일의 **[!UICONTROL lifecycleTimeout]** 필드에 설정된 5분(300초)입니다. 방문은 Adobe Analytic의 서버측 계산으로, 방문 시간 제한을 초과하지 않고 SDK에서 전송한 맨 처음 및 마지막 데이터 히트를 기준으로 합니다. 일반적으로 세션 시간 초과는 보고서 세트에 대해 30분으로 설정되어 있습니다. 방문 횟수는 기존의 웹 분석에서 가져오지만, 이러한 히트는 사용자가 앱을 입력하고 종료하는 방법에 대한 유용한 통찰력을 제공합니다.

## 메시징 {#section_5EFDD2B2EBA543C09902FF979C89F2EC}

### 푸시 알림에 대한 크기 또는 다른 제한이 있나요?

푸시 알림 메시지는 140자 제한이 있습니다. 그렇지만 발송 또는 예약 가능한 알림의 수나 알림 발송 횟수에는 제한이 없습니다.

### 푸시 알림에 대한 사용자 지정 페이로드를 지원하나요?

예, JSON 형식으로 코딩 가능한 사용자 지정 푸시 페이로드를 허용합니다. Android 및 iOS 페이로드는 각각 4KB 및 2KB로 제한됩니다. 이러한 페이로드는 푸시 또는 로컬 알림을 통해 앱으로 전송됩니다. 자세한 내용은 [환경: 푸시 메시지](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md)를 참조하십시오.

### 인앱 메시지에 크기 제한이 있나요?

Adobe Mobile Services에서 만들어 게시된 활성 인앱 메시지는 앱 보고서 세트당 15MB 크기 제한이 있는 서버에서 호스팅됩니다. 이 제한이 Adobe에서 호스팅되는 메시지 내용 및 리소스에 적용되는 한편 인앱 메시지가 다른 호스트 또는 앱 내의 리소스에서 참조할 수 있는 리소스에는 제한이 없습니다.

### 인앱 메시지에 직접 작성한 HTML을 사용할 수 있나요?

예, 인앱 메시지에 사용자 지정 HTML을 지원합니다. 자세한 내용은 [환경: 인앱 메시지](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md)를 참조하십시오.

### 푸시 알림 또는 인앱 메시지를 발송하기 위해 어떤 트리거를 사용할 수 있나요?

마케터는 인앱 메시지를 표시하는 트리거로 전송될 Analytics 데이터 또는 이벤트를 선택할 수 있습니다. 인앱 메시지는 장치에서 로컬로 발생하는 트리거를 사용합니다. 트리거를 여러 개 선택한 경우 메시지가 표시되려면 모든 트리거가 같은 히트에서 발생해야 합니다. 자세한 내용은 [환경: 인앱 메시지](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md)를 참조하십시오.

푸시 메시지는 이미 수집된 Analytics 내역 데이터에 만들어져 있을 수 있는 이미 존재하는 Adobe Analytics 세그먼트 또는 사용자 지정 세그먼트를 사용하여 발송됩니다. 자세한 내용은 [환경: 푸시 메시지](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md)를 참조하십시오.

### 입력한 인앱, 푸시 또는 마케팅 링크 이름에 오류가 발생하는 이유는 무엇입니까?

동일한 부모 보고서 세트 또는 VRS를 사용하는 여러 앱에서 동일한 인앱 메시지, 푸시 메시지 또는 마케팅 링크 이름을 사용할 수 없습니다. 이 문제를 해결하려면 인앱 메시지, 푸시 메시지 또는 마케팅 링크에 다른 이름을 입력합니다.

## 위치 {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### 설정 가능한 POI(관심 영역)의 수에 제한이 있나요?

특정 제한 사항은 없지만, 이상적인 성능을 위해 그리고 사용자 장치의 메모리 제한으로 인해 최대 5000개의 POI를 만들거나 업로드하는 것이 좋습니다.

## 획득 {#section_B37F1129CD5843E890D0E54179455357}

### 캠페인을 인앱 활동과 연관지어 생각할 수 있나요?

예. Adobe Mobile Services는 앱을 홍보하고 앱으로의 트래픽을 유도하는 데 도움이 되는 마케팅 링크를 작성하게 하고 획득 캠페인을 인앱 활동 및 대화와 연결하게 해줍니다. 자세한 내용은 [획득](/help/using/acquisition-main/acquisition-main.md)을 참조하십시오.

### 새 앱 사용자를 확보하고 추적하는 링크를 설정하려면 어떻게 하나요?

사용자가 Apple App Store 및 Google Play에서 애플리케이션을 다운로드하도록 안내하는 마케팅 링크를 만들 수 있습니다. 이러한 링크를 통해 성공 이벤트를 다운로드에 기여할 수 있습니다. 자세한 정보는 [마케팅 링크 빌더](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)를 참조하십시오.