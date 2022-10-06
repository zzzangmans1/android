``` xml
// main activity
<LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">


        <DatePicker
            android:datePickerMode="spinner"
            android:id="@+id/datePicker1"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:calendarViewShown="false" />

        <EditText
            android:layout_weight="1"
            android:id="@+id/edtDiary"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:background="#00ff00"
            android:lines="8" >
        </EditText>

        <Button
            android:id="@+id/btnWrite"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Button" />
    </LinearLayout>
```

``` java
public class MainActivity extends AppCompatActivity {
    DatePicker dp;
    EditText edtDiary;
    Button btnWrite;
    String fileName;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        setTitle("간단 일기장");

        dp = (DatePicker) findViewById(R.id.datePicker1);
        edtDiary = (EditText) findViewById(R.id.edtDiary);
        btnWrite = (Button) findViewById(R.id.btnWrite);

        Calendar cal = Calendar.getInstance();
        int cYear = cal.get(Calendar.YEAR);
        int cMonth = cal.get(Calendar.MONTH);
        int cDay = cal.get(Calendar.DAY_OF_MONTH);

        fileName = Integer.toString(cYear) + "_" + Integer.toString(cMonth+1)
                + "_" + Integer.toString(cDay) + ".txt";
        String str = readDiary(fileName);
        edtDiary.setText(str);

        dp.init(cYear, cMonth, cDay, new DatePicker.OnDateChangedListener() {
            @Override
            public void onDateChanged(DatePicker datePicker, int year, int monthOfYear, int dayOfMonth) {
                fileName = Integer.toString(year) + "_" +Integer.toString(monthOfYear) +"_"+ Integer.toString(dayOfMonth)+".txt";
                String str = readDiary(fileName);
                edtDiary.setText(str);
                btnWrite.setEnabled(true);
            }
        });


        btnWrite.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                try {
                    FileOutputStream outFs = openFileOutput(fileName, Context.MODE_PRIVATE);
                    String str = edtDiary.getText().toString();
                    outFs.write(str.getBytes());
                    outFs.close();
                    Toast.makeText(getApplicationContext(), fileName+" 이 저장됨", Toast.LENGTH_SHORT).show();
                }catch (IOException e){

                }
            }
        });
    }
    private String readDiary(String fileName) {
        String diaryStr = null;
        FileInputStream inFs;
        try {
            inFs = openFileInput(fileName);
            byte[] txt = new byte[500];
            inFs.read(txt);
            inFs.close();
            diaryStr = (new String(txt)).trim();
            btnWrite.setText("수정하기");
        }catch (IOException e){
            edtDiary.setHint("일기 없음");
            btnWrite.setText("새로 저장");
        }
        return diaryStr;
    }
}
```

Device File Explorer - data - data - 패키지 이름 - files 에 저장됩니다.

![image](https://user-images.githubusercontent.com/52357235/194247089-e3633fd8-e1ad-42b1-b648-14968fbb7544.png)


![image](https://user-images.githubusercontent.com/52357235/194245973-54424348-9592-405d-9a34-4a1da8d9eca9.png)

