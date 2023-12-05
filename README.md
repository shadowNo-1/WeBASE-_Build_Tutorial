# WeBASE-_Build_Tutorial
WeBASE _Build_Tutorial
This is [shadowNo-1](https://github.com/shadowNo-1)'s private note

[![Author](https://img.shields.io/badge/author-shadowNo--1-informational?style=flat&logo=github&logoColor=181717&color=green)](https://github.com/shadowNo-1)
![](https://img.shields.io/badge/license-GNU-informational?style=flat&logo=gnu&logoColor=white&color=A42E2B)
![Java](https://is.gd/QQflSA)

## WeBASE版本说明

## 基础环境配置
### 安装Java14
- 更新apt
  ```bash
  sudo apt update
  ```
- 下载Java14
  ```bash
  curl -O https://download.java.net/java/GA/jdk14/076bab302c7b4508975440c56f6cc26a/36/GPL/openjdk-14_linux-x64_bin.tar.gz
  ```
- 解压缩
  ```bash
  sudo tar xvf openjdk-14_linux-x64_bin.tar.gz
  ```
- 将解压后的`jdk-14`目录移动到`opt`目录下
  ```bash
  sudo mv jdk-14/ /opt/
  ```
- 执行下列`tee`命令，配置环境变量
  ```bash
  sudo tee /etc/profile.d/jdk14.sh <<EOF
  ```
- 配置环境变量
  ```bash
  > export JAVA_HOME=/opt/jdk-14
  > export PATH=\$PATH:\$JAVA_HOME/bin
  > EOF
  ```
  ![image](https://github.com/shadowNo-1/WeBASE-_Build_Tutorial/assets/61909905/b89239b3-05cc-4f87-ba06-f7a2a7d17017)
- 应用配置文件
  ```bash
  source /etc/profile.d/jdk14.sh
  ```
- 输入下列命令，查看jdk路径
  ```bash
  echo $JAVA_HOME
  ```
  ![image](https://github.com/shadowNo-1/WeBASE-_Build_Tutorial/assets/61909905/39f1f5ab-b098-4bde-96e1-b6fe285e77f5)



## 节点前置服务搭建
  1.下载安装包
  ```bash
  wget https://osp-1257653870.cos.ap-guangzhou.myqcloud.com/WeBASE/releases/download/v1.5.5/webase-front.zip
  ```
  2.解压文件
  ```bash
  unzip webase-front.zip
  ```
  3.进入解压后的目录
  ```bash
  cd webase-front
  ```
  4.拷贝sdk证书文件（build_chain的时候生成的）
  将节点所在目录`nodes/${ip}/sdk`下的所有文件拷贝到当前`conf`目录，供SDK与节点建立连接时使用（SDK会自动判断是否为国密，且是否使用国密SSL）
    - 链的sdk目录包含了`ca.crt`, `sdk.crt`, `sdk.key`和`gm`文件夹，`gm`文件夹包含了国密SSL所需的证书
    - 拷贝命令可使用`cp -r nodes/${ip}/sdk/* ./conf/`
    - 注，只有在建链时手动指定了`-G`(大写)时节点才会使用国密SSL
  若按照[](https://github.com/shadowNo-1/FISCO-BCOS_Build_Tutorial/)搭建说明搭建，复制命令可参考下列案例，使用此命令是你应处于`webase-front`目录下
  ```bash
  cp -r ~/fisco/nodes/127.0.0.1/sdk/* ./conf/
  ```
