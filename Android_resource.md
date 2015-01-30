##Android资源文件
----------------
###Asset目录下的文件，不能直接，需要`AssetManager`以二进制流形式来读取

###res目录下的文件，项目编译过程中自动创建索引R.java文件
	res //有索引的资源目录
	 |--animator  //属性动画xml文件
	 |--anim  //补间动画xml文件  
	 |--color  //不同状态下的颜色列表xml
	 |--
    ...
	 |--values
		   |
		   |---string.xml  //字符串资源（R.string.）	
		   |---color.xml  //(R.color.),可定义透明度
		   |---dimen.xml  //尺寸资源(R.dimen.)
		   

- 资源获取方式：
	- Resources类（通过`Context`的`getResources()`方法获取）
		- `gerXxx(int id)`  //通过资源清单的id值（R.xxx.xxx）获取相应的资源
		- `getAssets()`  //获取assets目录下资源的AssetManager对象
	- 重要的资源
		- StateListDrawable
			- 根元素为`<selector />`,包含多个`<item  />`,`item`的属性有`android:color|android:drawable`和android:state_xxx
		- LayerDrawable
			- ......
		- ShapeDrawable
			- 根元素为`<shape />`,属性如下：
				- android:shape=["rectangle"|"oval"|"line"|"ring"]
				- 子元素：
					- <corners> //四个角的弧度
					- <gradient> //定义使用渐变色填充
					- <padding> //内边距
					- <size> //大小
					- <solid> //单种颜色填充
					- <stroke> //绘制边框
		- ClipDrawable
			- <clip />元素，主要的属性如下：
				- android:drawable  //截取的源drawable对象
				- android:clipOrientation="horizontall|vertical"  //截取的方向
				- android:gravity  //截取的对齐方式
			- 通过ClipDrawable对象的setLevel(int level)方法设置截取的区域大小（0-10000）
		- AnimationDrawable
		- PropertyAnimation
	- 使用原始的XML资源（/res/xml/）
		- xml中访问：`@[<package_name>:]xml/file_name`
		- Java中访问：`[<package_name>.]R.xml.<file_name>`
		- 通过Resources的如下两个方法获取解析
			- XmlResourceParser getXml(int id) //获取xml文档对象
			- InputStream openRawResource(int id)  //获取xml输入流
	- 使用menu文件
		- xml中使用：`@[<package_name>:]menu/file_name`
		- JAVA中使用：`[<package_name>.]`R.menu.file_name
	- style.xml(/res/value/style.xml),定义一组全局的样式组合
	- 主题，用`style`，不同的是主题只能用于整个activity，不能作用于单个元素，在Java中通过`setTheme(int id)`方法设置，也可以在`manifest.xml`中的`<application android:theme="@style/xxx">`或`<activity android:theme="@android:style/Theme.Dialog">`
	- 属性资源（自定义一些组件时用到）
	- 音乐、视频等原始资源（/assets/或/res/raw/）
	- 国际化
		- 字符资源国际化
			- values-语言代码-r国家代码
				- values-zh-rCN、values-en-rUS
		- 图片资源国际化
			- drawable-语言代码-r国家代码[-mdpi|hdpi|xhdpi...]
				









































