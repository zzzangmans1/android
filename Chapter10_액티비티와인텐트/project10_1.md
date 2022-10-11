``` xml
 <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">

        <Button
            android:id="@+id/btnNewActivity"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="새화면 열기" />
    </LinearLayout>
```

세컨드.xml
``` xml
<LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="#00FF00">
        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/btnReturn"
            android:text="돌아가기"></Button>
    </LinearLayout>
```

``` java
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        setTitle("간단 일기장");

        Button btnNewActivity = (Button)findViewById(R.id.btnNewActivity);
        btnNewActivity.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(getApplicationContext(), SecondActivity.class);
                startActivity(intent);
            }
        });
    }
}
```

``` java
// second view 액티비티
public class SecondActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.second);

        Button btnReturn = (Button) findViewById(R.id.btnReturn);
        btnReturn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                finish();
            }
        });
    }
}
```

메니페스트.xml에 아래 그림의 노란색 부분을 추가해주어야 한다.

![image](https://user-images.githubusercontent.com/52357235/195017863-faf5eeac-8c4c-489c-8de5-004fe3dc5ea0.png)



![image](https://user-images.githubusercontent.com/52357235/195017489-c0138d2a-27e7-4a34-818d-c96af713485d.png)

![image](https://user-images.githubusercontent.com/52357235/195017465-5af8e508-37f1-46da-90bb-00d147946e7e.png)
