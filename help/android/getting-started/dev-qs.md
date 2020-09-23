---
description: 다음은 Android 라이브러리를 구현하고 시작, 업그레이드, 세션, 참여 사용자 등의 라이프사이클 지표를 수집하는 데 유용한 정보입니다.
keywords: android;library;mobile;sdk
seo-description: 다음은 Android 라이브러리를 구현하고 시작, 업그레이드, 세션, 참여 사용자 등의 라이프사이클 지표를 수집하는 데 유용한 정보입니다.
seo-title: 핵심 구현 및 라이프사이클
solution: Experience Cloud,Analytics
title: 핵심 구현 및 라이프사이클
topic: Developer and implementation
uuid: af4d11ac-8245-46a0-9b3a-4a0a29cfbbb2
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 100%

---


# 핵심 구현 및 라이프사이클 {#core-implementation-and-lifecycle}

다음은 Android 라이브러리를 구현하고 시작, 업그레이드, 세션, 참여 사용자 등의 라이프사이클 지표를 수집하는 데 유용한 정보입니다.

## SDK 다운로드 {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>SDK를 다운로드하려면 Android 2.2 이상을 사용해야 합니다.

1. 다음 섹션의 단계를 완료하여 개발 보고서 세트를 설정하고 미리 채워진 구성 파일 버전을 다운로드합니다.

   * [보고서 세트 만들기](/help/android/getting-started/requirements.md)
   * [SDK 다운로드](/help/android/getting-started/requirements.md)

1. `[Your_App_Name_]AdobeMobileLibrary-4.*-Android.zip` 파일을 다운로드하고 압축 해제한 후 다음 소프트웨어 구성 요소가 있는지 확인합니다. 

   * `adobeMobileLibrary.jar`: Android 장치 및 시뮬레이터에서 사용할 라이브러리입니다.

   * `ADBMobileConfig.json`: 앱에 맞게 사용자 지정된 SDK 구성 파일입니다.
   >[!IMPORTANT]
   >
   >Adobe Mobile Services UI 외부에서 SDK를 다운로드하는 경우에는 `ADBMobileConfig.json` 파일을 수동으로 구성해야 합니다. Analytics 및 Mobile SDK를 처음 사용하는 경우 개발 보고서 세트를 설정하고 미리 채워진 구성 파일 버전을 다운로드하려면 [시작하기 전에](/help/android/getting-started/requirements.md)를 참조하십시오.

## IntelliJ IDEA 또는 Eclipse 프로젝트에 SDK 및 구성 파일 추가 {#section_B89510FBB4C646AEA73A185B966E54D3}

**IntelliJ IDEA 프로젝트**

프로젝트에 SDK 및 구성 파일을 추가하려면

1. 프로젝트의 `assets` 폴더에 `ADBMobileConfig.json` 파일을 추가합니다.

1. 프로젝트 탐색 패널에서 프로젝트를 마우스 오른쪽 단추로 클릭합니다.
1. **[!UICONTROL 모듈 설정 열기를 선택합니다]**.
1. **[!UICONTROL 프로젝트 설정]**&#x200B;에서 **[!UICONTROL 라이브러리]**&#x200B;를 선택합니다.
1. **[!UICONTROL +]** 아이콘을 클릭하여 새 라이브러리를 추가합니다.
1. **[!UICONTROL Java]**&#x200B;를 선택하고 `adobeMobileLibrary.jar` 파일로 이동합니다.
1. 모바일 라이브러리를 사용할 모듈을 선택합니다.
1. **[!UICONTROL 적용]**&#x200B;을 클릭한 다음 **[!UICONTROL 확인]**&#x200B;을 클릭하여 모듈 설정 창을 닫습니다.

**Eclipse 프로젝트**

프로젝트에 SDK 및 구성 파일을 추가하려면

