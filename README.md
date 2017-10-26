#### 感谢[T-POT](https://github.com/dtag-dev-sec/t-pot-autoinstall)

# 正在调试中---2017-10-26

本脚本针对中国区调整加速！！！，境外使用肯定会减速！！！！

#### USED WITHIN THE CHINESE GFW !!! YOU FREE COUNTRY WILL SLOOOOOOOOOOOOOOOOOOOOOOOOOOW!!!

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

## 安装过程中要去git clone 代码回来，有点慢，需要等等

TODO 把代码克隆到coding

##  脚本修改内容

#### 替换ubuntu中文源


#### pip使用豆瓣源、npm使用淘宝源

```
pip install alerta -i http://pypi.douban.com/simple --trusted-host pypi.douban.com
npm --registry https://registry.npm.taobao.org install https://github.com/t3chn0m4g3/wetty -g
```

#### docker增加了aliyun的docker mirror
```
fuECHO "### Patching docker using aliyun mirrors."
tee -a /etc/docker/daemon.json <<EOF
{
  "registry-mirrors": ["https://4432scbk.mirror.aliyuncs.com"]
}
EOF
```

tpot 官方
