# mycat
分布式数据库中间件
支持SQL92标准
支持MySQL、Oracle、DB2、SQL Server、PostgreSQL等DB的常见SQL语法
遵守Mysql原生协议，跨语言，跨平台，跨数据库的通用中间件代理。
基于心跳的自动故障切换，支持读写分离，支持MySQL主从，以及galera cluster集群。
支持Galera for MySQL集群，Percona Cluster或者MariaDB cluster
基于Nio实现，有效管理线程，解决高并发问题。
支持数据的多片自动路由与聚合，支持sum,count,max等常用的聚合函数,支持跨库分页。
支持单库内部任意join，支持跨库2表join，甚至基于caltlet的多表join。
支持通过全局表，ER关系的分片策略，实现了高效的多表join查询。
支持多租户方案。
支持分布式事务（弱xa）。
支持XA分布式事务（1.6.5）。
支持全局序列号，解决分布式下的主键生成问题。
分片规则丰富，插件化开发，易于扩展。
强大的web，命令行监控。
支持前端作为MySQL通用代理，后端JDBC方式支持Oracle、DB2、SQL Server 、 mongodb 、巨杉。
支持密码加密
支持服务降级
支持IP白名单
支持SQL黑名单、sql注入攻击拦截
支持prepare预编译指令（1.6）
支持非堆内存(Direct Memory)聚合计算（1.6）
支持PostgreSQL的native协议（1.6）
支持mysql和oracle存储过程，out参数、多结果集返回（1.6）
支持zookeeper协调主从切换、zk序列、配置zk化（1.6）
支持库内分表（1.6）
集群基于ZooKeeper管理，在线升级，扩容，智能优化，大数据处理（2.0开发版）
========================== 分割线 ========================================
这里基于mycat，keepalived, haproxy,zookeeper,mysql 实践了高可用的一套电商方案（实现了基本的操作，具体的读者可自行扩展）

app 		app 		app
			 |
			 |		
--------------------------------
		  keepalived
haproxy<---------------->haproxy
	|	   zookeeper      |
mycat<------------------>mycat
|							|
--------------------------------
order01		orderN	user	goods
---------------------------------
order01slave,orderNslave,userslave,goodsslave