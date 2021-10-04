---
description: 히트 배치(일괄 처리)를 사용하면 애플리케이션에서 큐의 히트 수가 구성된 한도를 초과할 때까지 히트 전송을 보류할 수 있습니다.
keywords: android;라이브러리;모바일;sdk
solution: Experience Cloud,Analytics
title: 히트 일괄 처리
topic-fix: Developer and implementation
uuid: ada35be3-242b-4b2b-a828-9bf998dd58b5
exl-id: 74147f09-52fc-46dc-b4dd-2bf60b039f6e
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 100%

---

# 히트 배치 처리 {#hit-batching}

히트 배치(일괄 처리)를 사용하면 애플리케이션에서 큐의 히트 수가 구성된 한도를 초과할 때까지 히트 전송을 보류할 수 있습니다.

>[!IMPORTANT]
>
>히트 일괄 처리를 사용하려면 오프라인 추적을 활성화하고 SDK 버전 4.1 이상이 **있어야** 합니다.

히트 일괄 처리를 사용하려면 `ADBMobileConfig.json` 파일을 업데이트하고 `batchLimit` 값을 지정하십시오.

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

이 값을 0보다 큰 수로 설정하면 SDK는 *`batchLimit`* 값과 동일한 히트 수를 큐에 추가합니다. 이 임계값이 초과되면 큐에 있는 모든 히트가 전송됩니다.

다음 방법은 히트 일괄 처리에 사용됩니다.

* `Analytics.getQueueSize`: 현재 히트 일괄 처리 큐에 있는 히트 수와 함께 `long`을 반환합니다.

* `Analytics.sendQueuedHits`: 현재 큐에 있는 히트 수와 상관없이 라이브러리에서 큐에 있는 모든 히트를 강제로 보냅니다.
* `Analytics.clearQueue`: 큐에 있는 히트를 전송하지 않고 모두 지웁니다.
