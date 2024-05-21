# 第2章 简单动态字符串

redis将自己构建的一种名为简单动态字符串(`simple dynamic string, SDS`)的抽象类型用作默认的字符串表示。C字符串只会作为字符串字面(`string literal`)量用在一些无须对字符串值进行修改的地方。

```redis
127.0.0.1:6379> SET message 'hello world'
OK
```

该命令指示redis在数据库中创建一个新的键值对，其中：
* 键是一个字符串对象，其底层实现是一个保存着字符串"message"的SDS。
* 值也是一个字符串对象，其底层实现是一个保存着字符串"hello world"的SDS。

除了用来保存数据库中的字符串值，SDS还被用作缓冲区(buffer)：AOF模块中的AOF缓冲区以及客户端状态中的输入缓冲区。