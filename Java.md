#Java基础知识
-------------
##补码
取反加一
正数取反加一等于相对应的负数

##数据类型
- 基本数据类型
	- 整数 
		- byte     1byte 8位
		- short    2byte 16位
		- int      4byte 32位  
		- long     8byte 64位
	- 浮点 
		- float    4byte 32位
		- double   8byte 64位
	- 字符型
		- char     
- 复合数据类型
##变量
- 成员变量
	- 静态变量 `static`声明的类属性
	- 实例变量 普通的类属性
- 局部变量
	`{`和`}`中的变量
##作用域
块状`{`,`}`之间声明的变量不能被外部访问
##常量
	`final double PI = 3.1415926;` 
##类型转换
- 自动类型转换
	遵循有低级到高级规则
- 强制类型转换
	(类型名)变量    布尔型不能与其它类型转换

##复合语句
变量的作用域从外往里，不能由内而外
```
int a = 1;
{
	System.out.print(a);
	{
		{
			System.out.print(a);
		}
	}
}
```

##分支语句
```
switch(x){
	// x必须为整型或字符型
}
```

##循环语句
foreach语句：
```
	for(元素变量x : 遍历对象obj){
		
	}
```

##数组
- 一维数组
声明：  `类型[] 变量名`
分配内存： `new 类型[num]`
赋值：`变量名 = {first, second, third, forth, fifth, ...}`
一下几种写法都行：
	- `int[] j = new int[]{1,3,9,4,6,58}`
	- `int[] m = {1,5,1,9,3,4}`
- 二维数组
`int[][] i = {{1,3},{4,9},{5,3}};`

数组的长度：length属性
arr.length

数组的复制：
`import java.util.Arrays;`<br />
`Arrays.copyOf(数组);`<br />
`Arrays.copyOfRange(数组);`

##字符串
- 声明初始化方式
	- `String s = new String(char[] a, int offset, int length);` //还有其它的参数重载，具体看手册
- 字符串的连接（少用，连接后产生一个新的String对象）
	连接字符 `+`
- 获取字符串的长度
	str.length();
- 字符串中子串的搜索
	- 首次出现的位置：`str.indexOf(子串);`
	- 最后一次出现的位置:`str.lastIndexOf(子串);`
- 获取指定位置的字符
	str.charAt(int index); 
- 去除前后的空格
	str.trim();
- 字符的替换
	str.replace(),str.replaceAll(),str.replaceFirst(),...具体参数参照手册
- 判断字符串是否相等
	- 严格区分大小写  `str.equals(String oldStr);`
	- 不区分大小写 `str.equalsIgnoreCase(String oldStr);`
	- ‘==’号比较的内存中的地址
- 判断字符串是否以指定的字符开始或结束
	str.startsWith(String prefix);
	str.endsWith(String suffix);
- 大小写转换
	str.toLowerCase();
	str.toUpperCase();
- 字符串的分割
	String[] strs = str.split(String sign); //定义多个分隔符用 “|”隔开
- 格式化字符串
	str.format([Local i,] String format, Object args);
	- 日期格式化
		- 啊啊
	- 时间格式化
	- 日期时间组合格式化
		`%tF`  2008-03-26<br />
		`%tD`  03/25/08
		`%tc`,`%tr`,`%tT`,`%tR`
	- 常规格式化<br />
		%b,%B 布尔<br />
		%h,%H 散列码<br />
		%s,%S 字符串<br />
		%c,%C 字符<br />
		%d 十进制<br />
		%o 八进制<br />
		%x,%X 十六进制
- 正则表达式
	str.matches(String regex);
- 字符串生成器<br />
	StringBuilder str = new StringBuilder(""); //不可用于多线程，多线程改用StringBuffer类<br/>，具体方法参照手册，最后转换成String类型，str.toString();
	

##类与对象
#### 匿名对象：
new 对象名()
#### 构造方法：
与类名同名，可以有多个
#### this关键字：
- this.成员属性   
- this.成员方法
- this(参数) 表示构造方法

####子类调用父类的构造方法
super(参数列表);
####子类调用父类被隐藏的属性和被重写的成员方法
super.成员属性名;
super.成员方法名();


