# cmake

## cmake 的安装

### 1. mac 环境下

``` shell
brew install cmake
```

## cmake 的使用

**cmake_minimum_required**

*   CMake 最低版本号要求

*   ```cmake
    cmake_minimum_required(VERSION 3.0)
    ```

**project**

*   设置项目名

*   ```cmake
    project(Demo1)
    ```

**PROJECT_SOURCE_DIR**

*   项目的顶级目录

**add_subdirectory**

*   添加子目录，这样子目录中的CMakeLists.txt才会被调用

*   ```cmake
    add_subdirectory(common)
    # common 子目录
    ```

**message**

*   打印信息

*   ``` cmake
    message("project_dir:" ${PROJECT_SOURCE_DIR})
    ```

**include_directories**

*   添加头文件所在目录

*   ```bash
    include_directories("${PROJECT_SOURCE_DIR}/common")
    ```

**aux_source_directory**

*   将指定目录下的所有文件名保存到指定的变量中

*   ```cmake
    aux_source_directory(./src DIR_SRCS)
    ```

**add_definitions**

*   消除编译链接时的警告

*   ``` cmake
    add_definitions(-w)
    ```

**add_executable**

*   生成可执行文件

*   ```cmake
    add_executable(httpserver ${ALL_SRC})
    ```

**target_link_libraries**

*   添加外部链接库

*   ```cmake
    target_link_libraries(mgraccount jsoncpp)
    ```

