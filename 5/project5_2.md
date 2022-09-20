``` xml
<TableLayout
       android:layout_height="match_parent"
       android:layout_width="match_parent">
       <TableRow>
           <EditText
               android:id="@+id/Edit1"
               android:layout_span="5"
               android:hint="숫자1 입력"></EditText>
       </TableRow>

       <TableRow>
           <EditText
               android:id="@+id/Edit2"
               android:layout_span="5"
               android:hint="숫자2 입력"></EditText>
       </TableRow>

       <TableRow>
           <Button
               android:id="@+id/buttn0"
               android:text="0"></Button>
           <Button
               android:id="@+id/buttn1"
               android:text="1"></Button>
           <Button
               android:id="@+id/buttn2"
               android:text="2"></Button>
           <Button
               android:id="@+id/buttn3"
               android:text="3"></Button>
           <Button
               android:id="@+id/buttn4"
               android:text="4"></Button>
       </TableRow>

       <TableRow>
           <Button
               android:id="@+id/buttn5"
               android:text="5"></Button>
           <Button
               android:id="@+id/buttn6"
               android:text="6"></Button>
           <Button
               android:id="@+id/buttn7"
               android:text="7"></Button>
           <Button
               android:id="@+id/buttn8"
               android:text="8"></Button>
           <Button
               android:id="@+id/buttn9"
               android:text="9"></Button>
       </TableRow>

       <TableRow>
           <Button
               android:id="@+id/addbtn"
               android:layout_margin="5dp"
               android:layout_span="5"
               android:text="더하기"></Button>
       </TableRow>

       <TableRow>
           <Button
               android:id="@+id/subbtn"
               android:layout_margin="5dp"
               android:layout_span="5"
               android:text="빼기"></Button>
       </TableRow>

       <TableRow>
           <Button
               android:id="@+id/mulbtn"
               android:layout_margin="5dp"
               android:layout_span="5"
               android:text="곱하기"></Button>
       </TableRow>

       <TableRow>
           <Button
               android:id="@+id/divbtn"
               android:layout_margin="5dp"
               android:layout_span="5"
               android:text="나누기"></Button>
       </TableRow>

       <TableRow>
           <TextView
               android:id="@+id/restext"
               android:layout_margin="5dp"
               android:layout_span="5"
               android:text="계산결과 : "
               android:textColor="#FF0000"
               android:textSize="20dp"></TextView>
       </TableRow>
   </TableLayout>
```

``` java
public class MainActivity extends AppCompatActivity {

    EditText edit1, edit2;

    Button[] numButtons = new Button[10];

    Integer[] numBtnIDs = {R.id.buttn0, R.id.buttn1, R.id.buttn2, R.id.buttn3, R.id.buttn4, R.id.buttn5,
            R.id.buttn6, R.id.buttn7, R.id.buttn8, R.id.buttn9 };

    int i;

    String num1, num2;

    Integer res;

    Button addbtn, subbtn, divbtn, mulbtn;

    TextView restext;

    @SuppressLint("ClickableViewAccessibility")
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        setTitle("테이블 레이아웃 계산기");

        edit1 = (EditText) findViewById(R.id.Edit1);
        edit2 = (EditText) findViewById(R.id.Edit2);

        addbtn = (Button) findViewById(R.id.addbtn);
        subbtn = (Button) findViewById(R.id.subbtn);
        mulbtn = (Button) findViewById(R.id.mulbtn);
        divbtn = (Button) findViewById(R.id.divbtn);

        restext = (TextView) findViewById(R.id.restext);

        addbtn.setOnTouchListener(new View.OnTouchListener() {
            @Override
            public boolean onTouch(View view, MotionEvent motionEvent) {
                num1 = edit1.getText().toString();
                num2 = edit2.getText().toString();
                res = Integer.parseInt(num1) + Integer.parseInt(num2);
                restext.setText("계산결과 : " + res.toString());
                return false;
            }
        });

        subbtn.setOnTouchListener(new View.OnTouchListener() {
            @Override
            public boolean onTouch(View view, MotionEvent motionEvent) {
                num1 = edit1.getText().toString();
                num2 = edit2.getText().toString();
                res = Integer.parseInt(num1) - Integer.parseInt(num2);
                restext.setText("계산결과 : " + res.toString());
                return false;
            }
        });

        mulbtn.setOnTouchListener(new View.OnTouchListener() {
            @Override
            public boolean onTouch(View view, MotionEvent motionEvent) {
                num1 = edit1.getText().toString();
                num2 = edit2.getText().toString();
                res = Integer.parseInt(num1) * Integer.parseInt(num2);
                restext.setText("계산결과 : " + res.toString());
                return false;
            }
        });

        divbtn.setOnTouchListener(new View.OnTouchListener() {
            @Override
            public boolean onTouch(View view, MotionEvent motionEvent) {
                num1 = edit1.getText().toString();
                num2 = edit2.getText().toString();
                res = Integer.parseInt(num1) / Integer.parseInt(num2);
                restext.setText("계산결과 : " + res.toString());
                return false;
            }
        });

        for (i = 0; i <numBtnIDs.length;i++)
        {
            numButtons[i] = (Button) findViewById(numBtnIDs[i]);
        }

        for(i=0;i<numBtnIDs.length;i++)
        {
            final int index; // 꼭 필요함
            index = i;

            numButtons[index].setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View view) {
                    if(edit1.isFocused() == true)
                    {
                        num1 = edit1.getText().toString() + numButtons[index].getText().toString();
                        edit1.setText(num1);
                    }
                    else if(edit2.isFocused() == true){
                        num2 = edit2.getText().toString() + numButtons[index].getText().toString();
                        edit2.setText(num2);
                    }else
                    {
                        Toast.makeText(getApplicationContext(), "먼저 에디트텍스트를 선택하세요.",Toast.LENGTH_SHORT).show();;
                    }
                }
            });
        }
    }

}

```
![image](https://user-images.githubusercontent.com/52357235/191190477-733be3c9-a04f-4bb9-af84-2b6759bf50cf.png)
