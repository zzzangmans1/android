# GPS 
## 1. manifest.xml 권한 추가

ACCESS_COARSE_LOCATION - 기기 위치 추정치를 약 1.6km 이내로 제공합니다.
ACCESS_FINE_LOCATION - 최대한 정확한 기기 위치 추정치를 제공합니다. 일반적으로 50m 이내이며 몇 미터 혹은 더 정확한 경우도 있습니다.

ACCESS_BACKGROUND_LOCATION - 백그라운드 위치 액세스 권한 필요하면 추가해줘야 한다.

``` xml
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
```


## 2. build.gradle(Module.app) 추가

```
 // 안드로이드 gps api 라이브러리
    implementation 'com.google.android.gms:play-services-location:20.0.0'
```
## 참고
