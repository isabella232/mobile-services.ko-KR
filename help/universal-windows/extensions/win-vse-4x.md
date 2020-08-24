---
description: 이 익스텐션은 프로젝트에서 Experience Cloud 솔루션 4.x Windows SDK에 대한 참조를 훨씬 쉽게 추가할 수 있는 방법을 제공합니다.
seo-description: 이 익스텐션은 프로젝트에서 Experience Cloud 솔루션 4.x Windows SDK에 대한 참조를 훨씬 쉽게 추가할 수 있는 방법을 제공합니다.
seo-title: Experience Cloud 솔루션용 Windows Visual Studio 확장 4.x SDK
solution: Marketing Cloud,Analytics
title: Experience Cloud 솔루션용 Windows Visual Studio 확장 4.x SDK
topic: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
translation-type: tm+mt
source-git-commit: 38e63d6f4f85c2ced6364baa47646241ac783c12
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 2%

---


# Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

이 익스텐션을 사용하면 프로젝트에서 Experience Cloud 솔루션 4.x Windows SDK에 대한 참조를 훨씬 쉽게 추가할 수 있습니다.

## GitHub에서 라이브러리 설치 {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. GitHub에서 Windows Universal SDK를 [다운로드합니다](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. 다운로드한 파일의 압축을 해제합니다.
1. ADBMobileUniversalWindowsVSIX.vsix **[!UICONTRTOL ]** 파일을 두 번 클릭하여 설치 관리자를 엽니다.
1. [ **[!UICONTROL 전역 위치]** ]를 선택하고 라이브러리를 설치합니다.

## 프로젝트에 참조 추가 {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Windows 10 프로젝트를 엽니다.
1. 참조 관리자(Reference Manager) 대화상자를 엽니다.

   ![](assets/ref_manager.png)

1. [ **[!UICONTROL 확장]** ] 탭에서 **[!UICONTROL Adobe Mobile SDK를 찾아 선택합니다]**.
1. 확인을 **[!UICONTROL 클릭하여]** 저장합니다.

   Adobe Mobile SDK가 프로젝트에 추가됩니다. Microsoft **[!UICONTROL Visual C++ 런타임]** 패키지가 아직 추가되지 않은 경우 이 패키지가 프로젝트에 추가됩니다.

1. 구성 관리자에서 플랫폼 유형을 선택하고 앱 테스트를 시작합니다.

