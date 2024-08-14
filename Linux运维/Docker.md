<h1 align="center">Docker</h1>

文档：***`https://docker.easydoc.net/doc/81170005/cCewZWoN/lTKfePfP`***

**打包**：就是把你软件运行所需的依赖、第三方库、软件打包到一起，变成一个安装包

**分发**：你可以把你打包好的“安装包”上传到一个镜像仓库，其他人可以非常方便的获取和安装

**部署**：拿着“安装包”就可以一个命令运行起来你的应用，自动模拟出一摸一样的运行环境，不管是在 Windows/Mac/Linux。

### 重要概念：镜像、容器

**镜像**：可以理解为软件安装包，可以方便的进行传播和安装。

**容器**：软件安装后的状态，每个软件运行环境都是独立的、隔离的，称之为容器。

拉取Redis镜像并创建容器：***`docker run -d -p 6379:6379 --name redis redis:latest`***

基础命令：

```powershell
docker ps #查看当前运行中的容器
docker images #查看镜像列表
docker rm container-id #删除指定 id 的容器
docker stop/start container-id #停止/启动指定 id 的容器
docker rmi image-id #删除指定 id 的镜像
docker volume ls #查看 volume 列表
docker network ls #查看网络列表
docker compose up -d #创建多个容器编排
```

### 制作自己的镜像

> 1. 编写自己的dockerfile
> 2. 将依赖build为镜像
> 3. 运行
>
> 命令的参考文档：***`https://docs.docker.com/engine/reference/run/`***

### 目录挂载

> - ***`bind mount`*** 直接把宿主机目录映射到容器内，适合挂代码目录和配置文件。可挂到多个容器上
>
>   `bind mount` 用绝对路径 `-v D:/code:/app`
>
> - ***`volume`*** 由容器创建和管理，创建在宿主机，所以删除容器不会丢失，官方推荐，更高效，Linux 文件系统，适合存储数据库数据。可挂到多个容器上
>
>   `volume` 只需要一个名字 `-v db-data:/app`
>
> - ***`tmpfs mount`*** 适合存储临时文件，存宿主机内存中。不可多容器共享。

### 多容器通信

>  创建名为test-net的网络：***`docker network create test-net`***
>
> 运行 Redis 在 `test-net` 网络中，在网络中的别名是`redis`：***`docker run -d --name redis --network test-net --network-alias redis redis:latest`***

### Docker Compose

> - 如果你是安装的桌面版 Docker，不需要额外安装，已经包含了。
> - 如果是没图形界面的服务器版 Docker，你需要单独安装 [安装文档](https://docs.docker.com/compose/install/#install-compose-on-linux-systems)
> - 运行`docker-compose`检查是否安装成功
>
> 在`docker-compose.yml` 文件所在目录，执行：`docker-compose up`就可以跑起来了。
> 命令参考：https://docs.docker.com/compose/reference/up/
>
> 在后台运行只需要加一个 -d 参数`docker-compose up -d`
> 查看运行状态：`docker-compose ps`
> 停止运行：`docker-compose stop`
> 重启：`docker-compose restart`
> 重启单个服务：`docker-compose restart service-name`
> 进入容器命令行：`docker-compose exec service-name sh`
> 查看容器运行log：`docker-compose logs [service-name]`

### 备份和迁移数据

> 容器中的数据，如果没有用挂载目录，删除容器后就会丢失数据。
> 前面我们已经讲解了如何 [挂载目录](doc:kze7f0ZR)
> 如果你是用`bind mount`直接把宿主机的目录挂进去容器，那迁移数据很方便，直接复制目录就好了
> 如果你是用`volume`方式挂载的，由于数据是由容器创建和管理的，需要用特殊的方式把数据弄出来。
>
> ***备份：***
>
> - 运行一个 ubuntu 的容器，挂载需要备份的 volume 到容器，并且挂载宿主机目录到容器里的备份目录。
> - 运行 tar 命令把数据压缩为一个文件
> - 把备份文件复制到需要导入的机器
>
> ***导入：***
>
> - 运行 ubuntu 容器，挂载容器的 volume，并且挂载宿主机备份文件所在目录到容器里
> - 运行 tar 命令解压备份文件到指定目录
>
> ***备份 MongoDB 数据演示***
>
> - 运行一个 mongodb，创建一个名叫`mongo-data`的 volume 指向容器的 /data 目录
>   `docker run -p 27018:27017 --name mongo -v mongo-data:/data -d mongo:4.4`
> - 运行一个 Ubuntu 的容器，挂载`mongo`容器的所有 volume，映射宿主机的 backup 目录到容器里面的 /backup 目录，然后运行 tar 命令把数据压缩打包
>   `docker run --rm --volumes-from mongo -v d:/backup:/backup ubuntu tar cvf /backup/backup.tar /data/`
>
> 最后你就可以拿着这个 backup.tar 文件去其他地方导入了。
>
> ***恢复 Volume 数据演示***
>
> - 运行一个 ubuntu 容器，挂载 mongo 容器的所有 volumes，然后读取 /backup 目录中的备份文件，解压到 /data/ 目录
>   `docker run --rm --volumes-from mongo -v d:/backup:/backup ubuntu bash -c "cd /data/ && tar xvf /backup/backup.tar --strip 1"`
>
> ```
> 注意，volumes-from 指定的是容器名字
> strip 1 表示解压时去掉前面1层目录，因为压缩时包含了绝对路径
> ```
>
> 











































