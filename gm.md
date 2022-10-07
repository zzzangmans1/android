``` gradle 
// 구글맵 
    implementation 'com.google.android.gms:play-services-maps:18.1.0'
    implementation 'com.google.android.gms:play-services-location:20.0.0'

```

``` xml
// manifest.xml 
 // 구글 맵 등록
    <application
        <meta-data
            android:name="com.google.android.geo.API_KEY"
            android:value="AIzaSyCNcGbiElK0R3O0BGA-ZhPD4cjRQ7UWA3I" /> // API 키

```

``` xml
    <fragment
        android:id="@+id/googleMap"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        class="com.google.android.gms.maps.MapFragment" />
```

``` java

public class MainActivity extends AppCompatActivity implements OnMapReadyCallback {

    private FragmentManager fragmentManager;
    private MapFragment mapFragment;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // 구글 맵
        fragmentManager = getFragmentManager(); // fragmentmanager 객체 생성
        mapFragment = (MapFragment)fragmentManager.findFragmentById(R.id.googleMap); // 아이디 할당
        mapFragment.getMapAsync(this);  // 비동기식으로 구글맵 실행
    }
    
    // Fragment 객체가 설정되면 지도를 사용할 준비가 되면 실행되는 함수
    @Override
    public void onMapReady(@NonNull GoogleMap googleMap) {

        LatLng location = new LatLng(37.485284, 126.901451);// 위도 경도 변수
        MarkerOptions markerOptions = new MarkerOptions();  // 인스턴스 생성
        markerOptions.title("구로 디지털 단지");   // 핀 클릭했을 때 타이틀
        markerOptions.snippet("전철역");           // 핀 클릭했을 때 내용
        markerOptions.position(location);         // marker 찍을 위치
        googleMap.addMarker(markerOptions);         // 구글맵에 마커 표시

        googleMap.moveCamera(CameraUpdateFactory.newLatLngZoom(location, 16));  // 카메라 애니메이션 적용
    }
}

```
지정한 위도 경도가 주소에 표시됨

![image](https://user-images.githubusercontent.com/52357235/194442205-995a811f-f023-486e-ad0f-f5834e1de12e.png)
