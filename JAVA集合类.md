##JAVA集合类
1. Collection
	1. Set（集合中不能存在相同的元素，HashSet和TreeSet建议存放不可变对象，否则可能引发很多操作异常，如：删除操作等）
		-HashSet
			- 无序
			- 不能存在相同的元素
				- equals()和hashCode()的返回值都相等则不能加入
		- LinkedHashSet(与HashSet相比为有序（元素加入的顺序）)
		- TreeSet（红黑树）
			1. 自然排序（比较元素大小）
				- 按照存入集合的对象的大小（对象继承Comparable接口，实现其compareTo()方法来比较，其中JAVA的BigDecimal,Character,Boolean,String,Date,Time都实现了这个接口）来排序
				- 如果compareTo()返回0，则此元素加不进去
			2. 定制排序（通过给构造方法传入一个实现Comparator接口的对象）
		- EnumSet（专为枚举类设置的） 
					

2. List集合
	














