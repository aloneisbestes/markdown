# socket 头文件

网络套接字头文件

**linux环境**

```c++
#include <sys/socket>
```

### socket 函数

#### 1. 函数原型

```c++
int socket(int domain, int type, int protocol);
```

*   domain: 为地址族，常用的有 `AF_INET` (ipv4)和 `AF_INET6`(ipv6)

*   type: 数据传输方式/套接字类型，常用的有 SOCK_STREAM（流格式套接字/面向连接的套接字） 和 SOCK_DGRAM（数据报套接字/无连接的套接字）
*    protocol 表示传输协议，常用的有 IPPROTO_TCP 和 IPPTOTO_UDP，分别表示 TCP 传输协议和 UDP 传输协议。