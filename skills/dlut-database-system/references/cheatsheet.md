# 数据库系统速查

## SQL 速查
```sql
-- 基本查询
SELECT col FROM table WHERE condition GROUP BY col HAVING agg_cond ORDER BY col LIMIT n;

-- 连接查询
SELECT * FROM A INNER JOIN B ON A.id = B.a_id;
SELECT * FROM A LEFT JOIN B ON A.id = B.a_id;

-- 子查询
SELECT * FROM A WHERE id IN (SELECT a_id FROM B WHERE cond);

-- 聚合函数
COUNT(*), SUM(col), AVG(col), MAX(col), MIN(col)
```

## 范式判断速查
- 1NF：属性不可分
- 2NF：1NF + 非主属性完全依赖于候选码
- 3NF：2NF + 不存在传递依赖
- BCNF：每个决定因素都是候选码

## 事务隔离级别与问题
| 隔离级别 | 脏读 | 不可重复读 | 幻读 |
|----------|------|-----------|------|
| 读未提交 | ✓    | ✓         | ✓    |
| 读已提交 | ✗    | ✓         | ✓    |
| 可重复读 | ✗    | ✗         | ✓    |
| 串行化   | ✗    | ✗         | ✗    |
