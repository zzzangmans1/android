``` xml
 <LinearLayout
      android:layout_width="match_parent"
      android:layout_height="match_parent"
      android:orientation="vertical">
      <LinearLayout
          android:layout_width="wrap_content"
          android:layout_height="wrap_content"
          android:orientation="horizontal">
          <EditText
              android:id="@+id/edtUrl"
              android:layout_weight="1"
              android:singleLine="true"
              android:hint="URL을 입력하세요"
              android:layout_width="match_parent"
              android:layout_height="wrap_content"></EditText>
          <Button
              android:id="@+id/btnGo"
              android:text="이동"
              android:layout_width="wrap_content"
              android:layout_height="wrap_content"></Button>
          <Button
              android:id="@+id/btnBack"
              android:text="이전"
              android:layout_width="wrap_content"
              android:layout_height="wrap_content"></Button>
      </LinearLayout>
      <WebView
          android:id="@+id/webView1"
          android:layout_width="match_parent"
          android:layout_height="match_parent">

      </WebView>
  </LinearLayout>
```

아래는 Mainfest.xml 파일 

``` xml
<uses-permission android:name="android.permission.INTERNET"></uses-permission>
    <application
        android:allowBackup="true"
        android:icon="@drawable/emo_im_cool"
        android:label="쿡북 웹브라우저"
        android:theme="@style/Theme.Project4_2"
        android:logo="@drawable/web"
        android:usesCleartextTraffic="true">
        <activity
            android:name=".MainActivity"
            android:label="간단 웹브라우저"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
```

``` java 
public class MainActivity extends AppCompatActivity{
    EditText edtUrl;
    Button btnGo, btnBack;
    WebView web;

    @SuppressLint("ClickableViewAccessibility")
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        edtUrl = (EditText) findViewById(R.id.edtUrl);
        btnGo = (Button)findViewById(R.id.btnGo);
        btnBack = (Button)findViewById(R.id.btnBack);

        web = (WebView) findViewById(R.id.webView1);

        web.setWebViewClient(new CookWebViewClient());

        WebSettings webSet = web.getSettings();
        webSet.setBuiltInZoomControls(true);
        webSet.setJavaScriptEnabled(true);

        btnGo.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                web.loadUrl(edtUrl.getText().toString());
            }
        });

        btnBack.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                web.goBack();
            }
        });
    }

    class CookWebViewClient extends WebViewClient{

        @Override
        public boolean shouldOverrideUrlLoading(WebView view, String url){
            return super.shouldOverrideUrlLoading(view, url);
        }
    }
}

```
