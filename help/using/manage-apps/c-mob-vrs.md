---
description: VRS(가상 보고서 세트)는 보고서 세트에 하나 이상의 세그먼트 정의를 적용하여 생성되는 보고서 세트입니다. 이를 통해 사용자는 한 보고서 세트에 데이터를 유지 관리할 수 있지만, 별도의 보고서 세트에 있는 것처럼 데이터를 관리할 수 있습니다.
seo-description: VRS(가상 보고서 세트)는 보고서 세트에 하나 이상의 세그먼트 정의를 적용하여 생성되는 보고서 세트입니다. 이를 통해 사용자는 한 보고서 세트에 데이터를 유지 관리할 수 있지만, 별도의 보고서 세트에 있는 것처럼 데이터를 관리할 수 있습니다.
seo-title: 가상 보고서 세트
title: 가상 보고서 세트
uuid: 3 F 467 CAD -43 E 7-4 CD 0-889 B -89 F 8 C 61 febbd
translation-type: tm+mt
source-git-commit: 814c99695f538160ae28484ca8e2a92f5b24bb1a

---


# Virtual report suites {#virtual-report-suites}

VRS(가상 보고서 세트)는 보고서 세트에 하나 이상의 세그먼트 정의를 적용하여 생성되는 보고서 세트입니다. 이렇게 하면 사용자가 한 보고서 세트에 데이터를 유지 관리할 수 있지만 데이터를 별도의 보고서 세트에서와 같이 관리할 수 있습니다.

Vrss를 사용하는 앱은 다음과 같은 기능을 제외하면 일반 보고서 세트를 사용하는 앱과 동일한 역할을 합니다.

* 처리 규칙
* evars/props/listvars/events
* 타임스탬프 지원 옵션
* 차원 플래그(라이프사이클, 위치 등)
* 분류

이러한 값은 상위 보고서 세트에서 관리되며 동일한 상위 보고서 세트에 속하는 VRS와 공유됩니다.

다음 영역은 상위 보고서 세트와 관계없이 Adobe Mobile Services UI에서 액세스할 수 있습니다.

* 구성 파일
* 관심 영역 관리
* 링크 대상 관리
* 포스트백 관리
* 메시지 링크
* 획득

VRS를 사용하면 다음 작업을 완료할 수 있습니다.

* 데이터 액세스 제한

   다국적 회사에는 모든 지리적 위치에 대한 보고서 세트로 데이터를 보내는 앱이 있습니다. 그러나 회사는 한 지역의 비즈니스 사용자가 다른 지역의 데이터를 볼 수 없도록 제한하려고 합니다. 회사의 관리자는 지역별로 사용자를 세분화하고 해당 지역을 관리하는 비즈니스 사용자만 VRS에 대한 권한을 부여할 수 있는 VRS를 만들 수 있습니다.

   이러한 제한 사항으로 인해 비즈니스 사용자는 해당 지역과 관련이 없는 데이터를 볼 수 없습니다. 예를 들어 EMEA의 비즈니스 사용자는 APAC 지역에 대한 데이터를 볼 필요가 없습니다.

* 한 보고서 세트로 전송되는 모든 데이터가 포함된 인앱/푸시 메시지, 위치 POI, 확보 및 포스트백을 제어할 수 있습니다.

   다국적 회사는 모든 데이터를 모든 지리적 위치에 대한 동일한 보고서 세트로 전송하려고 합니다. 하지만 이 회사는 각 지역의 마케팅 팀이 해당 인앱/푸시 메시지를 처리하게 하려고 합니다. 회사의 관리자는 지역 VRS를 만들 수 있고, 각 팀은 해당 VRS를 기반으로 자체 앱을 관리할 수 있습니다.

   지역 팀은 VRS의 구성 파일을 사용하여 앱을 빌드합니다. 데이터는 상위 보고서 세트로 전송되지만 앱 내/푸시 메시지, 위치 POI, 획득 및 포스트백이 VRS로 만들어진 앱에서 제어됩니다.

## Create a virtual report suite in Adobe Analytics {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>Adobe Analytics 관리자만 Adobe Analytics에서 가상 보고서 세트를 만들고 수정할 수 있습니다. To create a virtual report suite, see [Create virtual report suites](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html).

각 VRS에는 고유한 ID가 있습니다. Adobe Mobile Services UI에서 상위 보고서 세트 ID를 보려면 앱 설정 관리 페이지의 **[!UICONTROL 앱 정보]** 섹션에서 **[!UICONTROL 자세한 정보를 클릭합니다]**.

