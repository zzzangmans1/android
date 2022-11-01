``` java
public class MapsActivity extends FragmentActivity implements OnMapReadyCallback {

    private GoogleMap mMap;
    private ActivityMapsBinding binding;
    private String Provider;
    private double longitude;
    private double latitude;
    private double altitude;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);


        // 위치관리자 객체 생성
        final LocationManager lm = (LocationManager) getSystemService(Context.LOCATION_SERVICE);

        // 마지막으로 확인된 위치 정보 얻기
        /**
         * 마지막으로 확인된 위치 정보 얻기
         * Location은 다음과 같은 정보들을 제공합니다.
         * getAccuracy() : 정확도
         * getLatitude() : 위도
         * getLongitude() : 경도
         * getTime() : 생성된 시간(UTC)
         * getElapsedRealtimeNanos() : 생성된 시간
         */
        if ( Build.VERSION.SDK_INT >= 23 &&
                ContextCompat.checkSelfPermission( getApplicationContext(), android.Manifest.permission.ACCESS_FINE_LOCATION ) != PackageManager.PERMISSION_GRANTED ) {
            ActivityCompat.requestPermissions( this, new String[] {
                    android.Manifest.permission.ACCESS_FINE_LOCATION}, 0 );
        }

        else{
            Location location = lm.getLastKnownLocation(LocationManager.GPS_PROVIDER);

            if(location != null)
            {
                Provider = location.getProvider();
                longitude = location.getLongitude();
                latitude = location.getLatitude();
                altitude = location.getAltitude();
                Log.v("ONDU", "위도 : " + latitude + "경도 : "   + longitude);
            }
        }


        Log.v("ONDU", "맵을 시작하겠습니다");
        lm.requestLocationUpdates(LocationManager.GPS_PROVIDER, 1000, 1, gpsLocationListener);
        lm.requestLocationUpdates(LocationManager.NETWORK_PROVIDER, 1000, 1, gpsLocationListener);
        binding = ActivityMapsBinding.inflate(getLayoutInflater());
        setContentView(binding.getRoot());

        // Obtain the SupportMapFragment and get notified when the map is ready to be used.
        SupportMapFragment mapFragment = (SupportMapFragment) getSupportFragmentManager()
                .findFragmentById(R.id.map);
        mapFragment.getMapAsync(this);
    }

    /**
     * Manipulates the map once available.
     * This callback is triggered when the map is ready to be used.
     * This is where we can add markers or lines, add listeners or move the camera. In this case,
     * we just add a marker near Sydney, Australia.
     * If Google Play services is not installed on the device, the user will be prompted to install
     * it inside the SupportMapFragment. This method will only be triggered once the user has
     * installed Google Play services and returned to the app.
     */
    @Override
    public void onMapReady(GoogleMap googleMap) {
        Log.v("ONDU", "onMapReady Method start");
        mMap = googleMap;

        // Add a marker in Sydney and move the camera
        LatLng sydney = new LatLng(latitude, longitude);
        mMap.addMarker(new MarkerOptions().position(sydney).title("Marker in Sydney"));
        mMap.moveCamera(CameraUpdateFactory.newLatLng(sydney));
    }

    // 위치 리스너는 위치정보를 전달할 때 호출되므로 onLocationChanged()메소드 안에 위치정보를 처리를 작업을 구현해야 합니다.
    final LocationListener gpsLocationListener = new LocationListener() {
        @Override
        public void onLocationChanged(@NonNull Location location) {
            String Provider = location.getProvider();
            double longitude = location.getLongitude();
            double latitude = location.getLatitude();
            double altitude = location.getAltitude();
        } public void onStatusChanged(String provider, int status, Bundle extras){

        } public void onProviderEnabled(String provider){

        } public void onProviderDisabled(String provider){

        }

    };
}
```

activity_maps.xml
``` xml
<?xml version="1.0" encoding="utf-8"?>
<fragment xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:map="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/map"
    android:name="com.google.android.gms.maps.SupportMapFragment"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MapsActivity" />
```

2022.11.1 현재 구현정도
![image](https://user-images.githubusercontent.com/52357235/199233581-b744f53b-7786-4bdd-928b-d51e50974094.png)
