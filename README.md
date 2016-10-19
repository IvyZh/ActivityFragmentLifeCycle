# ActivityFragmentLifeCycle
Activity和Fragment的生命周期


![](http://img.blog.csdn.net/20140719225005356?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbG1qNjIzNTY1Nzkx/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)



* fragment代码

Code：

	public class MyFragment extends Fragment {
	
	    String TAG = "MyFragment";
	
	    @Override
	    public void onAttach(Context context) {
	        super.onAttach(context);
	
	        Log.v(TAG, "onAttach");
	    }
	
	    @Override
	    public void onCreate(@Nullable Bundle savedInstanceState) {
	        super.onCreate(savedInstanceState);
	        Log.v(TAG, "onCreate");
	    }
	
	    @Nullable
	    @Override
	    public View onCreateView(LayoutInflater inflater, @Nullable ViewGroup container, @Nullable Bundle savedInstanceState) {
	        Log.v(TAG, "onCreateView");
	        View view = inflater.inflate(R.layout.fragment_content, container, false);
	        return view;
	    }
	
	    @Override
	    public void onActivityCreated(@Nullable Bundle savedInstanceState) {
	        super.onActivityCreated(savedInstanceState);
	        Log.v(TAG, "onActivityCreated");
	    }
	
	    @Override
	    public void onStart() {
	        super.onStart();
	        Log.v(TAG, "onStart");
	    }
	
	    @Override
	    public void onResume() {
	        super.onResume();
	        Log.v(TAG, "onResume");
	    }
	
	    @Override
	    public void onPause() {
	        super.onPause();
	        Log.v(TAG, "onPause");
	    }
	
	    @Override
	    public void onStop() {
	        super.onStop();
	        Log.v(TAG, "onStop");
	    }
	
	    @Override
	    public void onDestroyView() {
	        super.onDestroyView();
	        Log.v(TAG, "onDestroyView");
	    }
	
	
	    @Override
	    public void onDestroy() {
	        super.onDestroy();
	        Log.v(TAG, "onDestroy");
	    }
	
	
	    @Override
	    public void onDetach() {
	        super.onDetach();
	        Log.v(TAG, "onDetach");
	    }
	}



日志：

	10-19 10:20:13.892 21119-21119/com.ivy.activityfragmentlifecycle V/MyFragment: onAttach
	10-19 10:20:13.892 21119-21119/com.ivy.activityfragmentlifecycle V/MyFragment: onCreate
	10-19 10:20:13.908 21119-21119/com.ivy.activityfragmentlifecycle V/MyFragment: onCreateView
	10-19 10:20:13.908 21119-21119/com.ivy.activityfragmentlifecycle V/MyFragment: onActivityCreated
	10-19 10:20:13.908 21119-21119/com.ivy.activityfragmentlifecycle V/MyFragment: onStart
	10-19 10:20:13.908 21119-21119/com.ivy.activityfragmentlifecycle V/MyFragment: onResume
	10-19 10:20:26.632 21119-21119/com.ivy.activityfragmentlifecycle V/MyFragment: onPause
	10-19 10:20:27.092 21119-21119/com.ivy.activityfragmentlifecycle V/MyFragment: onStop
	10-19 10:20:27.092 21119-21119/com.ivy.activityfragmentlifecycle V/MyFragment: onDestroyView
	10-19 10:20:27.092 21119-21119/com.ivy.activityfragmentlifecycle V/MyFragment: onDestroy
	10-19 10:20:27.092 21119-21119/com.ivy.activityfragmentlifecycle V/MyFragment: onDetach



* main函数代码

Code：


	public class MainActivity extends AppCompatActivity {
	
	    String TAG = "MainActivity";
	
	    @Override
	    protected void onCreate(Bundle savedInstanceState) {
	        super.onCreate(savedInstanceState);
	        Log.v(TAG, "onStart");
	        setContentView(R.layout.activity_main);
	        // 设置默认的Fragment
	        setDefaultFragment();
	    }
	
	    private void setDefaultFragment() {
	        android.support.v4.app.FragmentManager fm = getSupportFragmentManager();
	        FragmentTransaction ft = fm.beginTransaction();
	        Fragment fragment = new MyFragment();
	        ft.replace(R.id.id_content, fragment);
	        ft.commit();
	    }
	
	
	
	    @Override
	    public void onStart() {
	        super.onStart();
	        Log.v(TAG, "onStart");
	    }
	
	    @Override
	    public void onResume() {
	        super.onResume();
	        Log.v(TAG, "onResume");
	    }
	
	    @Override
	    public void onPause() {
	        super.onPause();
	        Log.v(TAG, "onPause");
	    }
	
	    @Override
	    public void onStop() {
	        super.onStop();
	        Log.v(TAG, "onStop");
	    }
	
	
	    @Override
	    public void onDestroy() {
	        super.onDestroy();
	        Log.v(TAG, "onDestroy");
	    }
	
	
	}

日志：

	10-19 10:23:35.008 29482-29482/com.ivy.activityfragmentlifecycle V/MainActivity: onCreate
	10-19 10:23:35.132 29482-29482/com.ivy.activityfragmentlifecycle V/MainActivity: onStart
	10-19 10:23:35.132 29482-29482/com.ivy.activityfragmentlifecycle V/MainActivity: onResume
	10-19 10:23:38.080 29482-29482/com.ivy.activityfragmentlifecycle V/MainActivity: onPause
	10-19 10:23:38.660 29482-29482/com.ivy.activityfragmentlifecycle V/MainActivity: onStop
	10-19 10:23:38.660 29482-29482/com.ivy.activityfragmentlifecycle V/MainActivity: onDestroy


> 同时打开日志：

	10-19 10:24:06.052 29482-29482/com.ivy.activityfragmentlifecycle V/MainActivity: onCreate
	10-19 10:24:06.088 29482-29482/com.ivy.activityfragmentlifecycle V/MyFragment: onAttach
	10-19 10:24:06.092 29482-29482/com.ivy.activityfragmentlifecycle V/MyFragment: onCreate
	10-19 10:24:06.092 29482-29482/com.ivy.activityfragmentlifecycle V/MyFragment: onCreateView
	10-19 10:24:06.096 29482-29482/com.ivy.activityfragmentlifecycle V/MyFragment: onActivityCreated
	10-19 10:24:06.104 29482-29482/com.ivy.activityfragmentlifecycle V/MyFragment: onStart
	10-19 10:24:06.104 29482-29482/com.ivy.activityfragmentlifecycle V/MainActivity: onStart
	10-19 10:24:06.104 29482-29482/com.ivy.activityfragmentlifecycle V/MainActivity: onResume
	10-19 10:24:06.104 29482-29482/com.ivy.activityfragmentlifecycle V/MyFragment: onResume
	
	10-19 10:24:30.708 29482-29482/com.ivy.activityfragmentlifecycle V/MyFragment: onPause
	10-19 10:24:30.708 29482-29482/com.ivy.activityfragmentlifecycle V/MainActivity: onPause
	10-19 10:24:31.228 29482-29482/com.ivy.activityfragmentlifecycle V/MyFragment: onStop
	10-19 10:24:31.228 29482-29482/com.ivy.activityfragmentlifecycle V/MainActivity: onStop
	10-19 10:24:31.228 29482-29482/com.ivy.activityfragmentlifecycle V/MyFragment: onDestroyView
	10-19 10:24:31.228 29482-29482/com.ivy.activityfragmentlifecycle V/MyFragment: onDestroy
	10-19 10:24:31.228 29482-29482/com.ivy.activityfragmentlifecycle V/MyFragment: onDetach
	10-19 10:24:31.228 29482-29482/com.ivy.activityfragmentlifecycle V/MainActivity: onDestroy
