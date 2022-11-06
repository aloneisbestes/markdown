# unistd头文件使用

### access 函数断言

#### 1. 函数原型

```c++
int access(const char *pathname,int mode)
```

*   pathname:表示要测试的文件的路径
*   mode:表示测试的模式可能的值有:
    *   R_OK:是否具有读权限
    *   W_OK:是否具有可写权限
    *    X_OK:是否具有可执行权限
    *    F_OK:文件是否存在

#### 2. 返回值

若测试成功则返回0,否则返回-1