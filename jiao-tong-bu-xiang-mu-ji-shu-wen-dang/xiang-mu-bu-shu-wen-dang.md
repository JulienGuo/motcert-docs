# 后端部署文档

## 准备服务器

1. 登录aws，创建一台云主机。
2. 建议配置：
   1. 4核CPU
   2. 16G内存
   3. 40G存储
   4. OS ubuntu 16.04
   5. 网络端口建议全部开通，不设限制。

## 初次登入服务器

```
sudo su
mkdir -p /opt/gopath/src/gitlab.chainnova.com
cd /opt/gopath/src/gitlab.chainnova.com
```

生成git ssh key，执行如下命令

```text
ssh-keygen
```

连续回车三次，控制台输出如下图

![](../.gitbook/assets/image%20%283%29.png)

 输出ssh key公钥

```text
cat ~/.ssh/id_rsa.pub
```

 控制台输出内容如下

![](../.gitbook/assets/image%20%282%29.png)

拷贝输出等公钥，添加到[https://gitlab.chainnova.com/profile/keys](https://gitlab.chainnova.com/profile/keys)

![](../.gitbook/assets/image%20%289%29.png)

## 下载代码

登录服务器，然后执行以下命令

```text
cd /opt/gopath/src/gitlab.chainnova.com
git clone ssh://git@gitlab.chainnova.com:7998/if/motcert-backend.git
yes
cd motcert-backend/
git checkout -b local dev-1.4.2
git pull origin dev-1.4.2:local
```

## 安装docker 环境

### 安装docker-compose 

参考链接：[https://github.com/docker/compose/releases](https://github.com/docker/compose/releases)

```text
curl -L https://github.com/docker/compose/releases/download/1.23.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```

### 安装docker

参考链接：[https://docs.docker.com/install/linux/docker-ce/ubuntu/\#os-requirements](https://docs.docker.com/install/linux/docker-ce/ubuntu/#os-requirements)

如果有旧的版本，先删除，命令如下：

```text
apt-get remove docker docker-engine docker.io containerd runc
```

安装命令如下：

```text
apt-get update
apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
Y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
apt-key fingerprint 0EBFCD88
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
apt-get update
apt-get install docker-ce docker-ce-cli containerd.io
Y
docker run hello-world
usermod -aG docker $USER
chmod -R 777 /var
systemctl enable docker
sudo reboot
```

## 安装aws cli

参考：[https://docs.amazonaws.cn/cli/latest/userguide/install-linux.html](https://docs.amazonaws.cn/cli/latest/userguide/install-linux.html)

```text
curl -O https://bootstrap.pypa.io/get-pip.py
python3 get-pip.py --user
```

编辑环境变量配置脚本：

```text
vim ~/.bashrc
```

在文件最后录入：

```text
export PATH=~/.local/bin:$PATH
```

保存.bashrc，更新当前shell的配置：

```text
source ~/.bashrc
```

使用pip安装 AWS CLI

```text
pip install awscli --upgrade --user
aws --version
pip install awscli --upgrade --user
```

## 登录aws ecr dockerhub账户

执行配置命令：

```text
aws configure
```

输入从aws获得的相应ID和Key，如无则联系本机构账户的管理员

![](../.gitbook/assets/image%20%2822%29.png)

登录

```text
$(aws ecr get-login --no-include-email --region cn-north-1)
```

## 拉取需要的 docker images

拉取镜像

```text
docker pull hyperledger/fabric-ccenv:amd64-1.4.2
docker pull hyperledger/fabric-orderer:amd64-1.4.2
docker pull hyperledger/fabric-peer:amd64-1.4.2
docker pull hyperledger/fabric-ca:amd64-1.4.2
docker pull hyperledger/fabric-couchdb:amd64-0.4.15
```

## 启动Fabric网络

```text
cd /opt/gopath/src/gitlab.chainnova.com/motcert-backend/fixtures
docker-compose up &
```

## 启动项目后端服务

建议打开新的终端执行：

设置GOPATH环境变量，可以不具备Golang编译环境，但是要设置GOPATH变量

编辑环境变量配置脚本

```text
sudo su
vim ~/.bashrc
```

在文件最后录入

```text
export GOPATH=/opt/gopath
```

保存.bashrc，更新当前shell的配置

```text
source ~/.bashrc
```

启动service

```text
cd /opt/gopath/src/gitlab.chainnova.com/motcert-backend/app
cp app.file app
./app start &
```

到测试文档界面测试当前服务是否正常运转。

## 保存镜像快照

为了方便下次部署可以将当前云服务器在控制台界面保存为镜像快照，下次部署新的机器可以免去安装docker等工具软件的过程

![](../.gitbook/assets/image%20%2837%29.png)



保存后在IMAGES--&gt;AMIs可以浏览到，选中后点击Launch可以根据镜像创建新的云主机，这时得到的新主机软件环境已经具备上文安装的所有内容。

![](../.gitbook/assets/image%20%2823%29.png)



