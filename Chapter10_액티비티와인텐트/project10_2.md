
``` xml
<LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="0dp"
            android:layout_weight="3"
            android:orientation="horizontal">
            <ImageView
                android:id="@+id/iv1"
                android:layout_margin="5dp"
                android:layout_weight="1"
                android:src="@drawable/pic1"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"></ImageView>
            <ImageView
                android:id="@+id/iv2"
                android:layout_margin="5dp"
                android:layout_weight="1"
                android:src="@drawable/pic2"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"></ImageView>
            <ImageView
                android:id="@+id/iv3"
                android:layout_margin="5dp"
                android:layout_weight="1"
                android:src="@drawable/pic3"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"></ImageView>
        </LinearLayout>
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="0dp"
            android:layout_weight="3"
            android:orientation="horizontal">
            <ImageView
                android:id="@+id/iv4"
                android:layout_margin="5dp"
                android:layout_weight="1"
                android:src="@drawable/pic4"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"></ImageView>
            <ImageView
                android:id="@+id/iv5"
                android:layout_margin="5dp"
                android:layout_weight="1"
                android:src="@drawable/pic5"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"></ImageView>
            <ImageView
                android:id="@+id/iv6"
                android:layout_margin="5dp"
                android:layout_weight="1"
                android:src="@drawable/pic6"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"></ImageView>
        </LinearLayout>
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="0dp"
            android:layout_weight="3"
            android:orientation="horizontal">
            <ImageView
                android:id="@+id/iv7"
                android:layout_margin="5dp"
                android:layout_weight="1"
                android:src="@drawable/pic7"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"></ImageView>
            <ImageView
                android:id="@+id/iv8"
                android:layout_margin="5dp"
                android:layout_weight="1"
                android:src="@drawable/pic8"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"></ImageView>
            <ImageView
                android:id="@+id/iv9"
                android:layout_margin="5dp"
                android:layout_weight="1"
                android:src="@drawable/pic9"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"></ImageView>
        </LinearLayout>

        <Button
            android:id="@+id/btnResult"
            android:height="0dp"
            android:layout_weight="1"
            android:text="투표 종료"
            android:layout_width="match_parent"
            android:layout_height="0dp"></Button>
    </LinearLayout>
```

result 액티비티
``` xml
<TableLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:gravity="center_vertical"
        android:stretchColumns="0">
        <TableRow>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:id="@+id/tv1"
                android:layout_gravity="center_vertical"
                android:text="그림1"
                android:textSize="15dp"></TextView>
            <RatingBar
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:id="@+id/rbar1"
                style="?android:attr/ratingBarStyleIndicator"
                android:layout_gravity="right"></RatingBar>
        </TableRow>
        <TableRow>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:id="@+id/tv2"
                android:layout_gravity="center_vertical"
                android:text="그림1"
                android:textSize="15dp"></TextView>
            <RatingBar

                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:id="@+id/rbar2"
                style="?android:attr/ratingBarStyleIndicator"
                android:layout_gravity="right"></RatingBar>
        </TableRow>
        <TableRow>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:id="@+id/tv3"
                android:layout_gravity="center_vertical"
                android:text="그림1"
                android:textSize="15dp"></TextView>
            <RatingBar
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:id="@+id/rbar3"
                style="?android:attr/ratingBarStyleIndicator"
                android:layout_gravity="right"></RatingBar>
        </TableRow>
        <TableRow>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:id="@+id/tv4"
                android:layout_gravity="center_vertical"
                android:text="그림1"
                android:textSize="15dp"></TextView>
            <RatingBar
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:id="@+id/rbar4"
                style="?android:attr/ratingBarStyleIndicator"
                android:layout_gravity="right"></RatingBar>
        </TableRow>
        <TableRow>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:id="@+id/tv5"
                android:layout_gravity="center_vertical"
                android:text="그림1"
                android:textSize="15dp"></TextView>
            <RatingBar
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:id="@+id/rbar5"
                style="?android:attr/ratingBarStyleIndicator"
                android:layout_gravity="right"></RatingBar>
        </TableRow>
        <TableRow>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:id="@+id/tv6"
                android:layout_gravity="center_vertical"
                android:text="그림1"
                android:textSize="15dp"></TextView>
            <RatingBar
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:id="@+id/rbar6"
                style="?android:attr/ratingBarStyleIndicator"
                android:layout_gravity="right"></RatingBar>
        </TableRow>
        <TableRow>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:id="@+id/tv7"
                android:layout_gravity="center_vertical"
                android:text="그림1"
                android:textSize="15dp"></TextView>
            <RatingBar
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:id="@+id/rbar7"
                style="?android:attr/ratingBarStyleIndicator"
                android:layout_gravity="right"></RatingBar>
        </TableRow>
        <TableRow>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:id="@+id/tv8"
                android:layout_gravity="center_vertical"
                android:text="그림1"
                android:textSize="15dp"></TextView>
            <RatingBar
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:id="@+id/rbar8"
                style="?android:attr/ratingBarStyleIndicator"
                android:layout_gravity="right"></RatingBar>
        </TableRow>
        <TableRow>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:id="@+id/tv9"
                android:layout_gravity="center_vertical"
                android:text="그림1"
                android:textSize="15dp"></TextView>
            <RatingBar
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:id="@+id/rbar9"
                style="?android:attr/ratingBarStyleIndicator"
                android:layout_gravity="right"></RatingBar>
        </TableRow>
        <TableRow>
            <Button
                android:id="@+id/btnReturn"
                android:layout_span="2"
                android:text="돌아가기"></Button>

        </TableRow>
    </TableLayout>
```

