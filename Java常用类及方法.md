##JAVA常用类及方法
1. Scanner（从文件、输入流、字符串中解析出基本类型值和字符串值）
	- hasNextXxx()
	- nextXxx()
2. System
	- getEnv() //环境
	- getProperties()  //属性
	- in //
	- out //
	- err //
	- identityHashCode(Object x)  //根据对象的地址生成的hash值，具有唯一性
	- gc() 

3. Runtime
	- gc()
	- load(String filename)  //加载文件
	- loadLibrary(String libname)  //加载动态链接库
	- 获取内存、处理器信息等
	- exec()  //另开一个进程处理操作系统命令
4. Object
	- equals()
	- finalize()
	- getClass()
	- hashCode()
	- toString()
	- wait()
	- notify()
	- notifyAll()
	- clone() //protected
5. Objects(1.7以上，Object的工具类)

6. Cloneable接口，实现clone
7. StringBuffer(字符序列可变的字符对象,线程安全)
	- append()
	- insert()
	- reverse()
	- setCharAt()
	- setLength() 
8. StringBuilder(非线程安全)
9. Math
10. 随机数
	- Random
	- ThreadLocalRandom（Java7新增）
11. BigDecimal（高精度计算）
12. Date(deprecated)
13. Calendar(抽象类)，需要自己实现子类，内部实现了一个`GregorianCalendar`子类，通过`Calendar.getInstance()`调用
	- add()
	- set()
	- roll()
14. TimeZone()
	- getDefault() //获取机器上的默认时区
	- getTimeZone() //根据时区ID获得对应的时区

15. 正则表达式
	1. String的正则匹配
		- boolean matches(String regex)
		- String replaceAll(String regex, String replacement)
		- String replaceFirst(String regex, String replacement)
		- String[] split(String regex)
	2. 正则类
		- Pattern
			- compile() //将正则字符串编译成Pattern对象
			- Matcher matcher(String str)
		- Matcher

16. 格式化
	1. NumberFormat
	2. DateFormat
	3. SimpleDateFormat


















