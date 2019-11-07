---
description: 처리 규칙은 컨텍스트 데이터 변수로 보내는 데이터를 보고용으로 evar, prop 및 기타 변수에 복사하는 데 사용됩니다.
seo-description: 처리 규칙은 컨텍스트 데이터 변수로 보내는 데이터를 보고용으로 evar, prop 및 기타 변수에 복사하는 데 사용됩니다.
seo-title: 처리 규칙 및 컨텍스트 데이터
solution: Marketing Cloud,Analytics
title: 처리 규칙 및 컨텍스트 데이터
topic: 개발자 및 구현
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
translation-type: ht
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# 처리 규칙 및 컨텍스트 데이터 {#processing-rules-and-context-data}

처리 규칙은 컨텍스트 데이터 변수로 보내는 데이터를 보고용으로 evar, prop 및 기타 변수에 복사하는 데 사용됩니다. 자세한 내용은 [처리 규칙](https://docs.adobe.com/content/help/ko-KR/analytics/admin/admin-tools/processing-rules/processing-rules.html)을 참조하십시오.

처리 규칙을 사용하여 작업할 경우 다음 정보를 숙지하십시오.

* 네임스페이스를 사용하여 컨텍스트 데이터 변수를 그룹화하십시오. 이렇게 하면 논리적 순서를 유지할 수 있습니다. 예를 들어 제품에 대한 정보를 수집할 경우 다음 변수를 정의할 수 있습니다.

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* 컨텍스트 데이터 변수는 처리 규칙 인터페이스에서 알파벳순으로 정렬되어 동일한 네임스페이스에 있는 변수를 빠르게 확인할 수 있습니다.

   컨텍스트 데이터 키의 이름을 지정할 경우 evar 또는 prop 번호를 사용하지 마십시오.

   ```js
   "eVar1":"jimbo"
   ```

   이렇게 하면 처리 규칙에서 일회 매핑을 완료할 때 *약간* 간편해질 수 있지만 디버깅 및 향후 코드 업데이트에서는 가독성이 떨어져 더 어려워질 수 있습니다. 대신 키와 값에 대한 설명이 포함된 이름을 사용하는 것이 좋습니다.

   ```js
   "username":"jimbo"
   ```

* 카운터 이벤트를 정의하는 컨텍스트 변수는 1로 설정해야 합니다.

   ```js
   "logon":"1"
   ```

* 상향 이벤트를 정의하는 컨텍스트 데이터 변수는 이벤트를 키로, 상향할 값을 값으로 설정할 수 있습니다.

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>Adobe는 `"a."` 네임스페이스를 예약합니다. 충돌을 피하려면 컨텍스트 데이터 변수가 로그인 회사에서 고유하게 사용되면 됩니다.

