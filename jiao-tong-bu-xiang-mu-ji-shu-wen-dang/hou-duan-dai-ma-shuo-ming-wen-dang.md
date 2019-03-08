# 后端代码说明文档

## 根目录说明

![](../.gitbook/assets/image%20%2817%29.png)

* app----------------------本目录下存放fabric应用层的后端服务代码
* files---------------------本目录下临时存放下载文件时从区块链上查询到的pdf文件
* fixtures----------------本目录下存放fabric网络所需的docker配置文件、生成的加密文件、生成加密文件的工具、生成加密文件的相关脚本、fabric配置区块的配置文件、加密配置文件
* .gitignore-------------本文件是git的管理文件之一
* Makefile--------------本文件是make命令的代码文件
* Readme.md--------本文件是一个简略的项目介绍文件，记录了简单的流程不如本文档记录的全面
* appserver.yaml---本文件是本应用的后端服务配置文件
* config.yaml---------本文件是本应用作为fabric应用层的配置文件
* glossary.md--------本文件是本应用相关项目的相关业务术语的字典文件
* swagger.json------本文件是提供给前端的接口文档json版，可以用editor.swagger.io打开
* swagger.yaml-----本文件是提供给前端的接口文档yaml版，可以用editor.swagger.io打开

## app目录说明

![](../.gitbook/assets/image%20%2816%29.png)

* business---------------本目录存放业务逻辑处理的代码，主要包含证书数据的增改查，和一些业务判断，逻辑处理。
* chaincode-------------本目录存放智能合约，会被安装到fabric网络节点中，运行在专用容器里。
* fabricClient-----------本目录存放的代码负责和fabric网络交互，集中存放了和fabric相关的代码，包含对fabric sdk接口的直接调用。
* files-----------------------本目录和../files文件夹重复，不应该存在应该删掉。
* session-----------------本目录存放和服务会话管理有关的代码。
* tempUploadFiles--本目录临时存放从前端上传到后端的文件，然后会从本目录往区块链上存储。
* vendor------------------本目录存放本项目依赖的所有第三方库，除了golang的底层依赖之外的其他所有依赖都在本目录包含了，另外没有再依赖GOPATH下其他的包，如果新的开发需要依赖新的包也应该移动到本目录之下，本目录甚至包含了fabric完整的代码。
* app-----------------------本文件是在ubuntu16.04系统下通过go环境编译出来的二进制可执行文件，是在app/目录下执行"go build ."或者“go build main.go”得到的。
* app.file-----------------本文件同app，是在ubuntu16.04系统下通过go环境编译出来的二进制可执行文件，由于项目make clean的时候会把app删除，所以使用app.file备份。
* app.go-----------------本文件和其他同目录的go文件都属于main package，本文件的代码主要负责接收http 请求路由到具体的响应方法，然后反馈http响应，内含一个http后台服务。
* app\_test.go---------本文件是app.go的单元测试文件，实际没有实现。
* benchmark.go-----本文件目标实现性能自测功能，实际没有实现。
* server.go--------------本文件含有main package的main方法，是程序的入口，负责创建fabric sdk 相关对象，负责启动后端服务。
* version.go------------本文件负责软件版本管理。

## fixtures目录说明

![](../.gitbook/assets/image%20%2823%29.png)

* artifacts----------------本目录存放创世区块文件、channel tx文件等
* bin-------------------------本目录存放可以在ubuntu16.04下执行的可执行文件configtxgen、cryptogen，这两个文件用来生channel tx文件、创世区块文件、加密文件
* bin-mac------------------本目录同bin，不同的是存放的是macOS之下可执行的文件configtxgen、cryptogen
* certificates-------------本目录存放本应用后端和前端之间使用https时所需的证书和密钥。
* crypto-config----------本目录存放cryptogen工具生成的密钥和证书
* configtx.yaml----------本文件为通道配置文件
* crypto-config.yaml--本文件是cryptogen执行时参考的配置文件
* docker-compose.yaml----本文件是fabric网络所需的docker配置文件
* generate.sh-------------本文件是生成证书、密钥、tx文件、创世区块的脚本文件

