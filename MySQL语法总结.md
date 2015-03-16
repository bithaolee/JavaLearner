#MySQL语法总结
-----------
1. 使用帮助(命令行执行语句)
	- ? contents
	- ? data types
	- ? show
	- ? create table
2. 存储引擎
	- myisam
	- innodb
3. 字符集
4. 索引
	- 可以使用前缀索引
5. 锁机制
6. SQL模式
	- ANSI （字段值超过了给定的大小，将会被截取）
	- STRICT_TRANS_TABLES
	- TRADITIONAL
7. 聚合函数
	- min,max
	- rand
	- ...
8. 优化
	- show status;
	- show processlist;
	- explain sql语句
		- select_type： select 类型 
		- table：   输出结果集的表 
		- type：     表示表的连接类型   当表中仅有一行是type的值为system是最佳的连接类型； 当select操作中使用索引进行表连接时type的值为ref；  当select的表连接没有使用索引时，经常会看到type的值为ALL，表示对该表进行了全表扫描，这时需要考虑通过创建索引来提高表连接的效率。 
		- possible_keys： 表示查询时,可以使用的索引列. 
		- key：     表示使用的索引 
		- key_len：  索引长度 
		- rows：   扫描范围  
		- Extra：     执行情况的说明和描述 
	- analyze table
	- check table
	- checksum table
	- optimize table
9. 数据库的导入
	- mysqldump -opt db_name | mysql -h 新的host -p port -u user -p pwd db_name(新的数据库中的表)
	- 在shell里面执行`mysql_fix_privilege_tables`命令升级权限表
	- 备份
	- 还原
	- 错误日志
	- binlog
	- 慢查询
	- 主从数据库的配置