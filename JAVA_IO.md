##JAVA的IO处理
1. File（创建删除等文件操作，除了输入输出流之外的基本操作）

2. 在File的list()操作时，可传入一个过滤器`FilenameFilter`(接口)

3. JAVA的IO流（字节流和字符流只是处理的单位不一样，一个字节8byte，一个字符16byte）
	1. 字节流（输入输出的内容是二进制推荐使用）
		- InputStream（抽象类）
			- read() //从输入流读取一个字节
			- read(byte[] b) //读取b.length个字节，存到b中，返回读取的字节数，结束了就返回-1
			- read(byte[] b, int off, int len) //读取len个字节，从b的off位置存起
			- 指针操作
				- mark()
				- markSupport()
				- reset()
				- skip()
		- OutputStream(抽象类)
			- 参数基本等同InputStream,只是方法名变为write(),如：write(byte[] b) //表示将b数组中的数据输出到输出流中
	2. 字符流（输入输出的内容是文本推荐使用）
		- Reader（抽象类）
			- read() //读取一个字符
			- read(char[] c) //读取c.length个字符，存到c中
			- read(char[] c, int off, int len)  //...
			- 指针操作
				- mark()
				- markSupport()
				- reset()
				- skip()
		- Writer
			- 同OutputStream,参数类型为char类型，比OutputStream多出两个方法
			- write(String str)
			- write(String str, int off, int len)

	3. 处理流（忽略底层，编程更简洁）
		- PrintStream(包装了OutputStream)

	4. 转换流（将字节流转换成字符流）
		- InputStreamReader
		- OutputStreamWriter

	5. 缓冲流
		- BufferedReader
		- BufferedWriter
		- BufferedInputStream
		- BufferedOutputStream
	5. 推回输入流（将读取到的内容退回缓冲区，从而可以重复读取）
		- PushbackInputStream
		- PushbackReader

	6. 重定向标准输入输出流
		- System中有几个方法如下：
			- setOut()
			- setErr()
			- setIn()
	7. 随机存取流(可以自由移动指针位置，可在文件末尾追加内容)
		- RandomAccessFile
	8. 管道流（）
		
	8. 对象序列化

4. NIO级NIO2的操作





















































