#### 多谢T-POT的开源

因为有些包内容下载慢，所以我把自己在虚拟机里安装完成的压缩包上传到了百度网盘。

百度网盘 [戳这里下载]()制作中

虚拟机镜像介绍：

- VMware Workstation 12 pro
- Winrar 5.0
- 完全基于官方安装脚本安装，中途因为要去 docker pull ，太慢了，所以我中断了安装脚本，改用国内的docker镜像源安装完，随后的操作都是手工执行的脚本里的命令。
- 改用密码ssh登录系统（这里只是在测试环境，如果要上生产，还是建议只开启密钥登录），用户名：root，密码：、；用户名：rancher，密码rancher
- https://IP:64297/, 用户名：rancher，密码rancher 登录web控制台
- 所有服务都是开机自动启动。忘记那个快照是ssh改之前还是改之后创建的了，建议自己再创建一个快照。
- 如果需要迁移到生产环境部署，请自行考虑安全加固。

以上包是根据官方脚本安装，未增加其他配置，请放心食用。

以下是官方

# Autoinstall T-Pot on Ubuntu 16.04.x 
This script will install [T-Pot 16.10](http://dtag-dev-sec.github.io/mediator/feature/2016/10/31/t-pot-16.10.html) on a fresh Ubuntu 16.04.x LTS (64bit). 

It is intended to be used on hosted servers, where an Ubuntu base image is given and there is no ability to install custom ISO images. 
Successfully tested on vanilla Ubuntu 16.04.1 in VMware.

Choose Ubuntu 16.04.x 64bit as operating system. Make sure you have your SSH key added to your account (~/.ssh/authorized_keys) 
and meet the [system requirements](http://dtag-dev-sec.github.io/mediator/feature/2016/10/31/t-pot-16.10.html#requirements) (>=4GB RAM, 64GB disk, network exposure) for a full T-Pot instance. The system requirements depend on the flavour of T-Pot you intend to run. 

During setup, you can choose from four different configurations: T-Pot's standard installation, industrial edition, full installation and, in case you have limited ressources, you can opt for a "honeypot only"-mode during install, which will install T-Pot without suricata and ELK dashboard (>=3GB RAM required). 

So, clone the repository. Run as root. Enjoy.

    git clone https://github.com/dtag-dev-sec/t-pot-autoinstall.git
    cd t-pot-autoinstall/
    sudo su
    ./install.sh
    
The docker container status is periodically written to ~/docker-status, so you can check if everything is running. 

If you run into problems during installation it might be related to your hoster's custom Ubuntu update repositories. So far, we do not have a solution for this. 

In case you have *very limited resources*, you can still run last year's “*honeypot-only*”-version, which lacks the suricata and kibana dashboard (ELK) component but runs just fine on lower equipped machines with just 1GB of RAM. Therefore, select the previous versions by using the branch *16.03* or *15.03*. Just add a ` -b 15.03` to the `git clone` command. More info [here](https://github.com/dtag-dev-sec/t-pot-autoinstall/tree/15.03). But of course you will miss the [aweseome new features](http://dtag-dev-sec.github.io/mediator/feature/2016/10/31/t-pot-16.10.html#changelog) of T-Pot 16.10.
