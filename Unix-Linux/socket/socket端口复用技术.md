# 端口复用

**端口复用允许在一个应用程序可以把 n 个套接字绑在一个端口上而不出错。**

### 1. 定义

*   中间程序即是一个服务端程序(监听连接)，也是一个客户端程序(发送给端口程序).操作系统内核支持通过配置socket参数的方式来实现多个进程绑定同一个端口。
*   要复用端口,必须使中间程序的监听SOCKET用setsockopt()函数设置。
    *   复用端口的原理是用在服务器安装一个中间程序,在客户端发送数据给端口前劫获这个数据,判断这个是不是HACKER发来的数据,如果是把它发给后门程序,如果不是则转发给端口程序,返回信息再发给客户端。

### 2. setsockopt

**用于任意类型、任意状态套接口的设置选项值**。

*   选项可能存在于多层协议中，它们总会出现在最上面的套接字层。
*   当操作套接字选项时，选项位于的层和选项的名称必须给出。
*   为了操作套接字层的选项，应该将层的值指定为SOL_SOCKET。
*   为了操作其它层的选项，控制选项的合适协议号必须给出。
    *   例如，为了表示一个选项由TCP协议解析，层应该设定为协议 号TCP。

**头文件所在位置**

```c++
#include <sys/types.h>
#include <sys/socket.h>
```

#### 2.1 函数原型

```c++
int setsockopt(int sockFd, int level, int optname, const void *optval, socklen_t optlen);
```

#### 2.2 参数说明

*   sockfd：将要被设置或者获取选项的套接字。
*   level：选项定义的层次；支持SOL_SOCKET、IPPROTO_TCP、IPPROTO_IP和IPPROTO_IPV6。一般设成SOL_SOCKET以存取socket层。
    *   SOL_SOCKET:通用套接字选项.
    *   IPPROTO_IP:IP选项.IPv4套接口
    *   IPPROTO_TCP:TCP选项.
    *   IPPROTO_IPV6: IPv6套接口

*   **optname：** 欲设置的选项，有下列几种数值:

![optname参数](/Users/alone/markdown/images/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0pNVzE0MDc=,size_16,color_FFFFFF,t_70.png)

*   **optval：** 对于setsockopt()，指针，指向存放选项待设置的新值的缓冲区。获得或者是设置套接字选项.根据选项名称的数据类型进行转换。
*   **optlen**：optval缓冲区长度。

#### 2.3 SO_REUSEADDR参数单独说明（端口复用）

optname选项之一：允许套接口和一个已在使用中的地址捆绑。

**SO_REUSEADDR**提供如下四个功能：

*   允许启动一个监听服务器并捆绑其众所周知端口，即使以前建立的将此端口用做他们的本地端口的连接仍存在。这通常是重启监听服务器时出现，若不设置此选项，则bind时将出错。
*   允许在同一端口上启动同一服务器的多个实例，只要每个实例捆绑一个不同的本地IP地址即可。对于TCP，我们根本不可能启动捆绑相同IP地址和相同端口号的多个服务器。
*   允许单个进程捆绑同一端口到多个套接口上，只要每个捆绑指定不同的本地IP地址即可。这一般不用于TCP服务器。
*   允许完全重复的捆绑：当一个IP地址和端口绑定到某个套接口上时，还允许此IP地址和端口捆绑到另一个套接口上。一般来说，这个特性仅在支持多播的系统上才有，而且只对UDP套接口而言（TCP不支持多播）。

**SO_REUSEPORT**有如下语义：

-   此选项允许完全重复捆绑，但仅在想捆绑相同IP地址和端口的套接口都指定了此套接口选项才行。
-   如果被捆绑的IP地址是一个多播地址，则SO_REUSEADDR和SO_REUSEPORT等效。

**编写 TCP/SOCK_STREAM 服务程序时，SO_REUSEADDR到底什么意思？**

这个套接字选项通知内核，如果端口忙，但`TCP`状态位于 `TIME_WAIT` ，可以重用端口。如果端口忙，而TCP状态位于其他状态，重用端口时依旧得到一个错误信息，指明"地址已经使用中"。如果你的服务程序停止后想立即重启，而新套接字依旧使用同一端口，此时`SO_REUSEADDR` 选项非常有用。必须意识到，此时任何非期望数据到达，都可能导致服务程序反应混乱，不过这只是一种可能，事实上很不可能。
#### 2.4 返回说明

成功执行时，返回0。失败返回-1，errno被设为以下的某个值

-   **EBADF**：sockfd不是有效的文件描述词
-   **EFAULT**：optval指向的内存并非有效的进程空间
-   **EINVAL**：在调用setsockopt()时，optlen无效
-   **ENOPROTOOPT**：指定的协议层不能识别选项
-   **ENOTSOCK**：socket描述的不是套接字

#### 2.5 使用用例

```c++
	// 在sockfd_one绑定bind之前，设置其端口复用
	int opt = 1;
	setsockopt( sockfd_one, SOL_SOCKET,SO_REUSEADDR, (const void *)&opt, sizeof(opt));
```

