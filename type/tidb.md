# TiDB 

UDTS支持 TiDB 作为数据传输源/目标，支持版本 3.* 和 4.*

## TiDB 填写表单

| 参数名   | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| IP       | 内网地址需要填写VPC和子网信息。                            |
| 端口     | 连接端口                                                |
| 用户名   | 连接用户名                                              |
| 密码     | 用户名对应密码                                          |
| 数据库名 | 如果是单个数据库，请填写数据库名；如果是多个数据库，填写以逗号分割的数据库列表；如果是所有数据库，请填写* |                                              |
| 表名     | 传输表名，只有迁移单个数据库时有效。如果是单个表，请填写表名；如果是多个表，填写以逗号分割的列表；若不填或者填写*，则整库迁移     |

## 预检查项

以TiDB为源库时，TiDB参数`tikv_gc_life_time`建议大于1小时，以避免迁移过程中发生 GC 导致迁移失败。

查询方式：
```
select VARIABLE_NAME, VARIABLE_VALUE from mysql.tidb where VARIABLE_NAME = "tikv_gc_life_time"
```

设置方式：
```
set global tidb_gc_life_time = '24h';
```