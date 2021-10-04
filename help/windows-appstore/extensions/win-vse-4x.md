---
description: 이 확장은 프로젝트에서 Experience Cloud 솔루션 4.x Windows SDK에 대한 참조를 추가하는 훨씬 쉬운 방법을 제공합니다.
solution: Experience Cloud,Analytics
title: Experience Cloud 솔루션 4.x SDK용 Windows Visual Studio 확장 프로그램
topic-fix: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
exl-id: 63e9e5c7-2a12-47b3-a712-bf51e12821aa
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 13%

---

# Experience Cloud 솔루션 4.x SDK용 Windows Visual Studio 확장 프로그램 {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

이 확장은 프로젝트에서 Experience Cloud 솔루션 4.x Windows SDK에 대한 참조를 추가하는 훨씬 쉬운 방법을 제공합니다.

## GitHub에서 라이브러리 설치 {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)에서 Windows Universal SDK를 다운로드합니다.
1. 다운로드한 파일의 압축을 로컬로 해제합니다.
1. ADBMobileWindowsStoreVSIX.vsix 또는 ADBMobileWindowsPhoneVSIX.vsix 파일을 두 번 클릭하여 설치 관리자를 엽니다.

1. **[!UICONTROL 전역 위치]**&#x200B;를 선택하고 라이브러리를 설치합니다.

## 프로젝트에 참조 추가 {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Windows 8.1 또는 Windows Phone 8.1 프로젝트를 엽니다.
1. 참조 관리자(Reference Manager) 대화상자를 엽니다.

   ![](assets/ref_manager.png)

1. Windows 8.1 또는 Windows Phone 8.1의 **[!UICONTROL 확장]** 탭에서 **[!UICONTROL Mobile SDK Adobe]**&#x200B;를 찾아 선택합니다.
1. **[!UICONTROL 확인]**&#x200B;을 클릭하여 저장합니다.

   Adobe Mobile SDK가 프로젝트에 추가되고, 아직 추가되지 않은 경우 **[!UICONTROL Microsoft Visual C++ Runtime]** 패키지도 추가됩니다.

1. 구성 관리자에서 플랫폼 유형을 선택하고 앱 테스트를 시작합니다.
