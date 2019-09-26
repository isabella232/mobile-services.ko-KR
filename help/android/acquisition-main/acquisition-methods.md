---
description: '다음 획득 메서드는 Android 라이브러리에서 제공합니다 '
keywords: android;library;mobile;sdk
seo-description: '다음 획득 메서드는 Android 라이브러리에서 제공합니다 '
seo-title: 획득 메서드
solution: Marketing Cloud,Analytics
title: 획득 메서드
topic: 개발자 및 구현
uuid: 22ec432f-e7ae-4e8 파섹
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Acquisition methods{#acquisition-methods}

다음 획득 메서드는 Android 라이브러리에서 제공합니다.

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
