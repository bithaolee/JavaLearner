##JAVA反射
- 步骤：
	1. 加载
	2. 初始化

- 类加载器
	
- 反射查看类信息(通过Class类查看)
	- Class对象
		1. Class.forName() 
		2. 类名.class //推荐
		3. 实例.getClass()  
	- 通过Class对象获取相应的信息
		- 获取类对应的构造器（Constructor）
		- 获取类对应的方法（Method）
		- 获取类对应的属性（field）
		- 获取类对应的注解（annotation）
		- 获取该类对应的内部类（getDeclaredClasses()）
		- 获取该类对应的外部类（getDeclaringClass()）
		- 获取实现的接口
		- 获取超类
		- 获取包名
		- 获取所有访问修饰符
		- 获取类名（getName()）
		- 获取类的简称
		- 是否是注解类型（isAnnotation()）
		- 是否使用Annotation修饰（isAnnotationPresent()）
		- 是否是匿名类（isAnonymousClass()）
		- 是否是数组类（isArray()）
		- 是否是枚举类（isEnum()）
		- 是否是接口（isInterface()）
		- 判断一个对象是否是该类的实例（isInstance(Object obj)）
	- 通过反射创建对象
		- Class对象的newInstance()方法创建  //实际是通过默认构造器创建的
		- 通过制定的构造器创建实例，通过相应的构造器的newInstance()方法创建
	- 通过反射调用方法
		- 通过Method对象的invoke()方法调用
		- 通过调用Method对象的setAccessible(boolean flag)可以取消或恢复java语言的访问权限检查
	- 通过反射获取属性值（忽略访问权限）
		- 通过Field对象的getXxx(Object obj)获取
		- 通过Field对象的setXxx(Object obj)设置
	- 操作数组
		- Array.newInstance(Class<?> componentType, int... length)
		- setXxx()
		- getXxx()



























































































