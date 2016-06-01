# Docker 容器基础操作练习
```
1. 容器启动
docker	run	ubuntu:14.04	/bin/echo	'Hello	world'

启动一个	bash	终端，与用户交互
docker	run	-t	-i	ubuntu:14.04	/bin/bash

其中，-t	选项让Docker分配一个伪终端（pseudo-tty）并绑定到容器的标准输入上，-i 则让容器的标
准输入保持打开。

docker start	命令，直接将一个已经终止的容器启动运行

2. 查看容器

docker ps 

3. 终止容器

docker	stop
终止状态的容器可以用 	docker	ps	-a	命令看到

4. 守护态运行

docker run -d ubuntu:14.04 /bin/sh -c "while true; do echo hello world; sleep 1; done"
要获取容器的输出信息，可以通过 	docker	logs	命令

5.进入容器

1. 使用ssh登陆进容器 
2. 使用nsenter、nsinit等第三方工具 
3. 使用Docker本身提供的工具

在使用 -d 参数时，容器启动后会进入后台。 某些时候需要进入容器进行操作，有很多种方法，包括使用 docker attach 命令或 nsenter 工具等

docker attach

eg.

docker run -idt ubuntu
docker ps
docker attach d4a

如何退出容器而不停止容器：Ctrl+P+Q

6.导出容器

docker export 

docker export 7691a814370e > ubuntu.tar

7.导入容器快照

cat ubuntu.tar | sudo docker import - test/ubuntu:v1.0

也可以通过指定 URL 或者某个目录来导入
docker	import	http://example.com/exampleimage.tgz	example/imagerepo

用户既可以使用 	docker	load	来导入镜像存储文件到本地镜像库，也可以使用 	docker	import	来
导入一个容器快照到本地镜像库。这两者的区别在于容器快照文件将丢弃所有的历史记录和元数据信息
（即仅保存容器当时的快照状态），而镜像存储文件将保存完整记录，体积也要大。此外，从容器快照文
件导入时可以重新指定标签等元数据信息

8.删除容器
	docker	rm	trusting_newton

9.列出一个容器里面被改变的文件或者目录，list列表会显示出三种事件，A 增加的，D 删除的，C 被改变的
docker diff Name/ID 

10.显示一个运行的容器里面的进程信息
docker top Name/ID

11.从容器里面拷贝文件/目录到本地一个路径 
docker cp Name:/container_path to_path 
docker cp ID:/container_path to_path 

12.重启一个正在运行的容器
docker restart Name/ID 

```
