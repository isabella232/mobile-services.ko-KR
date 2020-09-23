---
description: 처리 규칙은 컨텍스트 데이터 변수로 보내는 데이터를 보고용으로 evar, prop 및 기타 변수에 복사하는 데 사용됩니다.
seo-description: 처리 규칙은 컨텍스트 데이터 변수로 보내는 데이터를 보고용으로 evar, prop 및 기타 변수에 복사하는 데 사용됩니다.
seo-title: 처리 규칙 및 컨텍스트 데이터
solution: Experience Cloud,Analytics
title: 처리 규칙 및 컨텍스트 데이터
topic: Developer and implementation
uuid: 51338ccd-fa52-4d9c-97c4-947a4100465d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 51%

---


# 처리 규칙 및 컨텍스트 데이터 {#processing-rules-and-context-data}

처리 규칙은 컨텍스트 데이터 변수로 보내는 데이터를 보고용으로 evar, prop 및 기타 변수에 복사하는 데 사용됩니다.

자세한 정보는 다음 내용을 참조하십시오.

* [Summit 2013에서 처리 규칙](https://tv.adobe.com/embed/1181/16506/) 교육
* 처리 규칙 사용 인증 받기

   처리 규칙에 대한 자세한 내용은 [처리 규칙 개요](https://docs.adobe.com/content/help/ko-KR/analytics/admin/admin-tools/processing-rules/processing-rules.html)를 참조하십시오.

처리 규칙을 사용하여 작업할 경우 다음 정보를 숙지하십시오.

* 네임스페이스를 사용하여 컨텍스트 데이터 변수를 그룹화할 수 있으므로 논리적 순서를 유지할 수 있습니다.

   예를 들어 제품에 대한 정보를 수집하려는 경우 다음 변수를 정의할 수 있습니다.

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* 컨텍스트 데이터 변수는 처리 규칙 인터페이스에서 알파벳순으로 정렬되어 동일한 네임스페이스에 있는 변수를 빠르게 볼 수 있습니다.

   evar 또는 prop 번호를 사용하여 컨텍스트 데이터 키의 이름을 지정하지 마십시오.

   ```js
   "eVar1":"jimbo"
   ```

   이 경우 처리 규칙에서 1회 매핑을 수행할 때 *약간* 더 쉬워질 수 있지만 디버깅 및 향후 코드 업데이트 중에 가독성을 잃게 되므로 더 어려울 수 있습니다. 대신 키 및 값에 대해 수사적 이름을 사용하십시오.

   ```js
   "username":"jimbo"
   ```

* 카운터 이벤트를 정의하는 컨텍스트 변수는 1로 설정해야 합니다.

   ```js
   "logon":"1"
   ```

* incrementor 이벤트를 정의하는 컨텍스트 데이터 변수에는 이벤트가 키로 사용되고 값이 값으로 증가할 수 있습니다.

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>Adobe는 &quot;`a.`&quot; 네임스페이스를 예약합니다. 이 제한 사항 이외에도 충돌을 피하려면 컨텍스트 데이터 변수가 로그인 회사에서 공유하게 사용되면 됩니다.

