``` xml

    <EditText
        android:id="@+id/edt_save"
        android:layout_width="100dp"
        android:layout_height="wrap_content"/>

```

``` java
public class MainActivity extends AppCompatActivity {

    EditText edt_save;
    String shared = "file";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        edt_save = (EditText) findViewById(R.id.edt_save);

        // sharedPreferences 선언
        SharedPreferences sharedPreferences = getSharedPreferences(shared, 0);
        String value = sharedPreferences.getString("hong", "");

        edt_save.setText(value);
    }

    // 앱을 나갔을 때 실행
    protected void OnDestroy(){
        super.onDestroy();

        SharedPreferences sharedPreferences = getSharedPreferences(shared, 0);
        SharedPreferences.Editor editor = sharedPreferences.edit(); // 에디터 생성
        String value = edt_save.getText().toString();               // edttext에 값을 가져오기
        editor.putString("hong", value);                        // value 값을 editor에 넣는다.
        editor.commit();                                           // 실질적인 저장
    }

```

어플을 실행했을 때 SharedPreferences 선언 하고 저장되어 있는 값의 파일이름을 적고 내용을 불러오고 EditText에 설정

앱을 나갔을 때 SharedPreferences와 Editor를 선언하고 EditText에 있는 값을 Value에 값을 넣고 editor에 그 값을 삽입하고 저장한다.

<img width="471" alt="image" src="https://user-images.githubusercontent.com/52357235/198859558-974a790c-754a-40fa-a5a0-3998e8b5664b.png">
