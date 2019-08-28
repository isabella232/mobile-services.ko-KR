---
description: 스크립트에서 플러그인을 호출하는 데 도움이 되는 정보입니다.
keywords: Xamarin
seo-description: 스크립트에서 플러그인을 호출하는 데 도움이 되는 정보입니다.
seo-title: 라이브러리 호출
solution: Marketing Cloud, 개발자
title: 라이브러리 호출
uuid: A 480201 A -4090-4662-8 DD 8-56 F 62144 CD 93
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Making calls to the library{#making-calls-to-the-library}

이 정보는 스크립트에서 플러그인을 호출하는 데 도움이 됩니다.

스크립트에서 플러그인을 호출하려면 네임스페이스를 가져와야 합니다.

`Com.Adobe.Mobile`사용:

* **iOS**: 네임스페이스를 가져온 후 `ADBMobile` 클래스의 정적 메서드를 통해 SDK를 직접 호출할 수 있습니다.

* **Android**: 클래스에서 정적 메서드를 통해 SDK를 직접 호출할 `Config/Analytics/Target/AudienceManager/Media`수 있습니다.

