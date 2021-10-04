---
description: 다음은 충돌을 추적하는 방법을 이해하고 허위 충돌을 처리하는 우수 사례를 확인하는 데 유용한 정보입니다.
solution: Experience Cloud,Analytics
title: 앱 충돌 추적
topic-fix: Developer and implementation
uuid: 3ab98c14-ccdf-4060-ad88-ec07c1c6bf07
exl-id: d8d59b4e-0231-446d-9ba1-8a9809be9c61
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 100%

---

# 앱 충돌 추적 {#track-app-crashes}

다음은 충돌을 추적하는 방법을 이해하고 허위 충돌을 처리하는 우수 사례를 확인하는 데 유용한 정보입니다.

>[!TIP]
>
>라이프사이클 지표의 일부로 앱 충돌이 추적됩니다. 충돌을 추적하기 전에 프로젝트에 라이브러리를 추가하고 라이프사이클을 구현합니다. 자세한 내용은 [핵심 구현 및 라이프사이클](/help/android/getting-started/dev-qs.md)에서 *IntelliJ IDEA 또는 Eclipse 프로젝트에 SDK 및 구성 파일 추가*&#x200B;를 참조하십시오.

라이프사이클 지표가 구현되면 각 활동의 `Config.collectLifecycleData` 메서드에서 `OnResume`에 대한 호출이 수행됩니다. `onPause` 메서드에서 `Config.pauseCollectingLifeCycleData`에 대한 호출이 수행됩니다.

`pauseCollectingLifeCycleData`에서 정상 종료를 나타내도록 플래그가 설정됩니다. 앱을 다시 실행하거나 재개하면 `collectLifecycleData`에서 이 플래그를 확인합니다. 앱이 제대로 종료되지 않았으며 이것이 플래그 상태에서 확인되는 경우, 그 다음 호출 시 `a.CrashEvent` 컨텍스트 데이터가 전송되고 충돌 이벤트가 보고됩니다.

정확한 충돌 보고를 보장하려면 각 활동의 `pauseCollectingLifeCycleData` 메서드에서 `onPause`를 호출해야 합니다. 다음은 이렇게 해야 하는 이유를 이해하기 위한 Android 활동 라이프사이클의 예시입니다.

![](assets/android-lifecycle.png)

Android 활동 라이프사이클에 대한 자세한 내용은 [활동](https://developer.android.com/guide/components/activities.html)을 참조하십시오.

*이 Android 라이프사이클 일러스트레이션은[Android 오픈 소스 프로젝트](https://source.android.com/)에서 생성 및 공유되었으며 [Creative Commons 2.5 Attribution License](https://creativecommons.org/licenses/by/2.5/)의 조항에 의거하여 사용됩니다.*

## 허위 충돌이 보고될 수 있는 원인은 무엇입니까?

1. Android Studio와 같은 IDE를 사용하여 디버깅 중인 경우 앱이 포그라운드에 있을 때 IDE에서 앱을 다시 시작하면 충돌이 발생합니다.

   >[!TIP]
   >
   >IDE에서 앱을 다시 시작하기 전에 먼저 앱을 백그라운드로 전환하면 이 충돌을 피할 수 있습니다.

1. 앱의 마지막 포그라운드 활동이 백그라운드로 전환된 후 `onPause`에서 `Config.pauseCollectingLifecycleData();`를 호출하지 않는 경우 앱이 수동으로 종료되거나 OS에 의해 종료되면 다음에 앱을 시작할 때 충돌이 발생합니다.

## 조각은 어떻게 처리해야 합니까?

조각에는 활동과 유사한 애플리케이션 라이프사이클 이벤트가 있습니다. 그러나 활동에 첨부되지 않으면 경험 구성요소를 활성화할 수 없습니다.

>[!IMPORTANT]
>
>포함 활동이 코드를 실행할 수 있는 라이프사이클 이벤트를 사용해야 합니다. 이 작업은 조각의 상위 보기에서 처리됩니다.

## (선택 사항) 활동 라이프사이클 콜백 구현

API 레벨 14부터 Android에서는 활동에 대한 전역 라이프사이클 콜백이 허용됩니다. 자세한 내용은 [애플리케이션](https://developer.android.com/reference/android/app/Application)을 참조하십시오.

이러한 콜백을 사용하여 모든 활동에서 `collectLifecycleData()` 및 `pauseCollectingLifecycleData()`를 올바르게 호출하는지 확인할 수 있습니다. 이 코드는 기본 활동 및 앱을 시작할 수 있는 다른 활동에만 추가해야 합니다.

```js
import com.adobe.mobile.Config; 
  
public class MainActivity extends Activity { 
... 
    @Override 
    protected void onCreate(Bundle savedInstanceState) { 
        super.onCreate(savedInstanceState); 
        setContentView(R.layout.activity_main); 
  
        getApplication().registerActivityLifecycleCallbacks(new Application.ActivityLifecycleCallbacks() { 
            @Override 
            public void onActivityResumed(Activity activity) { 
                Config.setContext(activity.getApplicationContext()); 
                Config.collectLifecycleData(activity); 
            } 
  
            @Override 
            public void onActivityPaused(Activity activity) {     
                Config.pauseCollectingLifecycleData(); 
            } 
    
            // the following methods aren't needed for our lifecycle purposes, but are required to be implemented 
            // by the ActivityLifecycleCallbacks object 
            @Override 
            public void onActivityCreated(Activity activity, Bundle savedInstanceState) {} 
            @Override 
            public void onActivityStarted(Activity activity) {} 
            @Override 
            public void onActivityStopped(Activity activity) {} 
            @Override 
            public void onActivitySaveInstanceState(Activity activity, Bundle outState) {} 
            @Override 
            public void onActivityDestroyed(Activity activity) {} 
        }); 
    } 
... 
}
```

`Config.collectLifecycleData(Activity activity`, `Map<String`, `Object> contextData)`를 사용하여 라이프사이클 호출로 추가 컨텍스트 데이터를 보내려면 해당 활동에 대해 `onResume` 메서드를 재정의하고 `collectLifecycleData`를 수동으로 호출한 후 `super.onResume()`을 호출해야 합니다.

```js
@Override 
protected void onResume() { 
    HashMap<String, Object> cdata = new HashMap<>(); 
    cdata.put("someKey", "someValue"); 
    Config.collectLifecycleData(this, cdata); 
  
    super.onResume(); 
}
```
