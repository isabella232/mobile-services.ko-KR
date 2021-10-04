---
description: 히트 일괄 처리를 사용하면 오프라인 추적 기능이 활성화된 애플리케이션에서 큐의 히트 수가 구성 가능한 한도를 넘을 때까지 히트 전송을 보류할 수 있습니다.
solution: Experience Cloud,Analytics
title: 히트 배치 처리
topic-fix: Developer and implementation
uuid: 3dda7372-0695-4cb7-b779-6abca2d6e0d9
exl-id: af21f435-13cb-4353-9fbb-c99274bce411
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 100%

---

# 히트 배치 처리 {#hit-batching}

히트 일괄 처리를 사용하면 오프라인 추적 기능이 활성화된 애플리케이션에서 큐의 히트 수가 구성 가능한 한도를 넘을 때까지 히트 전송을 보류할 수 있습니다.

>[!IMPORTANT]
>
>히트 일괄 처리를 수행하려면 SDK 버전 4.1 이상이 필요합니다.

히트 일괄 처리를 사용하려면 `ADBMobileConfig.json` 파일을 업데이트하고 `batchLimit` 값을 지정하십시오.

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

0보다 큰 숫자로 설정하면 SDK는 *`batchLimit`*&#x200B;와 동일한 히트 수를 대기열로 처리합니다. 이 임계값이 초과되면 큐에 있는 모든 히트가 전송됩니다.

다음 방법은 히트 일괄 처리에 사용됩니다.

* `trackingGetQueueSize()`: 현재 히트 일괄 처리 큐에 있는 히트 수와 함께 `NSUInteger`를 반환합니다.
* `trackingSendQueuedHits()`: 현재 큐에 있는 히트 수와 상관없이 라이브러리에서 큐에 있는 모든 히트를 강제로 보냅니다.
* `trackingClearQueue()`: 큐에 있는 히트를 전송하지 않고 모두 지웁니다.

>[!CAUTION]
>
>히트 일괄 처리를 사용하려면 오프라인 추적을 사용하도록 설정해야 합니다.
