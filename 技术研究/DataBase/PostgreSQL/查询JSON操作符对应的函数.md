**主题：** 查询PostgreSQL中JSON操作符对应的函数

**背景：** 

在JPA中编写SQL语句时，有时会针对JSON类型进行操作，但是对于 ？ @> 等类似的操作符，在执行SQL时会出错，通过研究发现可以使用操作符对应的数来编写SQL的方式解决此问题。



查询操作符对应的函数语句如下：

```sql
SELECT 
	oid, *
FROM 
	pg_catalog.pg_operator
WHERE 
	-- 需要查询的操作符
    oprname = '?'
    -- 查询jsonb的操作
    AND oprleft = (SELECT oid FROM pg_type WHERE typname = 'jsonb');
```

查询结果中的 **oprcode** 字段就是该操作符对应的函数。

例如 **?** 操作符：

```sql
-- 假设 info 是一个json字段,查询info中是否存在name字段
select * from user where info ? 'name'
-- ===>
select * from user where jsonb_exists(info, 'name')
```