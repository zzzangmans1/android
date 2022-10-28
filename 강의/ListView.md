``` java
public class MainActivity extends AppCompatActivity {

    private ListView LstView;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        LstView = (ListView) findViewById(R.id.Lstview);

        // ListView 에 데이터를 넣으려면 List를 만들어야 한다.
        List<String> data = new ArrayList<>();          // String형으로 받겠다.

        // 리스트와 리스트뷰 연결하는 어뎁터 생성
        // this = 현재 액티비티 해당, 디자인 가져다 쓰는 인자, 넣을 리스트
        ArrayAdapter<String> adapter = new ArrayAdapter<>(this, android.R.layout.simple_list_item_1, data);
        LstView.setAdapter(adapter);        // 리스트뷰에 리스트 랑 어뎁터로 연결

        data.add("이원주");
        data.add("정쩡이");
        data.add("사랑이");
        adapter.notifyDataSetChanged();     // 위 데이터를 넣은 리스트를 저장하겠다.
    }
}
```

``` xml
    <ListView
        android:id="@+id/Lstview"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

```

<img width="466" alt="image" src="https://user-images.githubusercontent.com/52357235/198579297-f50fdad6-2af6-42ce-a22c-22c32ba3211b.png">
