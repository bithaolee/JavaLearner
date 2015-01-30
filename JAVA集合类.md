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
					

2. List集合（判断两个元素是否相等的标准是通过比较`equals()`方法的返回值，删除元素时以此做判断）
	- 迭代器（ListEterator）
	- ArrayList
	- Vector(不要再用了)
	- LinkedList(还继承了Deque)，双向链表

3. Queue（队列）
	- PriorityQueue
		- 按照元素大小排序，并进行操作，而非按加入的先后顺序
		- 排序的规则参照TreeSet
	- Deque(双端队列，接口)
		- ArrayDeque

4. Map(同一个map中的key对象不能重复，通过key对象的equals()方法来判断)，其实Map和Set有很多相似之处，可以理解为，Map忽略掉value值和Set基本相同
	- HashMap
		- 判断key值是否相等，和HashSet的判断方法一致
		- 判断value的值是否相等，只需判断equals()方法即可
		- LinkedHashMap
			- 保证迭代顺序
	- TreeMap
		- key的行为和TreeSet的一致
	- IdentityHashMap
		- 对于key的值需要严格相等，及内存地址一样（key1==key2）
	- Hashtable(不要再用了)
	- EnumMap

5. 操作集合类的工具
	- 排序操作
		- reverse()
		- shuffle()
		- sort()
		- sort()
		- swap()
		- retate()
	- 查找替换
		- binarySearch()
		- max()
		- max()
		- min()
		- min()
		- fill()
		- frequency()
		- indexOfSubList()
		- lastIndexOfSubList()
		- replaceAll()
	- 同步（包装集合对象为线程安全的）
		- synchronizedList(集合对象)
		- synchronizedMap()
		- synchronizedSet()

6. 设置不可变集合
	- emptyXxx()  //返回一空的、不可变集合
	- singletonXxx()  //返回一个值包含指定对象的
	- unmodifiableXxx()  //返回指定集合的不可变视图
	




























