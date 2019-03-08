# 前端部署文档

## 下载代码

```text
git clone ssh://git@gitlab.chainnova.com:7998/fe-projects/anastatix-motcert-app.git
cd anastatix-motcert-app
```

改后端IP，共四处，搜索后结果如下图

![](../.gitbook/assets/image%20%285%29.png)

修改成新的IP后git push推到代码库

## 编译上传镜像

gitlab配了ci 自动编译镜像并推送到前端组专用的docker hub

## 部署线上

### 登录registry

```text
docker login -u chainnova -p chainnova-fe 120.92.92.23:5000
```

### 拉取镜像

```text
docker pull 120.92.92.23:5000/web-fe-motcert-management:latest
```

### 运行镜像

```text
docker run --privileged -dit -p 30010:80 --name trafic_motcert_nginx 120.92.92.23:5000/web-fe-motcert-management:latest
```

### 查看容器

```text
docker ps -a
```

是否生成容器trafic\_motcert\_nginx

部署成功后，访问http://ip:30010；

例如部署在本地，则访问http://localhost:30010

* 
