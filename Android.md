#Android开发笔记
----------------------
##工程目录结构
- src
- gen 自动生成，给资源文件唯一编码
- asset 原生资源文件，不经常被用户修改的文件，如：音频，视频
- bin .apk文件
- lib
- res 资源文件
	- drawable-xxdpi 图片资源 ，排序为`hdpi < `
	- layout 
	- menu 
	- values 字符资源文件（用于国际化）
- AndroidManifest 清单文件
	- 包名
	- apk版本
	- icon,label,theme

##资源的使用
1. 程序访问通过R.java文件
2. xml引用通过 `@<资源对应的内部类的类名>/<资源名>`；当使用标识符时（即分配一个唯一的标识），`@+id/<标识符代号>`，在xml中引用这个资源可以通过`@id/<标识符代号>`，在java代码中通过Activity的findViewById()方法获取；

##Android常用单位
- px（像素）：
- dip|dp：屏幕密度
- sp：描述字体
- in（英寸）：
- mm（毫米）
- pt（磅）
##Activity
- activity的组件
	- 布局管理器： View --> ViewGroup
		- 线性布局（LinearLayout），水平或者垂直一个一个排列，超过部分不显示
			- 表格布局（TableLayout），继承LinearLayout，有点类似html中表格
		- 帧布局（FrameLayout），实现叠放效果
			- ViewAnimator及其子类，可以重叠，在View切换时表现出动画效果
				- ViewSwitcher
					- ImageSwitcher(图片切换器)
					- TextSwitcher（文本切换器）
				- ViewFlipper
		- 相对布局（RelativeLayout）,实现相对父容器或兄弟容器的位置
		- 网格布局（GridLayout）需要4.0以上，与TableLayout类型，但它可以跨多行和多列
		- 绝对布局，自己控制x，y坐标
	- UI组件：
		- TextView
			- Button，继承自TextView，
				- RadioButton（单选按钮），通常与RadioGroup组合使用
				- CheckBox（复选框）都多了一个`android:checked`属性
				- ToggleButton（状态开关按钮）
				- Switch（开关）
				- DigitalClock(数字时钟)
				- Chronomeer（计时器）
		- EditView
		- 9Patch图片制作工具（指定图片中的某些部位不能缩放）
		- AnalogClock（表盘的时钟），继承View
		- ImageView 图片容器
			- ImageButton 图片按钮
				- ZoomButton(可放大缩小)，ZoomControls为一个放大缩小的按钮
			- QuickContactBadge（关联联系人），关联email，电话或者是特定的uri
		- ViewGroup（都是列表的容器，列表项一般用Adapter(接口)）
			- AdapterView(Abstract类)
				- AbsListView
					- ListView (垂直列表显示所有项)
				- AbsSpinnerView
				- AdapterViewAnimator
				- ......
		- ProgressBar及其子类
			- ...
		- SeekBar(拖动条)
		- RatingBar（星级评分条）
		- 杂项
			- Toast（提示框）
			- CalendarView（日历视图）
			- DatePicker（日期选择器）
			- TimePicker（时间选择器）
			- NumberPicker（数值选择器）
			- SearchView（搜索框）
			- TabHost（选项卡）
			- ScrollView（滚动视图）
			- Notification（手机状态栏的通知）
		- 对话框
			- AlertDialog
			- ProgressDialog（进度对话框）
			- DatePickerDialog（日期选择对话框）
			- TimePickerDialog（时间选择对话框）
		- 菜单

