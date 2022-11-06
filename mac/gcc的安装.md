# gcc的安装
## 1. gcc 下载地址
```
https://sourceforge.net/projects/hpc/files/hpc/gcc/
```
## 2. 解压

```shell
gunzip gcc-9.2-bin.tar.gz
tar -xvf gcc-9.2-bin.tar
```
## 3. 选择存放位置
```shell
# 创建一个安装位置。例如这里将其安装到  /usr/local/gcc-9.2 下
sudo mkdir /usr/local/gcc-9.2

# 将解压的文件移到安装文件夹下
sudo mv usr/local/* /usr/local/gcc-9.2/
```
## 4. 查看路径下是否有文件
```shell
ls -al /usr/local/gcc-9.2
```
## 5. 配置环境变量
```shell
vim ~/.bash_profile
# 在配置文件中添加如下配置
export GCC_HOME=/usr/local/gcc-9.2/
export PATH=$PATH:$GCC_HOME/bin
# 使用下面命令让文件立即生效
source ~/.bash_profile
```
