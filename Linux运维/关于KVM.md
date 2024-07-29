<h1 align="center">关于KVM</h1>

1. 更换Centos7的yum源：

   > ```
   > cat > /etc/yum.repos.d/CentOS-Base.repo << EOF
   > [base]
   > name=CentOS-7 - Base - mirrors.aliyun.com
   > failovermethod=priority
   > baseurl=http://mirrors.aliyun.com/centos/7/os/\$basearch/
   > gpgcheck=1
   > gpgkey=http://mirrors.aliyun.com/centos/RPM-GPG-KEY-CentOS-7
   > 
   > #released updates
   > [updates]
   > name=CentOS-7 - Updates - mirrors.aliyun.com
   > failovermethod=priority
   > baseurl=http://mirrors.aliyun.com/centos/7/updates/\$basearch/
   > gpgcheck=1
   > gpgkey=http://mirrors.aliyun.com/centos/RPM-GPG-KEY-CentOS-7
   > 
   > #additional packages that may be useful
   > [extras]
   > name=CentOS-7 - Extras - mirrors.aliyun.com
   > failovermethod=priority
   > baseurl=http://mirrors.aliyun.com/centos/7/extras/\$basearch/
   > gpgcheck=1
   > gpgkey=http://mirrors.aliyun.com/centos/RPM-GPG-KEY-CentOS-7
   > 
   > #additional packages that extend functionality of existing packages
   > [centosplus]
   > name=CentOS-7 - Plus - mirrors.aliyun.com
   > failovermethod=priority
   > baseurl=http://mirrors.aliyun.com/centos/7/centosplus/\$basearch/
   > gpgcheck=1
   > enabled=0
   > gpgkey=http://mirrors.aliyun.com/centos/RPM-GPG-KEY-CentOS-7
   > 
   > #contrib - packages by Centos Users
   > [contrib]
   > name=CentOS-7 - Contrib - mirrors.aliyun.com
   > failovermethod=priority
   > baseurl=http://mirrors.aliyun.com/centos/7/contrib/\$basearch/
   > gpgcheck=1
   > enabled=0
   > gpgkey=http://mirrors.aliyun.com/centos/RPM-GPG-KEY-CentOS-7
   > EOF
   > ```

2. 安装KVM相关软件包：`yum install libvirt virt-install qemu-kvm -y`

3. 启动服务：

   ```bash
   systemctl start libvirtd.service
   systemctl status libvirtd.service
   systemctl enable libvirtd.service  #设置开机自启
   ```

4. KVM安装VM：





















