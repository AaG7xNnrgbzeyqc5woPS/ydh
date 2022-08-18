# See(需要翻墙才能看):
 - [如何翻墙？——写在 BlogSpot 被封之后 {2018-12-26}](https://program-think.blogspot.com/2009/05/how-to-break-through-gfw.html)
 - [常见翻墙问题答疑 {2012-02-13}](https://program-think.blogspot.com/2011/09/gfw-faq.html)
 - [“如何翻墙”系列：获取翻墙软件方法大全](https://program-think.blogspot.com/2011/03/how-to-get-gfw-tools.html)
 - [多台电脑如何【共享】翻墙通道——兼谈【端口转发】的几种方法](https://program-think.blogspot.com/2013/01/cross-host-use-gfw-tool.html)
 - [学习一下德国人民的翻墙精神](https://program-think.blogspot.com/2009/07/break-through-berlin-wall.html)

# See(翻墙):
 - [如何保护隐私[0]：为啥写这个话题？](https://program-think.blogspot.com/2013/06/privacy-protection-0.html)
 - ❤️ [如何保护隐私[1]：如何选择软件和服务？](https://program-think.blogspot.com/2013/06/privacy-protection-1.html)
 - [全国公安工作信息化工程](https://zh.wikipedia.org/wiki/%E5%85%A8%E5%9B%BD%E5%85%AC%E5%AE%89%E5%B7%A5%E4%BD%9C%E4%BF%A1%E6%81%AF%E5%8C%96%E5%B7%A5%E7%A8%8B)
 - [中美政府信息监控的差异——“棱镜门”丑闻随想](https://program-think.blogspot.com/2013/06/usa-vs-china.html)
 - [粉碎棱镜](https://prism-break.org/en/)
 - [如何保护隐私[8]：流氓的桌面软件有哪些替代品？](https://program-think.blogspot.com/2014/08/privacy-protection-8.html)
 - [为什么桌面系统装 Linux 可以做到更好的安全性（相比 Windows ＆ macOS 而言）](https://program-think.blogspot.com/2017/03/Why-Linux-Is-More-Secure-Than-Windows-and-macOS.html)

# See:
 - ❤️ [BreakWall-Summary/2021.11/](https://github.com/AaG7xNnrgbzeyqc5woPS/BreakWall-Summary/tree/main/2021.11)
  
# 1. 安装docker(zorin os desktop)
 - [linux_help/docker_install/](https://github.com/AaG7xNnrgbzeyqc5woPS/linux_help/tree/master/docker_install)

## 1.1 看 docker 是否安装
```
john@john-TM1613:~$ docker info
Command 'docker' not found, but can be installed with:

sudo snap install docker     # version 20.10.14, or
sudo apt  install docker.io  # version 20.10.12-0ubuntu2~20.04.1

See 'snap info docker' for additional versions.

```

## 1.2 选择apt安装

```
sudo apt  install docker.io

```

**注释:** 第一次不成功,再安装一次就成功了。好像是网络无稳定，导致有些网站访问失败

## 1.3 upgrade 整个系统
```
sudo apt update
sudo apt upgrade
```

**注释:** 这一步可以先做一遍，更好！今天忘记做了

## 1.4 查看docker

```
docker info
sudo docker info
```
安装成功！

## 1.5 授权 
```
   # sudo usermod -aG  docker john      #指定具体用户
   sudo usermod -aG docker $(whoami)    #自动找到当前用户
   reboot # 重启电脑，授权才生效
```

## 1.6 测试
```
docker info
docker version
docker --version

docker run hello-world
```

# 2 docker-compose 安装
```
sudo curl -L https://github.com/docker/compose/releases/download/v2.9.0/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
```
```
sudo chmod +x /usr/local/bin/docker-compose
```
```
docker-compose --version
```

# 3 trojan-go client install
- [ p4gefau1t/trojan-go ](https://github.com/p4gefau1t/trojan-go)
- [BreakWall-Summary/2021.11/](https://github.com/AaG7xNnrgbzeyqc5woPS/BreakWall-Summary/tree/main/2021.11)


## 3.1 ❤️ 服务器端使用的是:  XRay_Trojan_Docker
 ssh 登录服务器，获取密码
 ```
 root@John:~# ls
XRay_Trojan_Docker  tcp.sh
root@John:~# cd XRay_Trojan_Docker/
root@John:~/XRay_Trojan_Docker# ls
Makefile  OneKeySet.sh  README.md  caddy  docker-compose.yml  info.txt  xray
root@John:~/XRay_Trojan_Docker# cat info.txt 
-----------------------------------------------
XRay Configuration:

VLESS:
Server: w1.bigbang.monster
Port: 443
UUID: 96dca993-6a87-4a38-8386-eaa87b40a9da

VMESS:
AlterId: 64
WebSocket Host: w1.bigbang.monster
WebSocket Path: /ray
TLS: True
TLS Host: w1.bigbang.monster
-----------------------------------------------
Trojan Configuration:
Server: w1.bigbang.monster
Port: 443
Password: eaa87b40a9da
-----------------------------------------------
root@John:~/XRay_Trojan_Docker# 

 ```
 只看 Trojan Configuration，目前我们客户端用 trojan
 
 ## 3.2 创建客户端配置文件
 ```
 cd 
 mkdir .trojan-go
 cd .trojan-go
 nano config.yaml             #输入配置文件，格式和内容如下
john@john-TM1613:~/.trojan-go$ cat config.yaml # 显示配置文件
run-type: client
local-addr: 127.0.0.1
local-port: 1080
remote-addr: w1.bigbang.monster
remote-port: 443
password: 
 - eaa87b40a9da
john@john-TM1613:~/.trojan-go$ 

 ```
 ❤️获取配置文件路径，确认配置文件正确
 ```
 john@john-TM1613:~$ cd
john@john-TM1613:~$ cd .trojan-go/
john@john-TM1613:~/.trojan-go$ pwd
/home/john/.trojan-go

john@john-TM1613:~/.trojan-go$ ls -l
total 4
-rw-rw-r-- 1 john john 132 8月  10 15:50 config.yaml
john@john-TM1613:~/.trojan-go$ cat config.yaml

 ```
 **在我的电脑是路径是：/home/john/.trojan-go**
 
 # 3.3 启动 docker 容器
 ```
 docker run \
 --name trojan-go \
 -d \
 -v /home/john/.trojan-go:/etc/trojan-go \
 --restart always \
 --network host \
 p4gefau1t/trojan-go \
 /etc/trojan-go/config.yaml 
 ```
 - **注意 -V 参数 要用你电脑的实际路径替代**
 - **启动参数 --restart 有以下几种，no, on-failure, always, unless-stopped**
 - 如果容器启动时没有设置–restart参数，则通过下面命令进行更新：  
 ``` docker update --restart [container] ```
 
 # 3.4 调试 命令
 ```
  docker ps
  docker ps -a
  docker images
  docker logs trojan-go
  docker rm trojan-go
  docker stop trojan-go
  docker start trojan-go
  docker restart trojan-go
 ```
 
# 3.5 调试例子，删除出错的容器
```
john@john-TM1613:~/.trojan-go$ pwd
/home/john/.trojan-go
john@john-TM1613:~/.trojan-go$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
john@john-TM1613:~/.trojan-go$ docker images
REPOSITORY            TAG       IMAGE ID       CREATED         SIZE
hello-world           latest    feb5d9fea6a5   10 months ago   13.3kB
p4gefau1t/trojan-go   latest    0213987ea3da   11 months ago   35.2MB
john@john-TM1613:~/.trojan-go$ docker  ps -a
CONTAINER ID   IMAGE                 COMMAND                  CREATED         STATUS                     PORTS     NAMES
52d90351188f   p4gefau1t/trojan-go   "/usr/local/bin/troj…"   8 minutes ago   Exited (1) 8 minutes ago             trojan-go
f68d8269c5ef   hello-world           "/hello"                 4 hours ago     Exited (0) 4 hours ago               dreamy_jackson
d931f1d39d48   hello-world           "/hello"                 4 hours ago     Exited (0) 4 hours ago               vibrant_pasteur
41062eacb369   hello-world           "/hello"                 4 hours ago     Exited (0) 4 hours ago               zen_lamarr
john@john-TM1613:~/.trojan-go$ docker rm trojan-go
trojan-go
john@john-TM1613:~/.trojan-go$ docker rm hello-world
Error: No such container: hello-world
john@john-TM1613:~/.trojan-go$ docker rm dreamy_jackson vibrant_pasteur zen_lamarr
dreamy_jackson
vibrant_pasteur
zen_lamarr
john@john-TM1613:~/.trojan-go$ docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
john@john-TM1613:~/.trojan-go$ 

```

## 3.6 调试例子2，这次启动成功！
```
john@john-TM1613:~/.trojan-go$ docker run \
>  --name trojan-go \
>  -d \
>  -v /home/john/.trojan-go:/etc/trojan-go \
>  --network host \
>  p4gefau1t/trojan-go \
>  /etc/trojan-go/config.yaml 
48626b6c0c5a76b22e9d37b174bf018776d796697bf789480351d120d5987734
john@john-TM1613:~/.trojan-go$ docker ps -a
CONTAINER ID   IMAGE                 COMMAND                  CREATED         STATUS         PORTS     NAMES
48626b6c0c5a   p4gefau1t/trojan-go   "/usr/local/bin/troj…"   6 seconds ago   Up 5 seconds             trojan-go
john@john-TM1613:~/.trojan-go$ docker logs trojan-go
[INFO]  2022/08/10 08:18:01 trojan-go v0.10.6 initializing
[INFO]  2022/08/10 08:18:01 adapter listening on tcp/udp: 127.0.0.1:1080
[WARN]  2022/08/10 08:18:01 tls sni is unspecified
[INFO]  2022/08/10 08:18:01 cert is unspecified, using default ca list
john@john-TM1613:~/.trojan-go$ 

```


# 4.0 客户端浏览器配置
 ❤️ **浏览器统一使用 firefox，无论是 linux 还是 windows 操作系统**
 
 ## 4.1 firefox 安装插件 Proxy SwitchyOmega
 方法一，浏览器地址栏输入以下地址：
 https://addons.mozilla.org/en-US/firefox/addon/switchyomega/?utm_content=addons-manager-reviews-link&utm_medium=firefox-browser&utm_source=firefox-browser
 
 方法二，about:addons 页面 输入需要搜索的插件：SwitchyOmega，找到  Proxy SwitchyOmega，按照指导安装
 
 ## 4.2  Proxy SwitchyOmega 配置 Options
 修改代理服务器项目  Profile :: proxy：
   Protocol:sock5   Server:127.0.0.1     	Port:1080
   
 ## 4.3 firefox 选择代理服务器配置项 proxy
   - 地址栏右侧，鼠标左键点击蓝色的圆圈图标，出现菜单
   - 在菜单种选择 proxy,圆圈变成蓝色了，现在走代理
   - 选择 direct 圆圈变成灰色，浏览器直连，不走代理。

## 4.4 如何一切都配置好了
  浏览 youtube.com
  google.com
  现在这些外网应该能看到
  https://www.youtube.com/
  https://www.google.com/
  
# 5.0 XRay_Trojan_Docker服务器，域名 w1.bigbang.monster
 - ❤️ 注意该服务器即将到期，失效！
 - 
  ```
  john@john-TM1613:~$ ping w1.bigbang.monster
PING w1.bigbang.monster (202.91.34.168) 56(84) bytes of data.
64 bytes from 202.91.34.168 (202.91.34.168): icmp_seq=1 ttl=53 time=238 ms
64 bytes from 202.91.34.168 (202.91.34.168): icmp_seq=2 ttl=53 time=262 ms
64 bytes from 202.91.34.168 (202.91.34.168): icmp_seq=3 ttl=53 time=181 ms
^C
--- w1.bigbang.monster ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 181.402/227.180/261.944/33.791 ms

  ```
 
 
   
   
