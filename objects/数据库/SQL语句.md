### DML -- CRUD 增删改查

insert语句

```
INSERT INTO table_name(col_name,...) VALUES(values,...)
-- 向表中插入一行数据, 自增字段, 缺省值字段, 可为 空字段可以不写
INSERT INTO table_name SELECT ...;
-- 将select查询的结果插入到表中
INSERT INTO table_name (col_name1,...) VALUES (values,...) On DUPLICATE KEY UPDATE
-- 如果主键冲突,唯一键冲突就执行update后的设置, 这条语句的意思, 就是主键不在新增记录, 主键在就更新部分字段
INSERT IGNORE INTO table_name (col_name,...) VALUES (value1,...);
-- 如果主键冲突,唯一键冲突就忽略错误, 返回一个警告
```



### SQL SELECT语句

SELECT语句用于从数据库中选取数据, 结果被存储在一个结果表中, 称为结果集.

```
SELECT column_name,column_name
FROM table_name;
```

```
SELECT * FROM table_name;
```

