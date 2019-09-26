---
description: 히트 일괄 처리를 사용하면 오프라인 추적 기능이 활성화된 애플리케이션에서 큐의 히트 수가 구성 가능한 한도를 넘을 때까지 히트 전송을 보류할 수 있습니다.
seo-description: 히트 일괄 처리를 사용하면 오프라인 추적 기능이 활성화된 애플리케이션에서 큐의 히트 수가 구성 가능한 한도를 넘을 때까지 히트 전송을 보류할 수 있습니다.
seo-title: 히트 배치 처리
solution: Marketing Cloud,Analytics
title: 히트 배치 처리
topic: 개발자 및 구현
uuid: 3dda7372-0695-4cb7-b779-6abca2d6e0d9
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# 히트 배치 처리 {#hit-batching}

히트 일괄 처리를 사용하면 오프라인 추적 기능이 활성화된 애플리케이션에서 큐의 히트 수가 구성 가능한 한도를 넘을 때까지 히트 전송을 보류할 수 있습니다.

>[!IMPORTANT]
>
>히트 일괄 처리에는 SDK 버전 4.1 이상이 필요합니다.

To enable hit batching, update your `ADBMobileConfig.json` file and specify a value for `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

0보다 큰 숫자로 설정하면 SDK는 *`batchLimit`*. 이 임계값을 넘기면 큐에 있는 모든 히트가 전송됩니다.

다음 메서드가 히트 일괄 처리에 사용됩니다.

* `trackingGetQueueSize()` 현재 히트 일괄 처리 큐에 있는 히트 수와 함께 `NSUInteger` 를 반환합니다.
* `trackingSendQueuedHits()` 현재 큐에 있는 히트 수에 관계없이 라이브러리에서 큐에 있는 모든 히트를 강제로 보냅니다.
* `trackingClearQueue()`: 큐에 있는 히트를 전송하지 않고 모두 지웁니다.

>[!CAUTION]
>
>히트 일괄 처리를 사용하려면 오프라인 추적을 활성화해야 합니다.

