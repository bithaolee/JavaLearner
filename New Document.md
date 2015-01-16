#Java基础知识
-------------
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

