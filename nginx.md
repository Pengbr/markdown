**架构：没有什么是加一层解决不了的**

```shell
nginx.exe 启动nginx
nginx -s stop 停止
nginx -s reload 重新加载
nginx -s quit安全退出
```



## 正向代理与反向代理

代理客户端的是正向代理（例如VPN），代理服务器的是反向代理

## nginx反向代理

![image-20230116085611693](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20230116085611693.png)

## 负载均衡

轮询、加权重

## 动静分离

动态资源与静态资源分离