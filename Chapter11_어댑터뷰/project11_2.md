


``` java
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        setTitle("갤러리 영화 포스터");
        Gallery gallery = (Gallery) findViewById(R.id.gallery1);

        MyGalleryAdapter galAdapter = new MyGalleryAdapter(this);
        gallery.setAdapter(galAdapter);
    }

    public class MyGalleryAdapter extends BaseAdapter{
        Context context;
        Integer[] PosterID = {R.drawable.mov11, R.drawable.mov12,
        R.drawable.mov13, R.drawable.mov14, R.drawable.mov15,
        R.drawable.mov16, R.drawable.mov17, R.drawable.mov18,
        R.drawable.mov19, R.drawable.mov20};

        public MyGalleryAdapter(Context c){
            context = c;
        }

        @Override
        public int getCount() {
            return PosterID.length;
        }

        @Override
        public Object getItem(int i) {
            return null;
        }

        @Override
        public long getItemId(int i) {
            return 0;
        }

        @SuppressLint("ClickableViewAccessibility")
        @Override
        public View getView(int position, View view, ViewGroup viewGroup) {
            ImageView imageView = new ImageView(context);
            imageView.setLayoutParams(new Gallery.LayoutParams(200, 300));
            imageView.setScaleType(ImageView.ScaleType.FIT_CENTER);
            imageView.setPadding(5,5,5,5);

            imageView.setImageResource(PosterID[position]);

            final int pos = position;
            imageView.setOnTouchListener(new View.OnTouchListener()
            {
                @Override
                public boolean onTouch(View view, MotionEvent motionEvent) {
                    ImageView ivPoster = (ImageView) findViewById(R.id.ivPoster);
                    ivPoster.setScaleType(ImageView.ScaleType.FIT_CENTER);
                    ivPoster.setImageResource(PosterID[pos]);
                    return false;
                }
            });
            return imageView;
        }
    }
}
```

``` xml
<LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">

        <Gallery
            android:id="@+id/gallery1"
            android:layout_width="match_parent"
            android:layout_height="87dp"
            android:spacing="5dp" />

        <ImageView
            android:id="@+id/ivPoster"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:padding="20dp" />
    </LinearLayout>
```

<img width="488" alt="image" src="https://user-images.githubusercontent.com/52357235/197740264-12e49518-14c0-440a-8723-1b82a9712d62.png">
