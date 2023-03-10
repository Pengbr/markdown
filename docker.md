# 容器技术

Docker 包括三个基本概念:

- **镜像（Image）**：Docker 镜像（Image），就相当于是一个 root 文件系统。比如官方镜像 ubuntu:16.04 就包含了完整的一套 Ubuntu16.04 最小系统的 root 文件系统。
- **容器（Container）**：镜像（Image）和容器（Container）的关系，就像是面向对象程序设计中的类和实例一样，镜像是静态的定义，容器是镜像运行时的实体。容器可以被创建、启动、停止、删除、暂停等。
- **仓库（Repository）**：仓库可看成一个代码控制中心，用来保存镜像。

Docker 使用客户端-服务器 (C/S) 架构模式，使用远程API来管理和创建Docker容器。

Docker 容器通过 Docker 镜像来创建。

容器与镜像的关系类似于面向对象编程中的对象与类。

| Docker | 面向对象 |
| :----- | :------- |
| 容器   | 对象     |
| 镜像   | 类       |

# docker基本使用

```shell
docker run hello-world
docker images
docker search  搜索镜像
docker pull  下载镜像
docker rmi -f 容器ID
docker rmi -f $(docker iamges -aq)  删除所有容器
# 运行容器
docker run [可选参数] image
--name 容器名字  -d 后台运行方式  -it使用交互方式运行  -p宿主机端口:容器内部端口
docker run -it centos /bin/bash  启动并进入容器
exit 退出容器
docker ps 列出当前所有运行的容器
docker ps -a 列出所有容器
# 显示日志
docker logs
# 查看进程信息
docker top
# 查看镜像的元数据
docker inspect
# 启动容器与停止容器
docker start 容器ID
docker stop 容器ID
# 进入容器
docker exec -it 容器ID
docker attach 容器ID
# 从容器拷贝到主机
docker cp 容器ID：容器内路径 目的主机路径
# 部署nginx
docker run -d --name nginx01 -p 3344:80 nginx
# 进入nginx
docker exec -it nginx01 /bin/bash
```

docker分层下载，docker image的核心，联合文件系统

容器相当于一个小的linux

# commit镜像

```shell
docker commit
docker commit -m '提交描述的信息' -a '作者' 容器ID 目标镜像名:[tag]
docker commit -a='br' -m='add webapps app' a2a261cf4672 tomcat02:1.0
```

# 容器数据卷

数据卷是一个虚拟目录，指向宿主机文件系统中的某个目录。一旦完成数据卷挂载，对容器的一切操作都会作用在数据卷对应的宿主机目录了。

容器之间可以有一个数据共享的技术。docker容器中产生的数据同步到本地。这就是卷技术。

一个是端口的映射，一个是文件目录的映射

```shell
# 直接使用命令挂载 -v    容器与主机双向绑定
docker run -it -v 主机目录：容器内目录
docker run -it -v C:\Users\hp\Desktop\test:/home centos /bin/bash
```

具名与匿名挂载

volume 卷

```shell
docker volume
-v 容器内路径    匿名挂载
-v 卷名：容器内路径    具名挂载
```

# dockerfile

dockerfile用来构建docker的镜像文件

数据卷容器

```shell
docker build 构建镜像
docker run 运行镜像
docker push 发布镜像
docker history 
```

1、每个保留关键字必须是大写字母    2、执行从上到下顺序执行   3、#表示注释   4、每一个指令都会创建提交一个新的镜像层

```shell
# dockerfile 基础指令
FROM 基础镜像
MAINTAINER 镜像是谁写的
RUN 运行命令
ADD 添加内容
WORKDIR 工作目录
VOLUME 挂载的目录
EXPOSE 暴露端口配置
CMD 指定容器启动时要运行的命令 可被覆盖
ENTRYPOINT 指定容器启动时要运行的命令 可以追加命令
ONBUILD 触发指令
COPY 将文件拷贝到镜像中
ENV 构建时设置环境变量
```

# 发布镜像

```shell
docker login 登录
docker tag 添加版本
docker push 发布
```

