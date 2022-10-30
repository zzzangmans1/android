``` xml

    <WebView
        android:id="@+id/webView"
        android:layout_width="match_parent"
        android:layout_height="match_parent"/>
```

``` java
public class MainActivity extends AppCompatActivity {


    private WebView webView;
    private String url = "www.naver.com";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        webView = (WebView) findViewById(R.id.webView);

        webView.getSettings().setJavaScriptEnabled(true); // 자바스크립트를 허용할 것이냐.
        webView.loadUrl(url);                           // 특정 URL 로드
        webView.setWebChromeClient(new WebChromeClient());                   // 구글 크롬 세팅
        webView.setWebViewClient(new WebViewClientClass());

    }

    public boolean onKeyDown(int KeyCode, KeyEvent event){
        if((KeyCode == KeyEvent.KEYCODE_BACK)  && webView.canGoBack()) // 뒤로가기 버튼을 눌렀을 때
        {
            // 웹을 뒤로가게 해라
            webView.goBack();
            return  true;
        }
        return super.onKeyDown(KeyCode, event);
    }

    private class WebViewClientClass extends WebViewClient {
        @Override
        public boolean shouldOverrideUrlLoading(WebView view, String url){
            // 현재 페이지에 URL을 읽어올 수 있는 메소드
            view.loadUrl(url);
            return true;
        }
    }
}
```

Interent 권한부여 manifest xml파일에 권한 추가
``` xml
<uses-permission android:name="android.permission.INTERNET"/>
```


AndroidManifest.xml의 application 태그에android:usesCleartextTraffic="true"

<img width="355" alt="image" src="https://user-images.githubusercontent.com/52357235/198862339-99022b79-ab9e-4cae-bd5c-98cd920555a7.png">
