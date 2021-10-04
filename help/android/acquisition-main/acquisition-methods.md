---
description: '다음은 Android 라이브러리에서 제공하는 획득 메서드입니다. '
keywords: android;라이브러리;모바일;sdk
solution: Experience Cloud,Analytics
title: 획득 메서드
topic-fix: Developer and implementation
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
exl-id: 0ce1b8fb-fd45-45de-8f97-e297e4c6529f
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 100%

---

# 획득 메서드{#acquisition-methods}

다음은 Android 라이브러리에서 제공하는 획득 메서드입니다.

* **campaignStartForApp**

   사용자가 링크를 클릭한 것처럼 개발자가 앱 획득 캠페인을 시작할 수 있도록 해줍니다. 이것은 수동 획득 링크를 만들고 앱스토어 리디렉션을 직접 처리하는 데 도움이 됩니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void campaignStartForApp(final String appId final Map<String Object> data); 
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Acquisition.campaignStartForApp("0652024f-adcd-49f9-9bd7-2552a4564d2f" new 
      HashMap<String Object (){{
           put("custom.key" "value");
      }}); 
      ```
