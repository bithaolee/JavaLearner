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










