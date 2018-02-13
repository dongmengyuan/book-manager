# book-manager
XiyouLinuxGroup图书管理系统

整体架构说明

config ----spring <-放置spring的配置文件
       |
       ----database <-放置数据库的配置文件

 dao ----dbfactory <-dao接口的生产工厂
     |
     ----dbimpl   <-数据库接口的实现类
     |
     ----dbservice <-数据库所提供的调用接口

model ---- <-存放Java Bean等数据模型

web  ---- <-存放控制器

test ---- <-存放测试类

upload ---- <-存放上传的文件

view ---- <-存放jsp、html等文件

utilClass ---- <-存放工具类(比如日期转换类:将时间戳转换为yy-mm-dd hh:mm:ss)
数据库建表

建表规范

主键一律无意义，就算有意义，也必须是以后不会被更新，修改并且是自增的字段。命名规范一律是pk_id,数据类型为int unsigned,字段not null。
唯一索引命名一律以uk_为前缀，唯一索引并不以提高查询速率为主要目的，主要是进行唯一性约束。
唯一组合索引命名一律以ugk_为前缀，目的同上，注意最左前缀的问题。
由于主键一律设置的是无意义的自增字段，所以对于有外键约束的字段，只设置了级联删除（只更新父表的主键会存在外键约束）。
日期字段的数据类型一律为datetime。
所有表的字段设置为not null，数字默认值为0,字符串默认值为''，datetime没有设置默认值，因此在后台必须处理时间问题。