##内部类
不允许非静态内部类中定义静态成员
####成员内部类
内部类的声明：<br />
`外部类名.内部类名 实例变量名；`，内部类需要通过外部类的对象来实例化，例如：<br />
```
Outer o = new Outer();
Outer.Inner i = o.new Inner();
```
内部类的特性：可以随意使用外部类的成员属性和方法，`外部类名.this`指向外部类实例；

####局部内部类
类的方法中定义的类。

1. 仅在定义了它们的代码块中是可见的；
2. 可以使用定义它们的代码块中的任何局部 final 变量；
3. 局部类不可以是 static 的，里边也不能定义 static 成员；
4. 局部类不可以用 public、private、protected 修饰，只能使用缺省的；
5. 局部类可以是 abstract 的。

####匿名内部类
匿名内部类是局部内部类的一种特殊形式，也就是没有变量名指向这个类的实例，而且具体的类实现会写在这个内部类里面。<br />
```
new 类名{
	public void getName(){
		//...
	}
}
```

####静态内部类



##反射


-----------------------------------------
##final
final 修饰的变量，变量的地址就不能改变了，如果是对象，对象的内容可发生变化
final 修饰的方法，不能被子类重写，可以被子类重载

	- 重写：能被子类继承，但子类重写了这个方法
final 修饰的类，不能被继承


##接口


##枚举类





=====================================
##Scanner
- next(); //以空格或回车结束
- nextLine(); //以回车结束
- nextInt(); //接收int类型
- nextDouble(); //接收double类型
- next



##多线程
####实现多线程的方式
	1. Thread
		- run()  //具体执行的任务，Override，不要直接调用
		- isAlive()  //线程是否未死亡
		- join()  //等待别的线程完成再执行
			- join()  //等待被join的线程完成
			- join(long millis)  //等待被join的线程 n 毫秒，如果还没结束，不再等待
			- join(long millis, int nanos)  //等待millis毫秒加nanos微秒
		- Thread 的静态方法
			- currentThread();返回当前正在运行的线程对象
			- sleep()  //睡眠线程
				- sleep(long millis)  //等待millis毫秒
				- sleep(long millis, int nanos)  //等待millis毫秒加nanos微秒
			- yield()  //线程让步，类似于睡眠线程，将线程转为`就绪`状态，只有优先级大于或等于此线程的处于就绪状态的线程才能获得执行的机会
	2. Runnable接口（可共享实例）
	3. Callable接口的call()方法和FutureTask包装类实现多线程，可以有返回值
####守护线程（后台线程）
后台运行，如果前台线程都死亡，守护线程也会自动死亡；
通过`setDaemon(true)`方法可以将一个线程设置为守护线程，先设置，在使用`start()`方法
####线程的优先级（1 ~ 10）
- 常量（可以是常量也可以是整数（1-10））
	- Thread.MAX_PRIORITY    10
	- Thread.PRIORITY        1
	- Thread.NORM_PRIORITY   5
- 方法
	- setPriority(常量或整数)  //设置优先级
	- getPriority(常量或整数)  //获取优先级
- 子线程默认优先级和父线程一致

####线程的声明周期
#####**notice**:
    状态
	    1. 新建
	    2. 就绪
	    3. 运行
	    4. 阻塞
	    5. 死亡

####线程同步
	1. 同步代码块
		
		synchronized(监视器[即被锁住的对象]){
			//执行程序
		}
		相当于 `加锁`-->`修改`-->`释放`
	2. 同步方法
		synchronized 关键字来修饰的方法，监视器为 this

#####同步锁
- Lock(接口)
- ReadWriteLock(接口)
####死锁

####线程通信
Object（都只能是监视器对象调用）
	- wait()  //将此监视器对象置为阻塞状态
	- notify()  //随机唤醒其他线程
	- notifyAll()  //唤醒其他所有线程
####线程池
- newCachedThreadPool
- newFixedThreadPool
- newScheduledThreadPool
- newSingleThreadPool
####线程相关类





##泛型
notice：
	- 在静态方法、静态块、静态变量中不能使用类型形参



##强制垃圾回收（只是通知系统回收，并不确定一定回收）
1. System.gc();
2. Runtime.getRuntime().gc();
3. Object的`finalize()`析构方法，在gc之前才执行