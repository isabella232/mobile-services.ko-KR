---
description: 사용자가 푸시 메시지에서 앱을 열었을 때 인앱 메시지 트리거를 푸시 메시지 ID로 설정할 수 있습니다.
seo-description: 사용자가 푸시 메시지에서 앱을 열었을 때 인앱 메시지 트리거를 푸시 메시지 ID로 설정할 수 있습니다.
seo-title: 푸시 메시지에서 앱이 열릴 때 인앱 메시지 트리거하기
title: 푸시 메시지에서 앱이 열릴 때 인앱 메시지 트리거하기
uuid: E 1 C 8 E 29 D -1 C 2 B -47 B 2-8 AB 2-6 B 6 E 15 DF 86 F 6
translation-type: tm+mt
source-git-commit: 114bce95e41c8e13695689dd2da2dbc04cb17ad7

---


# Trigger an in-app message when the app is opened from a push message{#trigger-an-in-app-message-when-the-app-is-opened-from-a-push-message}

사용자가 푸시 메시지에서 앱을 열었을 때 인앱 메시지 트리거를 푸시 메시지 ID로 설정할 수 있습니다.

1. 사용자에게 전송될 푸시 메시지에 대한 푸시 메시지 ID를 가져옵니다.

   메시지 생성 작업 과정 동안 URL에서 푸시 메시지 ID를 찾을 수 있습니다.

   다음은 한 예입니다.

   ![](assets/brandon_task1.png)

1. 다음 트리거로 인앱 메시지를 저장 및 활성화:

   `“a.push.payloadID” =`

   >[!TIP]
   >
   >푸시 메시지 ID는 1 단계에 있는 ID 입니다.

   이 트리거는 **[!UICONTROL 트리거]드롭다운 목록에서 사용할 수 없으므로 수동으로 추가해야 합니다.**

   ![](assets/brandon_task2.png)

1. 저장 후 1단계의 푸시 ID가 포함된 푸시 메시지를 보냅니다.
1. 푸시 메시지를 클릭하여 앱을 열고, 앱이 열릴 때 인앱 메시지가 표시되는지 확인합니다.

   테스트하는 동안, 다음 정보를 기억하십시오.

   * 인앱 메시지를 저장한 후에 호스팅된 구성 파일을 새 메시지로 업데이트하려면 약 45초가 소요됩니다.
   * 앱이 **새로** 시작될 경우 구성 파일 업데이트(새 인앱 업데이트)를 검색하므로 푸시 메시지를 클릭할 때 앱이 새로 시작되는지 확인해야 합니다.
   이는 일반적으로 세션 시간 초과가 발생했는지 확인해야 함을 의미합니다. 기본 시간 초과는 5분입니다.

