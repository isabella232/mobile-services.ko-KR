---
description: 타겟 미리 보기를 사용하면 타겟 활동에 대해 엔드투 엔드 QA를 쉽게 수행하고 해당 활동을 장치에서 미리 볼 수 있습니다.
title: Android에서 타겟 미리 보기
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
exl-id: 69103f3a-9521-4808-8ecd-7b960efca04d
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 74%

---

# Android에서 타겟 미리 보기 {#target-preview-on-android}

타겟 미리 보기를 사용하면 타겟 활동에 대해 엔드투 엔드 QA를 쉽게 수행하고 해당 활동을 장치에서 미리 볼 수 있습니다.

Target 미리 보기 설정 및 사용 방법에 대한 자세한 내용을 보려면 Adobe Target 사용 안내서에서 [Target 모바일 미리 보기](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/target-mobile-preview.html)로 이동하십시오.

>[!IMPORTANT]
>
>Target 미리 보기를 사용하려면 SDK 버전 4.14.0 이상이 필요합니다.

* **setPreviewRestartDeeplink**

   미리 보기 모드에서 미리 보기 선택 사항을 적용할 때 트리거되는 앱 딥링크를 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void setPreviewRestartDeeplink(String deeplink);
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```java
      Target.setPreviewRestartDeeplink("myapp://myhost"); 
      ```
