---
description: 스크립트에서 플러그인을 호출하는 데 도움이 되는 정보입니다.
keywords: Xamarin
seo-description: 스크립트에서 플러그인을 호출하는 데 도움이 되는 정보입니다.
seo-title: 라이브러리에 대한 호출
solution: Experience Cloud
title: 라이브러리에 대한 호출
uuid: a480201a-4090-4662-8dd8-56f62144cd93
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---


# 라이브러리에 대한 호출{#making-calls-to-the-library}

스크립트에서 플러그인을 호출하는 데 도움이 되는 정보입니다.

스크립트에서 플러그인을 호출하려면 네임스페이스를 가져와야 합니다.

사용 방법 `Com.Adobe.Mobile`:

* **iOS**:네임스페이스를 가져온 후 클래스의 정적 메서드를 통해 SDK를 직접 호출할 수 `ADBMobile` 있습니다.

* **Android**:클래스의 정적 메서드를 통해 SDK를 직접 호출할 수 `Config/Analytics/Target/AudienceManager/Media`있습니다.

