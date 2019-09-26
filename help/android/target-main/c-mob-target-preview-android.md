---
description: 타겟 미리 보기를 사용하면 타겟 활동에 대해 엔드투 엔드 QA를 쉽게 수행하고 해당 활동을 장치에서 미리 볼 수 있습니다.
seo-description: 타겟 미리 보기를 사용하면 타겟 활동에 대해 엔드투 엔드 QA를 쉽게 수행하고 해당 활동을 장치에서 미리 볼 수 있습니다.
seo-title: Android에서 타겟 미리 보기
title: Android에서 타겟 미리 보기
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94

---


# Android에서 타겟 미리 보기 {#target-preview-on-android}

타겟 미리 보기를 사용하면 타겟 활동에 대해 엔드투 엔드 QA를 쉽게 수행하고 해당 활동을 장치에서 미리 볼 수 있습니다.

타겟 미리 보기 설정 및 사용 방법은 [타겟 모바일 미리 보기](https://docs.adobe.com/content/help/en/target/using/implement-target/mobile-apps/target-mobile-preview.html)로 이동하십시오.

>[!IMPORTANT]
>
>To use Target Preview, you need SDK version 4.14.0 or later.

* **setPreviewRestartDeeplink**

   미리 보기 모드에서 미리 보기 선택이 적용될 때 트리거할 앱 딥링크를 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void setPreviewRestartDeeplink(String deeplink);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Target.setPreviewRestartDeeplink(“myapp://myhost”); 
      ```

