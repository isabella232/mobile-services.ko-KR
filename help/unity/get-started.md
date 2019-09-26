---
description: 이 플러그인으로 Unity 애플리케이션에서 Adobe Analytics 호출을 보낼 수 있습니다.
keywords: Unity
seo-description: 이 플러그인으로 Unity 애플리케이션에서 Adobe Analytics 호출을 보낼 수 있습니다.
seo-title: iOS 및 Android 4.x SDK용 Unity 플러그인
solution: Marketing Cloud,Developer
title: iOS 및 Android 4.x SDK용 Unity 플러그인
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
translation-type: tm+mt
source-git-commit: 5fbba02eb61679344f638b6465e47b0d9ae5a988

---


# iOS 및 Android 4.x SDK용 Unity 플러그인 {#unity-plug-in-for-the-ios-and-android-x-sdks}

이 플러그인으로 Unity 애플리케이션에서 Adobe Analytics 호출을 보낼 수 있습니다.

마지막 업데이트: **2016년 10월 20일**

## 시작하기 {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

GitHub 또는 Developer Connection에서 [ADBMobile.unitypackage](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) 파일을 다운로드합니다.

Here are the contents of the  file:`ADBMobile.unitypackage`

* Assets (root)

   * ADBMobile

      * 데모

         * ADBMobileDemo.cs
         * BooDemo.boo
         * BooScene.unity
         * CSharpScene.unity
         * JavaScriptDemo.js
         * JavaScriptScene.unity
         * SecondScene.unity
         * SecondSceneScript.cs
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



선택적 폴더: 데모 폴더에는 지원되는 각 스크립트 언어에 대한 샘플 코드와 Unity 장면이 있습니다.

## Unity 프로젝트로 ADBMobile 플러그인 가져오기 {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Unity 프로젝트를 엽니다.
1. **[!UICONTROL ADBMobile.unitypackage를 더블클릭합니다]**.
1. 가져오려는 폴더를 선택합니다.

