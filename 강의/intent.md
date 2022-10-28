mainActivity 자바
``` java
public class MainActivity extends AppCompatActivity {

    private Button btn_move;
    private EditText EdtInput;
    private String str;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        EdtInput = findViewById(R.id.EdtInput);
        btn_move = findViewById(R.id.btn_move);
        
        btn_move.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                str = EdtInput.getText().toString();        // EditText에 입력된 값을 str에 저장
                // 인텐트 사용
                // 첫 번째 인자는 자기 자신액티비티, 두번 째 인자는 넘어갈 액티비티.class
                Intent intent =  new Intent(MainActivity.this, SubActivity.class);
                intent.putExtra("str", str);        // sub액티비티로 별명 str  로 str에 있는 값 보낸다.
                startActivity(intent);  // 초기화한 인텐트를 실행 시켜 액티비티 이동
            }
        });
    }
}
```
mainActivity xml
``` xml
<EditText
        android:id="@+id/EdtInput"
        android:layout_width="200dp"
        android:layout_height="wrap_content" />
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="이동"
        android:id="@+id/btn_move" />
```

SubActivity java
``` java
public class SubActivity extends AppCompatActivity {

    private TextView TvSub;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_sub);

        TvSub = findViewById(R.id.TvSub);

        Intent intent = getIntent();           // 어디서 날라온 값이 있다면 여기 인텐트로 받겠다.
        String str = intent.getStringExtra("str");   // str 별명으로 온 문자열을 받겠다.
        TvSub.setText(str);
    }
}
```

SubActivity xml
``` xml
   <TextView
        android:id="@+id/TvSub"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="SUBACTIVITY"/>
```

<img width="475" alt="image" src="https://user-images.githubusercontent.com/52357235/198563234-3397cb55-3813-44ac-8bfb-849f8a8a2603.png">

<img width="474" alt="image" src="https://user-images.githubusercontent.com/52357235/198563340-40d78d32-bef9-464f-82d6-3b4d21dfac47.png">
