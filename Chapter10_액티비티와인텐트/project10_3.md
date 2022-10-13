``` xml
<LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">

        <Button
            android:id="@+id/btnDial"
            android:text="전화 걸기"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"></Button>

        <Button
            android:id="@+id/btnFinish"
            android:text="전화 끊기"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"></Button>
    </LinearLayout>
```

``` java
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        setTitle("액티비티 테스트 예제");

        android.util.Log.i("액티비티 테스트", "onCreate()");

        Button btnDial = (Button) findViewById(R.id.btnDial);
        btnDial.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
            }
        });

        Button btnFinish = (Button) findViewById(R.id.btnFinish);
        btnFinish.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                finish();
            }
        });

    }
    @Override
    protected void onStart(){

        super.onStart();
        android.util.Log.i("액티비티 테스트", "onStart()");
    }
    @Override
    protected void onDestroy(){

        super.onDestroy();
        android.util.Log.i("액티비티 테스트", "onDestroy()");
    }
}
```

