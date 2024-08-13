<h1 align="center">Docker</h1>

文档：***`https://docker.easydoc.net/doc/81170005/cCewZWoN/lTKfePfP`***

**打包**：就是把你软件运行所需的依赖、第三方库、软件打包到一起，变成一个安装包

**分发**：你可以把你打包好的“安装包”上传到一个镜像仓库，其他人可以非常方便的获取和安装

**部署**：拿着“安装包”就可以一个命令运行起来你的应用，自动模拟出一摸一样的运行环境，不管是在 Windows/Mac/Linux。

### 重要概念：镜像、容器

**镜像**：可以理解为软件安装包，可以方便的进行传播和安装。

**容器**：软件安装后的状态，每个软件运行环境都是独立的、隔离的，称之为容器。

拉取镜像创建容器：***`docker run -d -p 6379:6379 --name redis redis:latest`***

基础命令：

```powershell
# 查看镜像
docker images
# 查看容器
docker ps
```



