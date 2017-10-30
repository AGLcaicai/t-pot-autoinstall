#### 感谢[T-POT](https://github.com/dtag-dev-sec/t-pot-autoinstall)

```
#####################################################################
# 仅限中国网使用，加速都是针对中国的，国外会减速
# This script is used for ubuntu16.04 in China!!!!!!
# If you are out of the GFW,It's sloooooooooooooooooooooooooooooow
# 1、修改Ubuntu源为中国镜像
# 2、修改pip安装源为douban
# 3、修改npm安装源为taobao
# 4、修改git源为coding
# 5、docker增加aliyun mirror
#####################################################################

```

以下两个安装脚本在ubuntu16.04 与ubuntu16.10系统测试通过

 [ubuntu16.04](https://github.com/n3uz/t-pot-autoinstall/blob/master/install_ubuntu16.04.sh)   |   [ubuntu16.10](https://github.com/n3uz/t-pot-autoinstall/blob/master/install_ubuntu16.10.sh)

## 部署前置条件
- root运行安装脚本
- 准备普通用户，并为普通用户创建公私钥，用于密钥登录。

以普通用户z为例

```
z@ubuntu:~$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/z/.ssh/id_rsa):
Created directory '/home/z/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/z/.ssh/id_rsa.
Your public key has been saved in /home/z/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:ZEVXpFGTbX+e/RoGkF/XxN9McBKt7MUvaZxAZ7XL/Tw z@ubuntu
The key's randomart image is:
+---[RSA 2048]----+
|         .o o+OO+|
|         . o.o+=O|
|        o o..+.B*|
|       o   o..+.@|
|        S   o+ B*|
|             .Bo=|
|             .oE+|
|             . .o|
|              .. |
+----[SHA256]-----+

z@ubuntu:~$ ls -la ./.ssh
total 16
drwx------ 2 z z 4096 Oct 26 14:56 .
drwxr-xr-x 4 z z 4096 Oct 26 14:56 ..
-rw------- 1 z z 1766 Oct 26 14:56 id_rsa
-rw-r--r-- 1 z z  390 Oct 26 14:56 id_rsa.pub

```
添加公钥
```
z@ubuntu:~$ cat /home/z/.ssh/id_rsa.pub >> /home/z/.ssh/authorized_keys
```
保存私钥/home/z/.ssh/id_rsa 文件，用于后面的登录。


##  脚本修改内容

#### 1、替换ubuntu中文源

cn.ubuntu

#### 2、pip使用豆瓣源


```
pip install alerta -i http://pypi.douban.com/simple --trusted-host pypi.douban.com
```

#### 3、npm使用淘宝源

```
npm --registry https://registry.npm.taobao.org install https://github.com/t3chn0m4g3/wetty -g
```

#### 4、git 代码搬运到coding

https://git.coding.net/n3uz/tpotce-16.10.git

#### 5、docker增加了aliyun的docker mirror
```
fuECHO "### Patching docker using aliyun mirrors."
tee -a /etc/docker/daemon.json <<EOF
{
  "registry-mirrors": ["https://4432scbk.mirror.aliyuncs.com"]
}
EOF
```

## 如果安装过程中遇到 “Hash Sum mismatch”错误，请自行更换脚本中另外的源

如下是ubuntu16.10 使用163的源
```
cat > /etc/apt/sources.list << EOF
deb http://mirrors.163.com/ubuntu/ yakkety main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ yakkety-security main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ yakkety-updates main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ yakkety-backports main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ yakkety-proposed main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ yakkety main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ yakkety-security main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ yakkety-updates main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ yakkety-backports main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ yakkety-proposed main restricted universe multiverse
EOF
```

源地址请参考 [ubuntu 源列表](http://wiki.ubuntu.org.cn/%E6%BA%90%E5%88%97%E8%A1%A8)


--完--
