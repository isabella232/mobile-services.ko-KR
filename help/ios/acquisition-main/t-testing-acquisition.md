---
description: 다음은 장치 지문 파일을 기반으로 하는 기존 획득 캠페인 링크를 왕복하는 데 유용한 정보입니다.
seo-description: 다음은 장치 지문 파일을 기반으로 하는 기존 획득 캠페인 링크를 왕복하는 데 유용한 정보입니다.
seo-title: 기존 획득 테스트
solution: Marketing Cloud, Analytics
title: 기존 획득 테스트
uuid: E 0591 F 4 A-E 26 B -4 FE 4-97 C 1-A 6831 A 926 FA 5
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Testing legacy acquisition {#testing-legacy-acquisition}

다음은 장치 지문 파일을 기반으로 하는 기존 획득 캠페인 링크를 왕복하는 데 유용한 정보입니다.

모바일 앱이 아직 Google Play에 없을 경우 캠페인 링크를 생성할 때 모바일 앱을 대상으로 선택할 수 있습니다. 이 작업은 획득 링크를 클릭한 후 획득 서버가 사용자를 리디렉션하는 앱에만 영향을 미치며, 획득 링크를 테스트하는 기능에는 영향을 미치지 않습니다.

1. Navigate to **[!UICONTROL Use Legacy Acquisition Links]** in Adobe Mobile Services and generate an acquisition campaign URL.

   자세한 내용은 [기존 획득 링크 사용](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md)을 참조하십시오.

1. 앱을 설치할 모바일 장치에서 생성된 링크를 클릭합니다.

   Adobe 서버(`c00.adobe.com`)는 지문 파일을 저장한 다음 앱스토어로 리디렉션합니다. 테스트를 위해 앱을 다운로드할 필요는 없습니다.

1. 2단계에서 사용한 것과 동일한 모바일 장치에서 애플리케이션을 처음 시작합니다.

   이 문제를 방지하는 가장 쉬운 방법은 앱을 삭제했다가 다시 설치하는 것입니다.

다음 정보를 숙지하십시오.

* 획득 서버는 링크 클릭(2단계)과 앱 실행(3단계)에 기록된 IP 주소 및 사용자 에이전트 정보를 기반으로 한 속성 일치 기능을 제공합니다.
* HTTP 모니터링 도구를 사용하면 앱에서 전송된 히트를 모니터링하여 획득 속성을 확인할 수 있습니다.

>[!TIP]
>
>전송된 사용자 에이전트의 변형으로 인해 속성 확인이 실패할 수 있습니다.
