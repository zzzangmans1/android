``` java
public class MainActivity extends AppCompatActivity {

    private DrawerLayout drawerLayout;
    private View drawerview;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        drawerLayout = (DrawerLayout) findViewById(R.id.drawer_layout);
        drawerview = (View) findViewById(R.id.drawer);

        Button btn_open = (Button) findViewById(R.id.btn_open);
        btn_open.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                drawerLayout.openDrawer(drawerview);    // 메뉴 생성
            }
        });

        Button btn_close = (Button)findViewById(R.id.btn_close);
        btn_close.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                drawerLayout.closeDrawers();            // 메뉴 종료
            }
        });

        drawerLayout.setDrawerListener(lisnter);
        drawerview.setOnTouchListener(new View.OnTouchListener() {
            @Override
            public boolean onTouch(View view, MotionEvent motionEvent) {

                return true;
            }
        });

    }
    // 메뉴 리스너
    DrawerLayout.DrawerListener lisnter = new DrawerLayout.DrawerListener() {
        @Override
        public void onDrawerSlide(@NonNull View drawerView, float slideOffset) {
            // 메뉴가 슬라이드 되었을 때
        }

        @Override
        public void onDrawerOpened(@NonNull View drawerView) {
            // 메뉴가 open되었을 때
        }

        @Override
        public void onDrawerClosed(@NonNull View drawerView) {
            // 메뉴가 close되었을 때
        }

        @Override
        public void onDrawerStateChanged(int newState) {
            // 메뉴가 State가 Change 되었을 때
        }
    };
}
```

메인 xml

``` xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.drawerlayout.widget.DrawerLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:id="@+id/drawer_layout"
    tools:context=".MainActivity">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content">

        <Button
            android:id="@+id/btn_open"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="열려라 참께"/>

    </LinearLayout>

    <include layout="@layout/activity_drawer"/>



</androidx.drawerlayout.widget.DrawerLayout>
```

메뉴 xml
``` xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="240dp"
    android:layout_height="match_parent"
    android:layout_gravity="start"
    android:background="#00FF00"
    android:id="@+id/drawer"
    android:orientation="vertical">
    
    <Button
        android:id="@+id/btn_close"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="10dp"
        android:text="메뉴닫기"/>

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:text="이원주메뉴"/>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:layout_margin="10dp"
        android:background="#0000FF">

        <TextView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:gravity="center"
            android:text="텍스트 메뉴"/>
    </LinearLayout>

</LinearLayout>
```
