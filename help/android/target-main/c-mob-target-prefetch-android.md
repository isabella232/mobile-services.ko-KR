---
description: Adobe Target 미리 가져오기 기능은 Android Mobile SDK를 사용하여 서버 응답을 캐싱하여 가능한 한 적은 시간에 오퍼 콘텐츠를 가져옵니다.
seo-description: Adobe Target 미리 가져오기 기능은 Android Mobile SDK를 사용하여 서버 응답을 캐싱하여 가능한 한 적은 시간에 오퍼 콘텐츠를 가져옵니다.
seo-title: Android에서 오퍼 컨텐츠 미리 가져오기
title: Android에서 오퍼 컨텐츠 미리 가져오기
uuid: 063451b8-e191-4d58-8ed8-1723e310ad1a
translation-type: tm+mt
source-git-commit: fa7375ac8a1345d81748bcf635791c46d3943fed

---


# Android에서 오퍼 컨텐츠 미리 가져오기 {#prefetch-offer-content-in-android}

Adobe Target 미리 가져오기 기능은 Android Mobile SDK를 사용하여 서버 응답을 캐싱하여 가능한 한 적은 시간에 오퍼 콘텐츠를 가져옵니다.

>[!IMPORTANT]
>
>Prefetch functionality in the Mobile SDKs for Android is not supported for Auto Target, Auto Allocate, and Automated Personalization activity types in Adobe Target.

이 프로세스는 로드 시간을 줄이고, 다중 네트워크 호출을 방지하며, 모바일 앱 사용자가 방문한 mbox를 Adobe Target에 알려줄 수 있도록 해줍니다. 모든 컨텐츠는 미리 가져오기 호출 중에 검색되고 캐시되며, 이 컨텐츠는 지정된 mbox 이름에 대해 캐시된 컨텐츠를 포함하는 이후의 모든 호출에 대한 캐시에서 검색됩니다.

미리 가져오기 컨텐츠는 실행 간에는 지속되지 않으며, The prefetch content is cached as long as the application lives or until the `clearPrefetchCache()` method is called.

>[!IMPORTANT]
>
>Target prefetch APIs have been available since SDK version 4.14.0. For more information about parameter limitations, see [Batch-input-parameters](https://developers.adobetarget.com/api/#batch-input-parameters).

SDK 버전 4.14 이상에서는 지정되는 경우 v2 batch mbox TnT 호출을 시작할 때 파일에서`environmentId``ADBMobileConfig.json`가 선택됩니다. 이 파일에 `environmentId` 가 지정되지 않은 경우, TNT batch mbox 호출에서 환경 매개 변수가 전송되지 않고 기본 환경에 대한 오퍼가 전달됩니다.

예:

```java
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## Pre-fetch methods {#section_05967F1F3A554B0FBC2C08A954554BDE}

Android에서 미리 가져오기에 사용할 수 있는 메서드는 다음과 같습니다.

* **prefetchContent**

   구성된 Target 서버에 다수의 위치를 사용하는 미리 가져오기 요청을 전송하고 제공된 콜백에서 요청 상태를 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void prefetchContent(
      final List<TargetPrefetchObject> targetPrefetchArray,
      final Map<String, Object> profileParameters,
      final TargetCallback<Boolean> callback)
      ```

   * Here are the parameters for this method:

      * **targetPrefetchArray**

         미리 가져올 각 Target 위치에 대한 이름 및 mboxParameters를 포함하는 `TargetPrefetchObjects` 배열입니다.

      * **profileParameters**

         이 요청의 모든 위치 미리 가져오기에 사용할 프로필 매개 변수의 키 및 값을 포함합니다.

      * **callback**

         미리 가져오기가 완료되면 호출됩니다. Returns `true` if the prefetch was successful and `false` if the prefetch was unsuccesful.

* **loadRequests**

   요청 배열에 지정된 여러 mbox 위치에 대한 배치 요청을 실행합니다.  배열에 있는 각 개체는 제공된 mbox 위치에 컨텐츠를 사용할 수 있을 때 호출되는 콜백 함수를 포함합니다.

   >[!IMPORTANT]
   >
   >요청된 위치에 대한 컨텐츠가 이미 캐시되면 제공된 콜백에서 즉시 반환됩니다. 그렇지 않으면 Target 서버에 컨텐츠를 검색하도록 SDK가 네트워크 요청을 보냅니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void loadRequests( final List<TargetRequestObject> requestArray,  final Map<String, Object> profileParameters)
      ```

   * Here are the parameters for this method:

      * **requestArray**

         검색할 위치에 대한 이름, 기본 컨텐츠, 매개 변수 및 콜백 함수를 포함하는 `TargetRequestObjects` 배열입니다.

      * **profileParameters**

         이 요청의 모든 위치 미리 가져오기에 사용할 프로필 매개 변수의 키 및 값을 포함합니다.

* **clearPrefetchCache**

   Target 미리 가져오기에 의해 캐시된 데이터를 지웁니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static void clearPrefetchCache();
      ```

   * There are no parameters for this method.

* **createTargetRequestObject**

   제공된 데이터로 `TargetRequestObject` 인스턴스를 생성 및 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static TargetPrefetchObject createTargetRequestObject( 
      final String mboxName,
      final String defaultContent, 
      final Map<String, Object> mboxParams, 
      final Map<String, Object> orderParams, 
      final Map<String, Object> productParams, 
      final Target.TargetCallback<String> callback)
      ```

* **createTargetPrefetchObject**

   제공된 데이터로 TargetPrefetchObject 인스턴스를 생성 및 반환합니다.

   * 다음은 이 메서드에 대한 구문입니다.

      ```java
      public static TargetPrefetchObject createTargetPrefetchObject( 
      final String mboxName, 
      final Map<String, Object> mboxParams) 
      final Map<String, Object> orderParams, 
      final Map<String, Object> productParams)
      ```

## Public classes {#section_A273E53F069E4327BBC8CE4910B37888}

다음은 Android에서 미리 가져오기를 지원하는 공용 클래스입니다.

### 클래스 참조:TargetPrefetchObject

mbox 미리 가져오기에 사용되는 mbox 이름 및 매개 변수를 캡슐화합니다.

* **`name`**

   미리 가져올 위치의 이름입니다.
   * **유형**: 문자열

* `mboxParameters`

   이 `mboxParameters`의 요청에 대해 `TargetPrefetchObject`로서 첨부할 키-값 쌍의 컬렉션입니다.
   * **유형**:맵`<String, Object>`

* **`orderParameters`**

   order 노드 아래에 있는 현재 mbox에 첨부할 키-값 쌍의 컬렉션입니다.
   * **Type: Map**`<String, Object>`

* **`productParameters`**

   product 노드 아래에 있는 현재 mbox에 첨부할 키-값 쌍의 컬렉션입니다.

   * **Type: Map**`<String, Object>`


### 클래스 참조:TargetRequestObject

이 클래스는 Target 위치 요청에 사용되는 mbox 이름, 기본 컨텐츠, mbox 매개 변수 및 반환 콜백을 캡슐화합니다.

* **`mboxName`**

   요청된 위치의 이름입니다.

   * **유형**: 문자열

* **`mboxParameters`**

   이 `mboxParameters`에 대해 `TargetRequestObject`로서 첨부할 키-값 쌍의 컬렉션입니다.

   * **유형:맵`<String, Object>`**

* **`orderParameters`**

   order 노드 아래에 있는 현재 mbox에 첨부할 키-값 쌍의 컬렉션입니다.

   * **유형**:맵 `<String, Object>`

* **`productParameters`**

   product 노드 아래에 있는 현재 mbox에 첨부할 키-값 쌍의 컬렉션입니다.

   * **Type: Map**`<String, Object>`

* **`defaultContent`**

   SDK가 Target 서버에서 컨텐츠를 검색할 수 없는 경우 콜백에서 반환되는 문자열 값입니다.

   * **유형**: 문자열

* **`callback`**

   제공된 `TargetRequestObject`의 컨텐츠를 사용할 수 있을 때 호출되는 함수 포인터입니다.

   * **유형**:Target.TargetCallback`<String>`


## Code sample {#section_BF7F49763D254371B4656E17953D520C}

다음은 Android SDK를 사용하여 컨텐츠를 미리 가져오는 방법의 예입니다.

```java
// When your app launches, prefetch the content for a list of locations. 
// Define the list of mboxes that you want to prefetch. 
List<TargetPrefetchObject> prefetchMboxesList = new ArrayList<>(); 
  
