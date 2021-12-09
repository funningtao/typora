## Docker学习

### 启动、停止

启动`sudo service docker start`

停止`sudo service docker stop`

重启`sudo service docker restart`

### 镜像操作

列出镜像`docker images`

- REPOSITORY：镜像所在的仓库名称
- TAG：镜像标签
- IMAGEID：镜像ID
- CREATED：镜像的创建日期(不是获取该镜像的日期)
- SIZE：镜像大小

搜索镜像`docker search`

拉取镜像`docker pull`

删除镜像`docker image rm 名&ID`

### 容器操作

创建容器

`docker run [option] 镜像名 [向启动容器中传入命令]`

`sudo docker run -itd --name build2 -v /home/${USER}:/home/scm 192.168.11.230/scm/ubuntu-14.04.3:plane3.0-wm /bin/bash`

- -i 表示以“交互模式”运行容器
- -t 表示容器启动后会进入其命令行。加入这两个参数后，容器创建就能登录进去。即 分配一个伪终端。
- --name 为创建的容器命名
- -v 表示目录映射关系(前者是宿主机目录，后者是映射到宿主机上的目录，即 宿主机目录:容器中目录)，可以使 用多个-v 做多个目录或文件映射。注意:最好做目录映射，在宿主机上做修改，然后 共享到容器上。
- -d 在run后面加上-d参数,则会创建一个守护式容器在后台运行(这样创建容器后不会自动登录容器，如果只加-i -t 两个参数，创建后就会自动进去容器)。
- -p 表示端口映射，前者是宿主机端口，后者是容器内的映射端口。可以使用多个-p 做多个端口映射
- -e 为容器设置环境变量
- --network=host 表示将主机的网络环境映射到容器中，容器的网络与主机相同

进入已经运行的容器

`docker exec -it ID 指令`

**docker exec -it ID /bin/bash**

查看容器`docker ps -a`

停止一个已经在运行的容器
`docker container stop容器名或容器id`

启动一个已经停止的容器

`docker container start 容器名或容器id`

kill掉一个已经在运行的容器

`docker container kill 容器名或容器id`

删除容器`docker container rm id`

### 容器保存为镜像

`docker commit 容器名 镜像名`

### 镜像备份与迁移

打包镜像`docker save -o 保存的文件名 镜像名`

`docker save -o ./ubuntu.tar ubuntu`

加载镜像文件到本地

`docker load -i ./ubuntu.tar`