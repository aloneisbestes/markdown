# Lua 环境安装

## Linux 系统上安装

Linux & Mac上安装 Lua 安装非常简单，只需要下载源码包并在终端解压编译即可，本文使用了5.3.0版本进行安装：

```sh
curl -R -O http://www.lua.org/ftp/lua-5.3.0.tar.gz
tar zxf lua-5.3.0.tar.gz
cd lua-5.3.0
make linux test
make install
```

## Mac OS X 系统上安装

```sh
curl -R -O http://www.lua.org/ftp/lua-5.3.0.tar.gz
tar zxf lua-5.3.0.tar.gz
cd lua-5.3.0
make macosx test
make install
```

## Windows 系统上安装

window下你可以使用一个叫"SciTE"的IDE环境来执行lua程序，下载地址为：

-   Github 下载地址：https://github.com/rjpcomputing/luaforwindows/releases

双击安装后即可在该环境下编写 Lua 程序并运行。

你也可以使用 Lua 官方推荐的方法使用 LuaDist：[http://luadist.org/](https://luadist.org/)

