---
description: iOS Developer Library의 믹스 앤 매치 기능을 사용하여 iOS Adobe Mobile SDK를 Swift 프로젝트에 원활하게 통합할 수 있습니다.
seo-description: iOS Developer Library의 믹스 앤 매치 기능을 사용하여 iOS Adobe Mobile SDK를 Swift 프로젝트에 원활하게 통합할 수 있습니다.
seo-title: Swift 통합
solution: Marketing Cloud,Analytics
title: Swift 통합
topic: 개발자 및 구현
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Swift integration {#swift-integration}

iOS Developer Library의 믹스 앤 매치 기능을 사용하여 iOS Adobe Mobile SDK를 Swift 프로젝트에 원활하게 통합할 수 있습니다.

For more information, see Language Interoperability.[](https://developer.apple.com/documentation/swift#2984801.html)

예를 들어 위 문서에서 설명하는 대로 브릿징 헤더 메서드를 사용하면 Adobe Mobile iOS SDK 헤더 파일을 가져올 수 있습니다.

```
#import “ADBMobile.h”
```

Swift 파일에서 SDK의 메서드에 액세스하려면 다음 형식을 사용하십시오.

```
ADBMobile.{methodname}
```

