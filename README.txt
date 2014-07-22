这是一个通用的日志服务器。

日志分5个等级：
	0	debug
	1	info
	2	warn
	3	error
	4 	fatal

使用zmq进行日志通信，传输协议：

	{level}:{appname}:{log content}
	
	level		日志等级
	appname		程序名称
	log content	日志内容

比如：
	1:manage:manage started.


日志路径，默认为：/tmp

日志文件输出格式：
	{log_prefix}_{appname}_{date_by_day}.log

比如：
	bamboo_manage_2014-07-22.log

参数配置，写在同目录下的settings.lua中，

	daemon 		为true表示，以daemon形式启动本服务
	loggers		为一张表，参见示例的settings.lua
	log_dir		指定日志文件存放路径。默认为/tmp
	log_prefix	指定日志文件命名前缀。默认为bamboo
	log_addr	指定日志的通信地址。默认为'ipc:///tmp/bamboo_log'
	cmd_sub_addr	指定本服务的控制端口
	
本服务器使用的是zmq pull接口，需发送端使用zmq push接口。

