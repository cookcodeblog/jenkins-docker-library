[TOC]

# jenkins-docker-library
Jenkins docker images

## 在阿里云上新建镜像仓库

打开阿里云容器镜像服务：https://cr.console.aliyun.com ， 新建一个镜像仓库。

1. 选择离自己比较近的区域

2. 按提示填写信息

3. 选择”代码变更时自动构建镜像“和”海外机器构建“，并填写构建信息，比如：


```
代码分支：branches:master
Dockerfile目录：/cloudbees/jnlp-slave-with-java-build-toolst/latest
Dockerfile文件名：Dockerfile
镜像版本：latest
```




## 构建、拉取镜像和重新打标签

 1. 点击【管理】，选择【构建】，点击【立即构建】
 2. 构建成功后，在【基础信息】中查看用法
 3. 拉取新构建成功的镜像
 4. 重新打标签
 
 ```bash
 # 拉取新构建的镜像
docker pull registry.cn-shenzhen.aliyuncs.com/cookcodeblog/jnlp-slave-with-java-build-tools:latest
# 打上gcr.io同名标签
docker tag registry.cn-shenzhen.aliyuncs.com/cookcodeblog/jnlp-slave-with-java-build-tools:latest jnlp-slave-with-java-build-tools:latest
# 查看镜像
docker images
# 删除新构建的镜像，只保留gcr.io镜像
docker rmi registry.cn-shenzhen.aliyuncs.com/cookcodeblog/jnlp-slave-with-java-build-tools:latest
# 再次查看镜像
docker images
```