- activity的生命周期：
![Activity的生命周期](http://wear.techbrood.com/images/activity_lifecycle.png)
1. onCreate();



=======================

##Android事件处理
1. 事件监听（委托式）
	- 流程
		获取组件对象（事件源）----> 实现事件监听器（xxxListener）----> 调用setXxxListener()，将事件注册给普通组件 
	- 常用的监听器接口
		- View
			- View.OnClickListener
			- View.OnCreateContextMenuListener
			- View.OnFocusChangeListener
			- View.OnKeyListener
	- 几种实现监听器的方式
		- 内部类
		- 匿名内部类（推荐）
		- 外部类
		- Activity直接继承相应的监听器接口
		- 直接在界面布局文件中添加相应的事件监听属性，如：`android:onClick="testClick"`,在相对应的Activity中定义一个对应的方法`void testClick(View source)`;
2. 基于回调的事件处理
	- 组件自己充当监视器，自己实现相应的监听方法，返回Boolean值；如果返回为false，则会激活父一级的组件的同名方法，以此类推，一层一层往上传播，遇到返回值为true，则停止传播；

3. Configuration类
	- 手机设备上的配置信息
	- 获取方式：`Configuration cfg = getResources().getConfiguration()`
	- 监听系统设置更改，可重写`Activity`的`onConfigurationChanged(Configuration newConfig)`方法,配合在layout文件中加上`android:configChanges`属性
	
4. Handle（Android的UI操作非线程安全，多个线程并发操作UI组件，存在安全问题）
	- void handleMessage(Message msg)
	- final boolean hasMessages(int what)
	- final boolean hasMessages(int what, Object obj)
	- sendEmptyMessage(int what)
	- final boolean sendEmptyMessageDelayed()
	- ......
	
	- 与Handle一起工作的3个组件
		- Message：Handle接收和处理的消息对象
		- Looper：每个线程只能拥有一个Looper
		- MessageQueue：消息队列
5. 异步任务
	- 实现`AsyncTask<>`抽象类，重写几个方法； 


##Activity和Fragment

####fragment......

####配置Activity（必须显示的添加）
- 在`<application.../>`元素中添加`<activity.../>`子元素
	- 常用属性
		- name：类名
		- icon：图标
		- lable：标签
		- exported：是否可被其它应用调用
		- launchMode：加载模式（standard，singleTop，singleTask，singleInstance）
- 启动关闭`Activity`
	- 启动
		- `startActivity(Intent intent)`
		- `startActivityForResult(Intent intent, int requestCode)`，以指定的请求码启动，并且程序将会等到新启动的Activity的结果（重写`onActivityResult()`）
	- 关闭
		- finish()   //结束当前activity
		- finishActivity(int requestCode)  //结束指定的activity	
- 使用`Bundle`在`Activity`之间交换数据
	- `activity`之间的数据通信通过`Intent`来携带，以下是几个常用的需重载的方法
		- `putExtras(Bundle data)`，向Intent中放入需要携带的数据包
		- `Bundle getExtras()`，取出Intent中携带的数据包
		- `putExtra(String name, XXX value)`，以键值对形式向Intent中放入数据包，自动转换成Bundle格式
		- getXxxExtra(String name)，按key取出指定类型的数据
	- `Bundle`就是一个简单的数据携带包
		- `putXxx(String key, Xxx data)`，向Bundle放入各种类型的数据
		- `putSerializable(String key, Serializable data)`，向Bundle中放入一个可序列化的对象
		- `getXxx(String key)`
		- `getSerializable(String key, Serializable data)`
- `getIntent()`获取启动该Result的Intent
- Activity的几种基本状态
	- 活动状态：位于前台，可见，可获得焦点
	- 暂停状态：位于前台，可见，不可获得焦点
	- 停止状态：不可见，失去焦点
	- 销毁状态：结束
- Activity的加载模式
	- standard：默认的加载模式
	- singleTop：开将要启动的activity是否位于栈顶，如果是，则使用同一份，如果不是活着没有，则创建一个新的位于栈顶
	- singleTask：如果存在将要启动的activity，则清空将要启动的activity 上的所有，让将要启动的activity处于栈顶状态
	- singleInstance：
- Fragment：
	- 依赖Activity而存在
	- getActivity()获取所在的activity
	- 可在Activity运行的过程中进行动态的添加，删除，替换Fragment
		- FragmentManager的add(),remove(),replace();
	- ......


##Intent和IntentFilter通信详解
####Intent
	启动不同组件的方法：
	- startActivity(Intent intent)
	- startActivityForResult(Intent intent, int requestCode)
	
	- ComponentName startService(Intent service)
	- boolean bindService(Intent service, ServiceConnection conn, int flags)
	
	- sendBroadcast(Intent intent)
	- sendBroadcast(Intent intent, String receiverPermission)
	- sendOrderedBroadcast(Intent intent, String receiverPermission, BroadcastReceiver resultReceiver, Handle scheduler, int initialCode, String initialData, Bundle initialExtras)
	- sendOrderedBroadcast(Intent intent, String receiverPermission)
	- sendStickyBroadcast(intent intent)
	- sendStickyOrderedBroadcast(Intent intent, BroadcastReceiver resultReceiver, Handle schedule, int initialCode, String initialData, Bundle initialExtras)

- Intent的属性
	- 明确将启动那个应用组件
		- Component(明确指定启动那个组件) 
	- 不确定将启动那个组件，只是给出一个范围，可以配置启动其他的应用程序，如打电话之类的，在`Manifest.xml`文件中配置`<intent-filter>`设置启动该`activity`的门槛，`action`-->启动的动作，`category`-->限制条件，`type`-->接收的数据的格式
		- Action
		- Category
		- Data
		- Type
		- Extra 传递数据
		- Flag （intent.addFlag()）
			- add
	- 在Java代码中启动不确定的组件，通过intent提供的方法
		- intent.setDataAndType(Uri.parse("http://slfsal","image/*"))
		- intent.setData(Uri.parse(""));
		- intent.setAction()
		- intent.addCategory()
	- 使用Intent创建Tab页面




##数据存储与IO
- SharedPreferences存储
	1. SharedPreferences是一个接口，需通过`getSharedPreferences(String name, int mode)`方法来获取，参数 mode支持一下三个值：
		- Context.MODE_PRIVATE  //只能被本应用程序读写
		- Context.MODE_WORLD_READABLE  //能被其它应用程序读，不能写
		- Context.MODE_WORLD_WRITEABLE  //能被其它应用程序读写
		
	2. SharedPreferences(键值对形式的保存，主要用于保存配置信息)
		- boolean contains(String key)
		- abstract Map<String, ?> getAll
		- boolean getXxx(String key, Xxx defValue) //获取指定的key对应的value值，如果不存在，则返回`defValue`值,Xxx可以是boolean、float、int、long、String这几种基本类型中的一种
		
		- 写入数据是通过`SharedPreferences`的内部类`Editor`来处理的，通过`SharedPreferences`的`edit()`方法可获得`Editor`对象；
			- SharedPreferences.Editor clear()  //清空所有数据
			- SharedPreferences.Editor putXxx(String key, Xxx value);  //Xxx可以是基本数据类型中的一种
			- SharedPreferences.Editor remove(String key)  //移除某个key对应的value值
		- 编辑完了以后需要提交  boolean commit();
	3. 读取其它应用的数据
		- 获得相应的程序的上下文Context,通过`createPackageContext()`

- File存储
	- 流相关的知识......
- Sqlite存储
1. 常用类
	- SQLiteDatabase (操作数据库的方法集)
	- SQLiteOpenHelper (创建数据库和打开数据库等操作)





##ContentProvider(不同应用间数据共享的方法)
- 步骤
	1. 继承ContentProvider，重写几个方法
	2. 在Manifest.xml中注册该provider
		- 属性：
			- android:name=".FirstProvider"  //类名
			- android:authorities=""
			- android:expoted="true"  //是否允许其它应用调用
- URI
	1. 组成
		- 协议：`content://`
		- authority(类似于域名)：`com.i8i8i8.android.shareprovider`
		- words（资源部分，类似于path）：如`/id/2`
	2. 转换
		- Uri uri = Uri.parse(uri字符串);

- 调用其它应用的（ContentResolver）,通过`Context`的`getContextResolver()`方法获得，通过对应的ContextResolver中的方法进行操作
- 常用工具类
	- UriMatcher(用于匹配一个uri是否可用)
	- ContentUris(组合或解析Uri)
	- ContentObserver（监听uri资源的改变）
	

##Service,BroadcastReceiver
1. 步骤
	- 继承Service
	- 配置xml
2. 启动Service
	- startService()  //启动，启动者与被启动者没有关联
	- bindService()  //关联在一起，启动者退出，Service也退出
	- unbindService()  //解除绑定
3. 停止Service
	- stopService()
4. 每次启动Service一定会调用onStartCommand()方法，只有Service第一次启动时才会调用onCreate()方法
5. 实现通信需要先绑定相应的Service，通过`bindService()`
6. IntentService会自动实现多线程执行任务
7. AIDL Service（跨进程通信）......
8. TelephonyManager tManager = (TelephonyManager) getSystemService(Context.TELPHONY_SERVICE)  //获取手机通话，电话，网络的状态的信息
9. 短信发送相关：SmsManager sms = SmsManager.getDefault(); //获取Sms实例
10. 音频管理相关 ：AudioManager audio = (AudioManager) getSystemService(Service.AUDIO_SERVICE)
11. 震动：Vibrator vibrator = (Vibrator) getSystemService(Service.VIBRATOR_SERVICE)
12. 闹钟：AlarmingManager

##BroadcastReceiver
1. 实现Broadcast的onReceive()方法，10内没完成就提示未响应，通过配置文件manifest.xml配置出发onReceive()方法的条件
2. 发送广播：sendBroadcast(Intent intent)
3. 有序广播：根据优先级顺序接收到广播，优先级高的可以直接终止掉广播，可以往广播里加东西让后面的接收者收到；通过`android:priority=""`设置优先级（-1000 ~ 1000）
	- sendOrderedBroadcast()  //发送有序广播
	- setResultExtras(Bundle bundle) //设置下一个接收者可以接收到的信息
	- getResultExtras(true)  //获取上一个广播接收者存入的信息
	- abortBroadcast()  //取消广播的继续传播































































