# 运维文档

## 更新后端服务配置

进入项目后端服务代码根目录

```text
cd /opt/gopath/src/gitlab.chainnova.com/motcert-backend
apt update
apt install tree
tree -L 1
```

查看一级目录的内容

```text
tree -L 1
```

输出内容：

![](../.gitbook/assets/image%20%287%29.png)

#### 配置更新后重启后端服务即可

先找到已经运行的后端服务

```text
netstat -ntlp
```

输出结果如下图：

![](../.gitbook/assets/image%20%2830%29.png)

杀死该后端服务的进程

```text
kill -9 2756
```

重新启动新的后端服务

```text
cd /opt/gopath/src/gitlab.chainnova.com/motcert-backend/app
./app update &
```

## 更新后端服务代码逻辑

运维不包含代码的开发工作，只负责新开发的内容在生产环境发布。

假设更新代码即可得到新版代码编译出来的二进制可执行文件 app.file，将app.file重命名为app，然后重启。命令如下：    

```text
cd /opt/gopath/src/gitlab.chainnova.com/motcert-backend/app
git pull origin dev-1.0.0:local
cp app.file app
netstat -ntlp
kill -9 [此处为旧的进程号]
./app update &
```

## 更新（升级）智能合约代码

运维不包含智能合约代码的开发工作，只负责新合约在生产环境发布。

假设更新代码即可得到新版智能合约代码，在目录chaincode目录覆盖旧智能合约代码的位置，由于智能合约的变化一般会伴随后端服务代码的更新，所以假设更新代码后新版代码编译出来的二进制可执行文件 app.file也是新版。

那么升级操作命令如下：

```text
cd /opt/gopath/src/gitlab.chainnova.com/motcert-backend/app
git pull origin dev-1.0.0:local
cp app.file app
netstat -ntlp
kill -9 [此处为旧的进程号]
./app upgrade &
```

## 更新Fabric网络结构

更新fabric网络结构有四种办法：

1、使用fabric的互操作性功能，但是这个功能还没有开发完毕

2、使用目前支持的手动模式更新，这需要一些繁琐的手工操作

3、使用BaaS平台，这个也没有绿色可用的选择

4、小型网络可以采取停止整个网络，更新网络配置文件，重启

当前项目采取第4种办法，执行命令如下：

```text
netstat -ntlp
kill -9 [此处为旧的进程号]
cd /opt/gopath/src/gitlab.chainnova.com/motcert-backend
apt install make
make clean
git pull origin dev-1.0.0:local
cd fixtures
docker-compose up &
```

换一个终端，如果没有更新智能合约，则使用如下命令重启服务：

```text
sudo su
cd /opt/gopath/src/gitlab.chainnova.com/motcert-backend/app
cp app.file app
./app update &
```

换一个终端，如果智能合约有变化，则使用如下命令重启服务：

```text
sudo su
cd /opt/gopath/src/gitlab.chainnova.com/motcert-backend/app
cp app.file app
./app upgrate &
```

换一个终端，如果原fabric网络的数据已经全部被清除，则使用如下命令重启服务：

```text
sudo su
cd /opt/gopath/src/gitlab.chainnova.com/motcert-backend/app
cp app.file app
./app start &
```

## 网络节点数据备份处理

当停止fabric网络时我们使用了make clean命令

查看一下Makefile的内容：

```text
root@ip-172-31-14-164:/opt/gopath/src/gitlab.chainnova.com/motcert-backend# cat Makefile 
.PHONY: all dev clean build env-up env-down run

all: clean build env-up run

dev: build run

##### BUILD
build:
        @echo "Build ..."
        @dep ensure
        @go build
        @echo "Build done"

##### ENV
env-up:
        @echo "Start environment ..."
        @cd fixtures && docker-compose up --force-recreate -d
        @echo "Environment up"

env-down:
        @echo "Stop environment ..."
        @echo "Copy CouchDB First !"
#       @exit 1
        @cd fixtures && docker-compose down
        @echo "Environment down"

##### RUN
run:
        @echo "Start app ..."
        @./app

##### CLEAN
clean: env-down
        @echo "Clean up ..."
        @rm -rf ~/motcert-network-backup
        @cp -rf ~/motcert-network ~/motcert-network-backup
        @rm -rf /tmp/motcert-* ./app/app
        @docker rm -f -v `docker ps -a --no-trunc | grep "motcert" | cut -d ' ' -f 1` 2>/dev/null || true
        @docker rmi `docker images --no-trunc | grep "motcert" | cut -d ' ' -f 1` 2>/dev/null || true
        @echo "Clean up done"
```

在fixtures/docker-compose.yaml里面fabric网络的数据被映射到了~/motcert-network，

当make clean停止整个网络的时候，~/motcert-network被备份到了~/motcert-network-backup

## couchdb的自身复制机制

couchdb提供的自身复制机制可以备份状态数据库。不过，这一步不是必须的，即使没有备份couchdb，fabric网络的数据也已经备份。

本例我们把couchdb0容器部署在了52.82.20.13云主机上，端口映射了7184，那么登录[http://52.82.20.13:7184/\_utils/\#](http://52.82.20.13:7184/_utils/#) 

页面如下图

![](../.gitbook/assets/image%20%2833%29.png)

如下图选择的标签页即是couchdb客户端提供的复制操作界面，具体用法参考couchdb官方文档

![](../.gitbook/assets/image%20%2829%29.png)