1. 프로젝트의 `assets` 폴더에 `ADBMobileConfig.json` 파일을 추가합니다.
1. **[!UICONTROL Eclipse IDE]**&#x200B;에서 프로젝트 이름을 마우스 오른쪽 단추로 클릭합니다.
1. **[!UICONTROL 빌드 경로]** > **[!UICONTROL 외부 아카이브 추가]**&#x200B;를 클릭합니다.
1. 선택 `adobeMobileLibrary.jar`.
1. **[!UICONTROL 열기를 클릭합니다]**.
1. 다시 프로젝트를 마우스 오른쪽 단추로 클릭한 다음 **[!UICONTROL 빌드 경로]** > **[!UICONTROL 빌드 경로 구성]**&#x200B;을 선택합니다.
1. **[!UICONTROL 주문 및 내보내기]** 탭에서 **`adobeMobileLibrary.jar`**&#x200B;이 선택되었는지 확인합니다.

## 앱 권한 추가 {#section_2EAF73ABF6424647B219A63B33B02CD5}

AppMeasurement 라이브러리를 사용하려면 데이터를 전송하고 오프라인 추적 호출을 기록할 다음 권한이 필요합니다.

* `INTERNET`
* `ACCESS_NETWORK_STATE`

이러한 권한을 추가하려면 애플리케이션 프로젝트 디렉터리의 `AndroidManifest.xml` 파일에 다음 줄을 추가합니다.

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

## 애플리케이션 컨텍스트 설정 {#set-application-context}

기본 활동의 `onCreate` 메서드에 다음 코드를 추가해야 합니다.

```java
   @Override
   public void onCreate(BundlesavedInstanceState){
     super.onCreate(savedInstanceState)
     setContentView(R.layout.main);
     Config.setContext(this.getApplicationContext());
   }
```

## 라이프사이클 지표 구현 {#section_BA686C09021F474AADDE8690BBB910F7}

라이프사이클을 사용하면 앱이 시작될 때마다 시작, 업그레이드, 세션, 참여 사용자 및 기타 여러 지표를 측정하기 위해 한 번의 히트가 전송됩니다. 자세한 내용은 [라이프사이클 지표](/help/android/metrics.md)를 참조하십시오.

**애플리케이션의 각 활동에서 다음 단계를 완료합니다.**

1. 라이브러리를 가져옵니다:

   ```java
   import com.adobe.mobile.*;
   ```

1. `onResume` 함수에서 라이프사이클 데이터 수집을 시작합니다.

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
       // -or- Config.collectLifecycleData(this, contextData); 
   }
   ```

1. `onPause` 함수에서 라이프사이클 데이터 수집을 일시 중지합니다.

   ```java
   @Override 
   public void onPause() { 
       Config.pauseCollectingLifecycleData(); 
   }
   ```

>[!IMPORTANT]
>
>정확한 충돌 보고를 위해 모든 활동에 이러한 호출을 추가해야 합니다. 자세한 내용은 [앱 충돌 추적](/help/android/analytics-main/crashes.md)을 참조하십시오.

## 라이프사이클 호출로 추가 데이터 포함

라이프사이클 지표 호출을 통해 추가 데이터를 포함하려면 컨텍스트 데이터가 포함된 `collectLifecycleData`에 추가 매개 변수를 전달하십시오.

```java
@Override 
public void onResume() {
    HashMap<String, Object> contextData = new HashMap<String, Object>(); 
    contextData.put("myapp.category", "Game"); 
    Config.collectLifecycleData(this, contextData); 
}
```

`collectLifecycleData`와 함께 전송되는 추가 컨텍스트 데이터 값은 Adobe Mobile Services의 사용자 지정 변수에 매핑해야 합니다.

![](assets/map-variable-lifecycle.png)

다른 라이프사이클 지표는 자동으로 수집됩니다. 자세한 내용은 [라이프사이클 지표](/help/android/metrics.md)를 참조하십시오.

## 다음 단계 {#section_BF709684E1DD40EA9169BC1D0D4B37C2}

다음 작업을 완료하십시오.

* [앱 상태 추적](/help/android/analytics-main/states.md)
* [앱 작업 추적](/help/android/analytics-main/actions.md)

