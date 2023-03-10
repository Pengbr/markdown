redis缓存数据库

方便扩展、大数据量高性能、数据类型是多样型的

redis远程字典服务

redis-cli    redis-server

![image-20230206191650561](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20230206191650561.png)

redis benchmark 测试性能

reids默认有16个数据库

![image-20230208105555353](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20230208105555353.png)

redis是单线程的，redis基于内存操作

redis-key

```shell
exists key
move key
keys *
expire   ttl time to live 过期时间
```

