---
description: 스크립트에서 플러그인을 호출하는 데 도움이 되는 정보입니다.
keywords: Xamarin
solution: Experience Cloud Services
title: 라이브러리에 대한 호출
uuid: a480201a-4090-4662-8dd8-56f62144cd93
exl-id: a5ec1e1b-e29a-42c9-bcc9-bee05c427044
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 10%

---

# 라이브러리에 대한 호출{#making-calls-to-the-library}

스크립트에서 플러그인을 호출하는 데 도움이 되는 정보입니다.

스크립트에서 플러그인을 호출하려면 네임스페이스를 가져와야 합니다.

사용 `Com.Adobe.Mobile`:

* **iOS**: 네임스페이스를 가져온 후에는 의 정적 메서드를 통해 SDK를 직접 호출할 수 있습니다 `ADBMobile` 클래스를 참조하십시오.

* **Android**: 에서 정적 메서드를 통해 SDK에 직접 호출할 수 있습니다 `Config/Analytics/Target/AudienceManager/Media`클래스를 참조하십시오.
