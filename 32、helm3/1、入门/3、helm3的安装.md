## helm3的安装



#### 1、下载自己需要的helm3的版本安装包

- 方式1：下载源码编译安装，下载地址：https://github.com/helm/helm/tags
- 方式2：下载二进制包，直接使用，下载地址：https://get.helm.sh/helm-v3.0.0-linux-amd64.tar.gz



#### 2、解压缩下载的安装包

```shell
tar -zxvf helm-3.1.3.tar.gz
```



#### 3、移动解压出来的helm，完成安装

```shell
mv linux-amd64/helm /usr/local/bin/
```



#### 4、安装验证

```shell
helm version
```

