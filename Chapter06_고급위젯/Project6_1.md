``` xml
<LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical">

            <Chronometer
                android:id="@+id/chronometer1"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:format="예약에 걸린 시간 : %s"
                android:gravity="center"
                android:textSize="20dp"></Chronometer>

            <Button
                android:id="@+id/btnStart"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:text="예약 시작"></Button>
        </LinearLayout>

        <RadioGroup
            android:layout_width="match_parent"
            android:layout_height="wrap_content">
            <RadioButton
                android:id="@+id/rdoCal"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="날짜 설정 (캘린더 뷰)"></RadioButton>

            <RadioButton
                android:id="@+id/rdoTime"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="시간 설정"></RadioButton>
        </RadioGroup>
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:layout_weight="1">
            <FrameLayout
                android:layout_width="match_parent"
                android:layout_height="match_parent">
                <CalendarView
                    android:id="@+id/calendarView1"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:showWeekNumber="false"></CalendarView>

                <TimePicker
                    android:id="@+id/timePicker1"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"></TimePicker>
            </FrameLayout>
        </LinearLayout>
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:background="#CCCCCC"
            android:orientation="horizontal">
            <Button
                android:id="@+id/btnEnd"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="예약완료"></Button>
            <TextView
                android:id="@+id/tvYear"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="0000"></TextView>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="년"></TextView>
            <TextView
                android:id="@+id/tvMonth"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="00"></TextView>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="월"></TextView>
            <TextView
                android:id="@+id/tvDay"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="00"></TextView>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="일"></TextView>
            <TextView
                android:id="@+id/tvHour"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="00"></TextView>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="시"></TextView>
            <TextView
                android:id="@+id/tvMinute"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="00"></TextView>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="분"></TextView>
        </LinearLayout>
    </LinearLayout>
```

``` java
public class MainActivity extends AppCompatActivity {

    // activity_main.xml에서 id를 부여한 12개 위젯에 대응하는 변수 선언
    Chronometer chrono;
    Button btnStart, btnEnd;
    RadioButton rdoCal, rdoTime;
    CalendarView calView;
    TimePicker tPicker;
    TextView tvYear, tvMonth, tvDay, tvHour, tvMinute;
    int selectYear, selectMonth, selectDay;

    @SuppressLint("ClickableViewAccessibility")
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        setTitle("시간 예약");
    
        // xml id 와 변수 연동
        btnStart = (Button) findViewById(R.id.btnStart);
        btnEnd = (Button)findViewById(R.id.btnEnd);

        chrono = (Chronometer) findViewById(R.id.chronometer1);

        rdoCal = (RadioButton) findViewById(R.id.rdoCal);
        rdoTime = (RadioButton) findViewById(R.id.rdoTime);

        tPicker = (TimePicker) findViewById(R.id.timePicker1);
        calView = (CalendarView) findViewById(R.id.calendarView1);

        tvYear = (TextView) findViewById(R.id.tvYear);
        tvMonth = (TextView)findViewById(R.id.tvMonth);
        tvDay   =(TextView) findViewById(R.id.tvDay);
        tvHour = (TextView)findViewById(R.id.tvHour);
        tvMinute = (TextView) findViewById(R.id.tvMinute);
    
        // 라디오 버튼을 눌러야 보이게 해야 하므로 숨김
        tPicker.setVisibility(View.INVISIBLE);
        calView.setVisibility(View.INVISIBLE);

        // 캘린더 버튼을 누르면 캘린더가 나오고
        rdoCal.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                tPicker.setVisibility(View.INVISIBLE);
                calView.setVisibility(View.VISIBLE);
            }
        });
        // 시간 버튼을 누르면 시간이 나오고
        rdoTime.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                tPicker.setVisibility(View.VISIBLE);
                calView.setVisibility(View.INVISIBLE);
            }
        });
        // 예약 시작 버튼을 누르면 크르노 타이머가 시작
        btnStart.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                chrono.setBase(SystemClock.elapsedRealtime());
                chrono.start();
                chrono.setTextColor(Color.RED);
            }
        });
        // 예약 완료 버튼을 누르면 크로노 타이머 종료
        btnEnd.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                chrono.stop();
                chrono.setTextColor(Color.BLUE);

                tvYear.setText(Integer.toString(selectYear));
                tvMonth.setText(Integer.toString(selectMonth));
                tvDay.setText(Integer.toString(selectDay));

                tvHour.setText(Integer.toString(tPicker.getCurrentHour()));
                tvMinute.setText(Integer.toString(tPicker.getCurrentMinute()));
            }
        });
        // 캘린더 선택 연 월 일 설정
        calView.setOnDateChangeListener(new CalendarView.OnDateChangeListener() {
            @Override
            public void onSelectedDayChange(@NonNull CalendarView calendarView, int i, int i1, int i2) {
                selectYear = i;
                selectMonth = i1+1;
                selectDay = i2;
            }
        });


    }
}

```

![image](https://user-images.githubusercontent.com/52357235/192483575-39a0c71f-c946-4f74-a7a8-4a8512f7fa3c.png)
