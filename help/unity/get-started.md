---
description: 이 플러그인으로 Unity 애플리케이션에서 Adobe Analytics 호출을 보낼 수 있습니다.
keywords: Unity
seo-description: 이 플러그인으로 Unity 애플리케이션에서 Adobe Analytics 호출을 보낼 수 있습니다.
seo-title: iOS 및 Android 4.x SDK용 Unity 플러그인
solution: Marketing Cloud,Developer
title: iOS 및 Android 4.x SDK용 Unity 플러그인
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
translation-type: ht
source-git-commit: 0d50c7e6674de33b8190e74c113ae010ff226e97

---


# iOS 및 Android 4.x SDK용 Unity 플러그인 {#unity-plug-in-for-the-ios-and-android-x-sdks}

이 플러그인으로 Unity 애플리케이션에서 Adobe Analytics 호출을 보낼 수 있습니다.

마지막 업데이트: **2020년 3월 10일**
* [Unity-v4.19.0](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases/tag/v4.19.0-Unity)

## 시작하기 {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

GitHub에서 ADBMobile.unitypackage 파일을 다운로드합니다.

아래는 `ADBMobile.unitypackage` 파일의 컨텐츠입니다.

* Assets (root)

   * ADBMobile

   * 플러그인

      * ADBMobile.cs
      * Android

         * adobeMobileLibrary-{version}.jar
         * AndroidManifest.xml
         * 자산

            * ADBMobileConfig.json
      * iOS

         * ADBMobile.h
         * ADBMobileConfig.json
         * ADBMobileWrapper.h
         * ADBMobileWrapper.mm
         * AdobeMobileLibrary.a


**선택 폴더**: *데모* 폴더에는 Unity 장면과 샘플 코드가 포함되어 있습니다.

## Unity 프로젝트로 ADBMobile 플러그인 가져오는 중 {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Unity 프로젝트를 엽니다.
1. **[!UICONTROL ADBMobile.unitypackage]**&#x200B;를 더블클릭합니다.
1. 가져오려는 폴더를 선택합니다.
