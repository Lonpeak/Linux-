<h1 align="center">Centos命令</h1>

系统配置情况：

> ```bash
> cat /etc/redhat-release		# Cenos查看系统信息
> uname -a                	# 查看内核/操作系统/CPU信息
> head -n 1 /etc/issue    	# 查看操作系统版本
> cat /proc/cpuinfo       	# 查看CPU信息
> hostname									# 查看计算机名
> lspci -tv               	# 列出所有PCI设备
> lsusb -tv               	# 列出所有USB设备
> lsmod                  	 	# 列出加载的内核模块
> env                     	# 查看环境变量
> dmidecode | grep "Product Nmae"   #查看服务器型号
> ```

关于资源：

> ```bash
> free -m                # 查看内存使用量和交换区使用量
> df -h                  # 查看各分区使用情况
> du -sh <目录名>        # 查看指定目录的大小
> grep MemTotal /proc/meminfo   # 查看内存总量
> grep MemFree /proc/meminfo    # 查看空闲内存量
> uptime                 # 查看系统运行时间、用户数、负载
> cat /proc/loadavg      # 查看系统负载
> # 查看内存的插槽数，已经使用多少插槽。每条内存多大，已使用内存多大
> dmidecode|grep -P -A5 "Memory\s+Device"|grep Size|grep -v Range 
> # 查看内存支持的最大内存容量
> dmidecode|grep -P 'Maximum\s+Capacity'
> # 查看内存的频率
> dmidecode|grep -A16 "Memory Device"
> dmidecode|grep -A16 "Memory Device"|grep 'Speed'
> ```

磁盘和分区：

> ```bash
> mount | column -t      # 查看挂接的分区状态
> fdisk -l               # 查看所有分区
> swapon -s              # 查看所有交换分区
> hdparm -i /dev/hda     # 查看磁盘参数(仅适用于IDE设备)
> dmesg | grep IDE       # 查看启动时IDE设备检测状况
> ```

网络：

> ```bash
> ifconfig               # 查看所有网络接口的属性
> iptables -L            # 查看防火墙设置
> route -n               # 查看路由表
> netstat -lntp          # 查看所有监听端口
> netstat -antp          # 查看所有已经建立的连接
> netstat -s             # 查看网络统计信息
> ```

进程：

> ```bash
> ps -ef                 # 查看所有进程
> top                    # 实时显示进程状态
> ```
>
> 















