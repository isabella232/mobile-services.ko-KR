---
description: 이 확장은 프로젝트에서 Experience Cloud 솔루션 4.x Windows SDK에 대한 참조를 추가하는 훨씬 쉬운 방법을 제공합니다.
solution: Experience Cloud Services,Analytics
title: Experience Cloud 솔루션 4.x SDK용 Windows Visual Studio 확장 프로그램
topic-fix: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
exl-id: 8ed91dc1-8f30-4788-8471-21bb54256b0b
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 14%

---

# Experience Cloud 솔루션 4.x SDK용 Windows Visual Studio 확장 프로그램 {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

이 확장은 프로젝트에서 Experience Cloud 솔루션 4.x Windows SDK에 대한 참조를 추가하는 훨씬 쉬운 방법을 제공합니다.

## GitHub에서 라이브러리 설치 {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Windows Universal SDK 다운로드 위치 [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Unzip the downloaded file locally.
1. 를 두 번 클릭합니다. **[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix]** 파일을 사용하여 설치 관리자를 엽니다.
1. 선택 **[!UICONTROL 전역 위치]** 라이브러리를 설치합니다.

## Add references to your project {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Windows 10 프로젝트를 엽니다.
1. 참조 관리자(Reference Manager) 대화상자를 엽니다.

   ![](assets/ref_manager.png)

1. On the **[!UICONTROL Extensions]** tab, locate and select **[!UICONTROL Adobe Mobile SDK]**.
1. 클릭 **[!UICONTROL 확인]** 저장하려고

   Adobe Mobile SDK가 프로젝트에 추가됩니다. 만약 **[!UICONTROL Microsoft Visual C++ Runtime]** 패키지가 아직 추가되지 않았습니다. 이 패키지가 프로젝트에 추가됩니다.

1. In the Configuration Manager, select a a platform type and begin testing your app.
