---
description: .xml 파일을 직접 대체하여 TVML/TVJS 앱에서 Adobe Target을 활용할 수 있습니다. 사용자 지정 ADBTarget XML 요소를 사용하여 페이지의 영역을 Target 컨텐츠으로 대체하도록 지정합니다.
title: TVML/TVJS용 Adobe Target
uuid: afd5a583-5266-43f2-8cb0-0ace89c53a57
exl-id: 9348d49c-2a5a-4ea0-b90d-99d446bd336a
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 75%

---

# TVML/TVJS용 Adobe Target{#adobe-target-for-tvml-tvjs}

.xml 파일을 직접 대체하여 TVML/TVJS 앱에서 Adobe Target을 활용할 수 있습니다. 사용자 지정 ADBTarget XML 요소를 사용하여 페이지의 영역을 Target 컨텐츠으로 대체하도록 지정합니다.

>[!IMPORTANT]
>
>TVML 페이지에서 `ADBTarget` 요소를 사용하기 전에 tvOS SDK를 사용하도록 TVML/TVJS 앱을 구성해야 합니다. 자세한 내용은 [tvOS를 사용한 Apple TV 구현](/help/ios/apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)을 참조하십시오.

## 시작하기 {#section_88445645FD67416EAF6FDC3E3D3F5C33}

1. Target 위치를 사용할 `.xml` 파일을 확인합니다.
1. `ADBTarget` 요소를 `<document>` 요소의 하위 요소로 파일에 추가합니다.
1. Target이 Mbox 위치를 찾지 못하거나 시간이 초과되면 `<ADBTarget>` 및 `</ADBTarget>` 태그 사이의 값이 기본 콘텐츠로 사용됩니다.

## Target에서 Mbox 구성 {#section_F2DA140C34B0421D976046F825B23123}

Target에서 반환된 콘텐츠는 `<ADBTarget>` 태그를 모두 포함하여 `</ADBTarget>`과 `ADBTarget` 사이에서 모든 콘텐츠를 대체합니다.

>[!TIP]
>
>어떤 콘텐츠를 대체할 것인지 적절히 계획해야 합니다.

사용 사례는 레이블의 문자열 값을 대체하는 것처럼 간단하거나, 페이지 전체를 대체하는 것처럼 복잡할 수도 있습니다.

## ADBTarget 요소 구성 {#section_44A7AEC6FC0648ADAD0BACB57D493AFA}

`ADBTarget` 요소에서 `mbox` 속성에 Mbox 이름을 제공해야 합니다. 요청에 사용자 지정 속성을 `customParameterName="customParameterValue"` 형식으로 선택적으로 추가할 수 있습니다.

* **`mbox`**

   Mbox 위치 이름.

   * 속성 유형: 문자열
   * 이 속성은 필수입니다.

* **`id`**

   주문 ID.

   * 속성 유형: 문자열
   * 이 속성은 필수가 **아닙니다**.

* **`total`**

   주문 총계.

   * 속성 유형: 문자열
   * 이 속성은 필수가 **아닙니다**.

* **`purchasedProductIds`**

   이 주문에 대해 구입한 제품 ID를 쉼표로 구분한 목록입니다.

   * 다음은 이 속성의 코드 샘플입니다.


      ```objective-c
      purchasedProductIds="product1,product2,product3" 
      ```

   * 속성 유형: 문자열
   * 이 속성은 필수가 **아닙니다**.

* **`mboxParameters`**

   `mboxParameters`의 키 값 쌍 목록입니다. 이 문자열의 각 항목은 세미콜론(;)으로 구분되며 키 값은 콜론(:)으로 구분됩니다.

   * 다음은 이 속성의 코드 샘플입니다.

      ```objective-c
      mboxParameters="mboxparameterKey:mboxParameterValue;mboxParameterKey1:mboxParameterValue1;mboxParameterKey2:mboxParameterValue2"
      ```

   * 속성 유형: 문자열
   * 이 속성은 필수가 **아닙니다**.

* **`customParameterName`**

   이 속성 값은 `customParameterValue`입니다.

   * 속성 유형: 문자열
   * 이 속성은 필수가 **아닙니다**.


## 예시 {#section_6D6D6E8C7FE147168FC30D83CBC06985}

### 예제 1

다음 예에서는 `ADBTarget` 페이지의 `LandingPage.xml.js` 요소를 사용하여 경고 내용을 바꿉니다.

#### Target 구성

`landingPage`라는 이름의 Mbox 위치가 있고 오퍼 콘텐츠가 다음과 같이 설정되어 있다고 가정합니다.

```objective-c
<title>My cool landing page</title> 
<description>Thanks for coming to my page</description> 
```

#### landingPage.xml.js 구성

* 다음은 landingPage.xml.js에 대한 구성입니다.

   ```js
   <alertTemplate> 
       <ADBTarget mbox="landingPage">  
           <title>TargetTestPage</title> 
           <description>Load fail or timeout (defaultContent)</description> 
       </ADBTarget>  
   </alertTemplate> 
   ```

* Target 요청이 성공하고 오퍼 콘텐츠가 반환되면 페이지에 다음과 같은 결과가 표시됩니다.

   ```objective-c
   <alertTemplate> 
       <title>My cool landing page</title> 
       <description>Thanks for coming to my page</description> 
   </alertTemplate>
   ```

* Target 서버에 연결할 수 없거나 요청 시간이 초과되면 페이지에 다음이 표시됩니다.

   ```objective-c
   <alertTemplate> 
       <title>TargetTestPage</title> 
       <description>Load fail or timeout (defaultContent)</description> 
   </alertTemplate>
   ```

### 예제 2

다음 예에서는 `ADBTarget` 요소에 사용자 지정 데이터를 추가하는 방법을 보여줍니다. 이 메서드를 사용하면 조건부 환경을 만들고 타겟에서 이 Mbox 위치에 대한 콘텐츠를 제공할 수 있습니다.

```objective-c
<alertTemplate> 
    <ADBTarget mbox="landingPage" customData="custom data" moreCustomData="more custom data"> 
        <title>TargetTestPage</title> 
        <description>Load fail or timeout (defaultContent)</description> 
    </ADBTarget>  
</alertTemplate>
```