main 액티비티
``` java
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        setTitle("명화 선명도 투표");

        final int voteCount[] = new int[9];
        for(int i = 0; i< 9;i ++) voteCount[i] = 0;

        ImageView image[] = new ImageView[9];
        Integer imageId[] = {R.id.iv1, R.id.iv2, R.id.iv3, R.id.iv4, R.id.iv5, R.id.iv6, R.id.iv7, R.id.iv8, R.id.iv9};
        final String imgName[] = {"독서하는 소녀", "꽃장식 모자 소녀", "부채를 든 소녀", "이레느깡 단 베르양", "잠자는 소녀", "테라스의 두 자매", "피아노 레슨", "피아노 앞의 소녀들", "해변에서"};


        for(int i =0;i<imageId.length; i++){
            final int index;
            index  = i;
            image[index] = (ImageView) findViewById(imageId[index]);
            image[index].setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View view) {
                    voteCount[index]++;
                    Toast.makeText(getApplicationContext(), imgName[index] + " : 총 " + voteCount[index] + " 표", Toast.LENGTH_SHORT).show();
                }
            });
        }

        Button btnFinish = (Button) findViewById(R.id.btnResult);
        btnFinish.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(getApplicationContext(), ResultActivity.class);
                intent.putExtra("VoteCount",voteCount);
                intent.putExtra("ImageName", imgName);
                startActivity(intent);
            }
        });
    }
}
```

result 액티비티
``` java
public class ResultActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.result);
        setTitle("투표 결과");

        Intent intent = getIntent();
        int[] voteResult = intent.getIntArrayExtra("VoteCount");
        String[] imageName = intent.getStringArrayExtra("ImageName");

        TextView tv[] = new TextView[imageName.length];
        RatingBar rbar[] = new RatingBar[imageName.length];

        Integer tvID[] = {R.id.tv1, R.id.tv2, R.id.tv3, R.id.tv4, R.id.tv5,
        R.id.tv6, R.id.tv6, R.id.tv7, R.id.tv8, R.id.tv9};

        Integer rbarID[] = {R.id.rbar1, R.id.rbar2, R.id.rbar3, R.id.rbar4, R.id.rbar5,
        R.id.rbar6, R.id.rbar7, R.id.rbar8, R.id.rbar9};

        for(int i =0;i <voteResult.length; i++){
            tv[i]= (TextView)findViewById(tvID[i]);
            rbar[i] = (RatingBar) findViewById(rbarID[i]);
        }

        for(int i =0;i<voteResult.length;i++){
            tv[i].setText(imageName[i]);
            rbar[i].setRating((float)voteResult[i]);
        }

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
![image](https://user-images.githubusercontent.com/52357235/195058537-f9f2db3b-6abe-452e-848d-4d613475e7dd.png)

![image](https://user-images.githubusercontent.com/52357235/195058207-187bd289-597d-4b2d-b4fa-3910ef075115.png)

![image](https://user-images.githubusercontent.com/52357235/195058165-dd646308-ce92-4be3-859e-375cfd895ee3.png)
