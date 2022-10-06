SD카드를 사용할 수 있도록 퍼미션 및 application에 관련 속성 추가

``` xml
// manifest.xml
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
<application
        android:requestLegacyExternalStorage="true"
```

``` xml
// activity_main.xml
 <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">
        <LinearLayout
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:orientation="horizontal">
            <Button
                android:id="@+id/btnPrev"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:text="이전 그림">

            </Button>
            <TextView
                android:id="@+id/tvNumber"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:gravity="center"
                android:text="0/0"
                android:textSize="20dp" />
            <Button
                android:id="@+id/btnNext"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:text="다음 그림">
            </Button>
        </LinearLayout>
        <com.cookandroid.noactivity.myPictureView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/myPictureView1">
        </com.cookandroid.noactivity.myPictureView>
    </LinearLayout>
```

그림을 띄울 java 파일 생성

![image](https://user-images.githubusercontent.com/52357235/194203284-0eb0f589-ad21-46b4-b318-8094220fec79.png)

![image](https://user-images.githubusercontent.com/52357235/194203292-34cf38a7-c7de-4223-83c4-1f315fb79562.png)

``` java
// 이미지 띄울 자바
package com.cookandroid.noactivity;

import android.content.Context;
import android.graphics.Bitmap;
import android.graphics.BitmapFactory;
import android.graphics.Canvas;
import android.util.AttributeSet;
import android.view.View;

import androidx.annotation.Nullable;


public class myPictureView extends View {
    String imagePath = null;
    public myPictureView(Context context, @Nullable AttributeSet attrs){
        super(context, attrs);
    }

    @Override
    protected void onDraw(Canvas canvas){

        super.onDraw(canvas);
        if(imagePath != null){
            Bitmap bitmap = BitmapFactory.decodeFile(imagePath);
            canvas.drawBitmap(bitmap, 0, 0, null);
            bitmap.recycle();
        }
    }

}

```

그리고 이미지 뷰어에 띄울 이미지 사진 SD 카드에 업로드
![image](https://user-images.githubusercontent.com/52357235/194204406-6b0490ad-988c-467a-9731-1ebae848fff6.png)


![image](https://user-images.githubusercontent.com/52357235/194204374-cc36b831-66d5-470d-b538-927ed85d2849.png)

``` java
// main 
public class MainActivity extends AppCompatActivity {
    Button btnPrev, btnNext;
    myPictureView myPicture;
    TextView tvNumber;
    int curNum = 0;
    File[] imageFiles;
    String imageFname;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        setTitle("간단 이미지 뷰어");

        ActivityCompat.requestPermissions(this, new String[]{Manifest.permission.WRITE_EXTERNAL_STORAGE}, MODE_PRIVATE);

        btnPrev = (Button)  findViewById(R.id.btnPrev);
        btnNext = (Button) findViewById(R.id.btnNext);
        myPicture = (myPictureView) findViewById(R.id.myPictureView1);
        tvNumber = (TextView) findViewById(R.id.tvNumber);

        imageFiles = new File(Environment.getExternalStorageDirectory()
                .getAbsolutePath()+"/Pictures").listFiles(new FileFilter() {
            @Override
            public boolean accept(File file){
                return !file.getName().startsWith(".");
            }
        });
        imageFname = imageFiles[0].toString();
        myPicture.imagePath = imageFname;
        tvNumber.setText("1" + "/" + (imageFiles.length));
        btnPrev.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                if(curNum <= 0) {
                    Toast.makeText(getApplicationContext(), "첫 번째 그림입니다.", Toast.LENGTH_SHORT).show();
                }else
                {
                    curNum--;
                }
                imageFname = imageFiles[curNum].toString();
                myPicture.imagePath=imageFname;
                myPicture.invalidate();
                tvNumber.setText((curNum+1) + "/" + (imageFiles.length));
            }
        });
        btnNext.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                if(curNum >= imageFiles.length-1) {
                    Toast.makeText(getApplicationContext(), "마지막 그림입니다.", Toast.LENGTH_SHORT).show();
                }else
                {
                    curNum++;
                }
                imageFname = imageFiles[curNum].toString();
                myPicture.imagePath=imageFname;
                myPicture.invalidate();
                tvNumber.setText((curNum+1) + "/" + (imageFiles.length));
            }
        });
    }
}
```

![image](https://user-images.githubusercontent.com/52357235/194232813-36098df7-0b38-4065-bcae-930128826128.png)
