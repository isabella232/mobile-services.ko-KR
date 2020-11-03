---
description: iOS Developer Library의 믹스 앤 매치 기능을 사용하여 iOS Adobe Mobile SDK를 Swift 프로젝트에 원활하게 통합할 수 있습니다.
seo-description: iOS Developer Library의 믹스 앤 매치 기능을 사용하여 iOS Adobe Mobile SDK를 Swift 프로젝트에 원활하게 통합할 수 있습니다.
seo-title: Swift 통합
solution: Experience Cloud,Analytics
title: Swift 통합
topic: Developer and implementation
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '129'
ht-degree: 100%

---


# Swift 통합 {#swift-integration}

iOS Developer Library의 믹스 앤 매치 기능을 사용하여 iOS Adobe Mobile SDK를 Swift 프로젝트에 원활하게 통합할 수 있습니다.

자세한 내용은 [언어 상호 운용성](https://developer.apple.com/documentation/swift#2984801.html)을 참조하십시오.

예를 들어, 설명서에 설명된 대로 브리징 헤더 메서드를 사용하여 Adobe Mobile iOS SDK 헤더 파일을 가져올 수 있습니다.

```
#import “ADBMobile.h”
```

Swift 파일의 SDK에서 메서드에 액세스하려면 다음 형식을 사용하십시오.

```
ADBMobile.{methodname}
```

