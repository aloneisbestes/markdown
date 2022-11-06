# ssh免密登录 linux-linux

## 1. 生成秘钥

客户端生成公私钥

本地客户端生成公私钥：（一路回车默认即可）

``` shell
ssh-keygen
```

## 2. 上传秘钥到服务器

这里测试用的服务器地址为：aloneisbestes.cn
用户为：alone

```shell
ssh-copy-id -i ~/.ssh/id_rsa.pub alone@aloneisbestes.cn
```

## 3.测试免密登录

客户端通过ssh连接远程服务器，就可以免密登录了。

``` shell
ssh alone@aloneisbestes.cn
```

