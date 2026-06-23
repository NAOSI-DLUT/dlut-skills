# Java 程序设计复习要点

## 核心概念对比
| 概念 | 要点 |
|------|------|
| 抽象类 vs 接口 | 抽象类可有成员变量和实现方法；接口 JDK8 前全抽象，现在有 default/static |
| == vs equals | == 比较引用/基本值；equals 默认引用比较，String 等已重写 |
| String vs StringBuilder | String 不可变；StringBuilder 可变、非线程安全；StringBuffer 线程安全 |
| ArrayList vs LinkedList | 数组实现/随机访问快 vs 链表实现/插入删除快 |

## 易错点
- 泛型擦除：运行时无泛型类型信息
- 多线程中 `i++` 非原子操作，需同步或使用原子类
- `finally` 块通常执行，但 System.exit 或 JVM 崩溃时不执行
- 资源释放要用 try-with-resources：`try (InputStream in = ...) { }`

## 大题常见类型
1. 面向对象设计（类图、继承、多态应用）
2. 集合操作与算法实现
3. 多线程编程（生产者消费者、读写锁）
4. IO 流操作（文件复制、对象序列化）
5. Socket 通信编程
6. JDBC 数据库操作
