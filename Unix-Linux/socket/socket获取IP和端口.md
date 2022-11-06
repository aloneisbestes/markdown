# socket 获取 IP 和 port

 从sockaddr结构中提取IP， 先将结构sockaddr转为sockaddr_in结构，然后用在利用相关[API](https://so.csdn.net/so/search?q=API&spm=1001.2101.3001.7020)将其中的IP地址从网络格式转化我们熟悉点分十进制的字符串。

### 1. sockaddr和sockaddr_in结构

程序员不应操作sockaddr结构，sockaddr是给操作系统用的
程序员应使用sockaddr_in来表示地址，sockaddr_in区分了地址和端口，使用更方便。

```c++
 struct sockaddr {  
    unsigned short    sa_family;    // 2 bytes address family, AF_xxx  unsiged short
    char              sa_data[14];     // 14 bytes of protocol address  
}; 
```

```c++
struct sockaddr_in {  
    short            sin_family;       // 2 bytes e.g. AF_INET, AF_INET6  
    unsigned short   sin_port;    // 2 bytes e.g. htons(3490)  
    struct in_addr   sin_addr;     // 4 bytes see struct in_addr, below  
    char             sin_zero[8];     // 8 bytes zero this if you want to  
};  
  
struct in_addr {  
    unsigned long s_addr;          // 4 bytes load with inet_pton()  
}; 
```

它们结构之间表示如下图。

![img](/Users/alone/markdown/images/70.jpeg)

### 2. 从结构sockaddr获取IP和端口。

 使用结构**inet_ntop**获取IP地址，而不是用**inet_ntoa**。可能是因为64位机子引起的问题。

  **inet_ntop接口文档:**

```c++
/* Convert a Internet address in binary network format for interface
   type AF in buffer starting at CP to presentation form and place
   result in buffer of length LEN astarting at BUF.  */
extern const char *inet_ntop (int __af, const void *__restrict __cp,
			      char *__restrict __buf, socklen_t __len)
 
// 将其转化的结果放置到buf中。即最终转化的IP值存放在buf中。
```

#### 2.1 获取ip和端口

```c++
 struct sockaddr from;
 /*
     ...
        working 
     ...
*/
 struct sockaddr_in *sock = ( struct sockaddr_in*)&from;
 int port = ntohs(sock->sin_port);
 #ifdef __MINGW32__  //windows上打印方式
	 printf("ip:port  %s : %d",inet_ntoa(sock->sin_addr),port);
 #else              //linux上打印方式
	struct in_addr in  = sock->sin_addr;
	char str[INET_ADDRSTRLEN];   //INET_ADDRSTRLEN这个宏系统默认定义 16
	//成功的话此时IP地址保存在str字符串中。
	inet_ntop(AF_INET,&in, str, sizeof(str));
	printf("ip:port  %s : %d",str,port);
 #endif
```