Map<String, Object> mboxParameters1 = new HashMap<>(); 
mboxParameters1.put("status", "platinum"); 
prefetchMboxesList.add(Target.createTargetPrefetchObject("mboxName1", mboxParameters1));

Map<String, Object> mboxParameters2 = new HashMap<>(); 
mboxParameters2.put("userType", "paid"); 
 
List<String> purchasedIds = new ArrayList<String>(); 
purchasedIds.add("34"); 
purchasedIds.add("125");  
Map<String, Object> orderParameters2 = new HashMap<>(); 
orderParameters2.put("id", "ADCKKIM"); 
orderParameters2.put("total", "344.30"); 
orderParameters2.put("purchasedProductIds",  purchasedIds); 
  
Map<String, Object> productParameters2 = new HashMap<>(); 
productParameters2.put("id", "24D3412"); 
productParameters2.put("categoryId","Books"); 
  
prefetchMboxesList.add(Target.createTargetPrefetchObject("mboxName2", mboxParameters2, orderParameters2, productParameters2));

// Define the profile parameters map. 
Map<String, Object> profileParameters = new HashMap<>(); 
profileParameters.put("ageGroup", "20-32");

// Define the target callback for the prefetch call status. 
Target.TargetCallback<Boolean> prefetchStatusCallback = new Target.TargetCallback<Boolean>() { 
    @Override 
    public void call(final Boolean status) { 
        // check the returned status for the prefetch call 
    }};

// Call the prefetchContent API. 
Target.prefetchContent(prefetchMboxesList, profileParameters, prefetchStatusCallback);

// When the content is required, you can initiate the locations request. 
// Define the list of target request objects. 
List<TargetRequestObject> locationRequests = new ArrayList<>(); 
  
Target.TargetCallback<String> callback1 = new Target.TargetCallback<String>() { 
    @Override 
    public void call(final String content) { 
        // check the returned content for mboxName1. 
    }}; 
  
locationRequests.add(Target.createTargetRequestObject("mboxName1", "defaultContent1", mboxParameters1, callback1));

Target.TargetCallback<String> callback2 = new Target.TargetCallback<String>() { 
    @Override 
    public void call(final String content) { 
        // check the returned content for mboxName2. 
    }}; 
  
locationRequests.add(Target.createTargetRequestObject("mboxName2", "defaultContent2", mboxParameters2, orderParameters2, productParameters2, callback2)); 
  
// Call the loadRequests API. 
Target.loadRequests(locationRequests, profileParameters); 
```

## 추가 정보 {#section_A454BAD1CD49423E86C71BAEE06125FD}

다음은 이러한 샘플에 대한 추가 정보입니다.

* `ProductParameters`는 다음 키만 허용합니다.

   * `id`
   * `categoryId`

* `OrderParameters`는 다음 키만 허용합니다.

   * `id`
   * `total`
   * `purchasedProductIds`

* `purchasedProducts`는 문자열의 ArrayList를 허용합니다.
