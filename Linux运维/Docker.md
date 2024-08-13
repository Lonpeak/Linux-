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

> 













































