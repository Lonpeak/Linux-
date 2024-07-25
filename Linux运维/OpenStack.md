<h1 align="center">OpenStack</h1>

## 1. ***虚拟机与容器：***

1. 虚拟机架构：宿主机-->多个OS-->Bin/Lib-->App

2. 容器架构：宿主机-->Bin/Lib-->App

   <img src="/Users/lonpeak/Desktop/Linux运维/access/1.png" style="zoom:50%;" />

 虚拟机的隔离性和安全性比容器要好，但是容器的性能方面更优秀。

 通过OpenStack可以对服务器资源进行统筹化管理；并且可以对虚拟机进行可视化管理，新增或删除、监控等。

## 2. ***OpenStack的项目分层：***

<img src="/Users/lonpeak/Desktop/Linux运维/access/2.png" style="zoom:25%;" />

**基础公共组件：**

> Database和Message Queue用的是公共组件，分别是MySQL和RabbitMQ。
>
> *KeyStone：*提供认证服务

**Iaas服务：**

> Nova：计算服务
>
> Glance：镜像服务
>
> Cinder：块存储服务
>
> Neutron：网络服务
>
> Ironic：裸金属服务

**系统管理及自动化:**

> Ceilometer：度量资源
>
> Heat：提供编排服务

**IaaS+服务：**

> Trove：数据库服务
>
> Sahara：大数据服务
>
> Swift：对象存储服务

***图形化界面：Horizon***

## 3.OpenStack主要项目之间的关系

<img src="/Users/lonpeak/Desktop/Linux运维/access/3.png" style="zoom:40%;" />

![](/Users/lonpeak/Desktop/Linux运维/access/4.png)

## 4.Nova

1. 什么是Nova

   > OpenStack中提供计算资源服务的项目
   >
   > Nova负责：
   >
   > - 虚拟机lifecycle管理
   > - 其他计算资源的lifecycle管理
   >
   > Nova不负责：
   >
   > - 承载虚拟机的物理主机自身的管理
   > - 全面的系统状态监控
   >
   > **总结：**Nova事实上是OpenStack最核心的项目组件

2. Nova的逻辑结构

   <img src="/Users/lonpeak/Desktop/Linux运维/access/5.png" style="zoom:30%;" />

3. Nova物理部署示例

   <img src="/Users/lonpeak/Desktop/Linux运维/access/6.png" style="zoom:50%;" />

4. Nova核心概念

   

5. 

## 5.