Adobe Mobile Services UI에서 VRS를 사용하여 조직의 특정 그룹에 대한 앱 및 세그먼트 데이터를 만들 수 있습니다. 이런 방식으로 예를 들면, 스페인의 비즈니스 사용자는 일본의 비즈니스 사용자와 관련된 데이터를 볼 수 없습니다.

>[!TIP]
>
>상위 보고서 세트에서 상속된 값은 수정할 수 없습니다.

VRS는 상위 보고서 세트에 연결된 서버 측 세그먼트 정의입니다. 따라서 VRS에 데이터 컬렉션을 수행할 수 없습니다. SDK가 상위 보고서 세트에만 히트를 보내므로 결국 히트를 기록하기 때문입니다.

## Virtual report suite in Adobe Mobile Services and data collection {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

Adobe Mobile Services 에서는 상위 보고서 세트 또는 가상 보고서 세트를 기반으로 앱을 만들 수 있습니다. 가상 보고서 세트를 기반으로 앱을 만들 때 앱의 정의에 맞게 VRS 세그먼트를 정렬하는 것이 좋습니다.

>[!TIP]
>
>푸시 인증은 Mobile Services UI의 앱 수준에서 첨부됩니다.

푸시 메시지가 올바르게 전송되도록 하려면 대상 세그먼트를 올바르게 정의해야 합니다. 자세한 내용은 [대상: 푸시 메시지에 대한 대상 세그먼트 정의 및 구성](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

## Understanding time zones {#section_498E1EED22D741C3BDED44F01FACA72A}

[앱 설정 관리] 페이지의 시간대 속성은 Adobe Analytics에서 VRS를 만드는 데 사용하는 표준 시간대 속성과 다릅니다. [앱 설정 관리] 페이지의 속성은 Adobe Analytics로 데이터를 전송하는 데 사용되는 상위 보고서 세트에서 상속됩니다. Adobe Analytics에서 VRS를 만들 때 지정하는 속성은 Mobile Services UI에서 보고서를 표시하는 데 사용되며 상위 보고서 세트와 다를 수 있습니다.

## Select a virtual report suite in the Mobile Services UI {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

앱을 만들 때 VRS를 사용하려면 **앱 정보 페이지의보고서 세트** 드롭다운 목록에서 VRS를 선택합니다. 이 목록에는 상위 및 가상 보고서 세트가 포함되어 있습니다.

>[!IMPORTANT]
>
>To select a VRS from the list, locate an option with the blue dot and the `vrs_` *`<company_name>`* `_` *`<unique name>`* naming convention.

## Virtual Report Suite properties {#section_20ECE6243F664C4FB4347ADB4FF0458A}

다음은 VRS의 속성입니다.

>[!TIP]
>
>읽기 전용 속성은 상위 보고서 세트에서 상속됩니다.

| 속성 | 상위 보고 세트에서 상속됨 | 편집 가능 여부 | 참고 |
|--- |--- |--- |--- |
| `target.clientCode` | 아니요 | 예 |  |
| `target.timeout` | 아니요 | 예 |  |
| `audienceManager.server` | 아니요 | 예 |  |
| `audienceManager.analyticsForwardingEnabled` | 예 | 예 |  |
| `audienceManager.timeout` | 아니요 | 예 |  |
| `acquisition.server` | 아니요 | 아니요 |  |
| `acquisition.appid` | 아니요 | 아니요 |  |
| `analytics.rsids` | 예 | 아니요 |  |
| `analytics.server` | 아니요 | 아니요 |  |
| `analytics.ssl` | 아니요 | 예 |  |
| `analytics.offlineEnabled` | 예 |  |  |
| `analytics.charset` | 예 | 아니요 |  |
| `analytics.lifecycleTimeout` | 아니요 | 예 | 사용자가 해당 데이터 불일치를 원치 않을 경우 상위 보고 세트여야 합니다. |
| `analytics.privacyDefault` | 아니요 | 예 |  |
| `analytics.batchLimit` | 아니요 | 예 |  |
| `analytics.timezone` | 예 | 예, 앱을 처음 생성하는 경우입니다. | 이 시간대 속성은 Adobe Analytics에 데이터를 전송하는 데 사용되며, VRS가 작성될 때 설정된 시간대 속성과는 다릅니다. |
| `analytics.timezoneOffset` | 예 | 아니요 |  |
| `analytics.referrerTimeout` | 아니요 | 예 |  |
| `analytics.backdateSessionInfo` | 예 | 예 |  |

## 추가 정보 {#section_4C4446F1FBE64F659BC0A2362C9F3E59}

가상 보고서 세트에 대한 몇 가지 추가 정보는 다음과 같습니다.

* VRS에 대한 자세한 내용은 [가상 보고서 세트](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-about.html)를 참조하십시오.
* For more information about planning a VRS implementation, see [Virtual report suite workflow](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html).