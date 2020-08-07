---
description: 타겟 미리 보기를 사용하면 타겟 활동에 대해 엔드투 엔드 QA를 쉽게 수행하고 해당 활동을 장치에서 미리 볼 수 있습니다.
seo-description: 타겟 미리 보기를 사용하면 타겟 활동에 대해 엔드투 엔드 QA를 쉽게 수행하고 해당 활동을 장치에서 미리 볼 수 있습니다.
seo-title: iOS에서 타겟 미리 보기
title: iOS에서 타겟 미리 보기
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 87%

---


# iOS에서 타겟 미리 보기{#target-preview-on-ios}

타겟 미리 보기를 사용하면 타겟 활동에 대해 엔드투 엔드 QA를 쉽게 수행하고 해당 활동을 장치에서 미리 볼 수 있습니다.

Target 미리 보기 설정 및 사용 방법에 대한 자세한 내용은 [Target 모바일 미리 보기](https://docs.adobe.com/content/help/ko-KR/target/using/implement-target/mobile-apps/target-mobile-preview.html)를 참조하십시오.

>[!IMPORTANT]
>
>Target 미리 보기를 사용하려면 SDK 버전 4.14.0 이상이 필요합니다.

## Target 미리 보기 메서드

* **setPreviewRestartDeplink**

   미리 보기 모드에서 미리 보기 선택 사항을 적용할 때 트리거되는 앱 기본값을 설정합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * 다음은 이 메서드의 코드 샘플입니다.

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@" myapp://myhost"]; 
      ```
