# Java 程序设计速查

## 常用语法速查
```java
// 增强 for
for (Type item : collection) { }

// Lambda
list.forEach(item -> System.out.println(item));

// Stream
list.stream().filter(x -> x > 0).map(x -> x * 2).collect(Collectors.toList());
```

## 集合选择速查
| 场景 | 推荐实现 |
|------|----------|
| 随机访问多 | ArrayList |
| 插入删除多 | LinkedList |
| 去重无序 | HashSet |
| 去重有序 | TreeSet |
| 键值查找 | HashMap |
| 键值有序 | TreeMap |
| 线程安全 List | CopyOnWriteArrayList |
| 线程安全 Map | ConcurrentHashMap |

## 异常层次
```
Throwable
├── Error（严重错误，不处理）
└── Exception
    ├── RuntimeException（非受检）
    │   ├── NullPointerException
    │   ├── ArrayIndexOutOfBoundsException
    │   └── IllegalArgumentException
    └── 其他受检异常（IOException、SQLException 等）
```

## JDBC 模板
```java
Class.forName("com.mysql.cj.jdbc.Driver");
Connection conn = DriverManager.getConnection(url, user, pass);
PreparedStatement ps = conn.prepareStatement("SELECT * FROM t WHERE id=?");
ps.setInt(1, id);
ResultSet rs = ps.executeQuery();
```
