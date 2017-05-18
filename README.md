#### 多谢T-POT的开源

因为有些包内容下载慢，所以我把自己在虚拟机里安装完成的压缩包上传到了百度网盘。

百度网盘 [戳这里下载]()制作中

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
