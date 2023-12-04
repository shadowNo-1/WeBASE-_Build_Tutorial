# WeBASE-_Build_Tutorial
WeBASE _Build_Tutorial
## 快速入门搭建
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
