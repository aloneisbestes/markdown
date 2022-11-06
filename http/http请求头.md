

## http 请求头信息

| 请求头字段名        | 说明                                                         | 示例                                                         |
| :------------------ | :----------------------------------------------------------- | :----------------------------------------------------------- |
| Accept              | 能够接受的回应内容类型（Content-Types）。                    | Accept: text/plain                                           |
| Accept-Charset      | 能够接受的字符集                                             | Accept-Charset: utf-8                                        |
| Accept-Datetime     | 能够接受的按照时间来表示的版本                               | Accept-Datetime: Thu, 31 May 2007 20:35:00 GMT               |
| Accept-Encoding     | 能够接受的编码方式列表。参考HTTP压缩。                       | Accept-Encoding: gzip, deflate                               |
| Accept-Language     | 能够接受的回应内容的自然语言列表。                           | Accept-Language: en-US                                       |
| Authorization       | 用于超文本传输协议的认证的认证信息                           | Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==            |
| Cache-Control       | 用来指定在这次的请求/响应链中的所有缓存机制 都必须 遵守的指令 | Cache-Control: no-cache                                      |
| Connection          | 该浏览器想要优先使用的连接类型                               | Connection: keep-alive Connection: Upgrade                   |
| Content-Length      | 以 八位字节数组 （8位的字节）表示的请求体的长度              | Content-Length: 348                                          |
| Content-MD5         | 请求体的内容的二进制 MD5 散列值，以 Base64 编码的结果        | Content-MD5: Q2hlY2sgSW50ZWdyaXR5IQ==                        |
| Content-Type        | 请求体的 多媒体类型 （用于POST和PUT请求中）                  | Content-Type: application/x-www-form-urlencoded              |
| Cookie              | 之前由服务器通过 Set- Cookie （下文详述）发送的一个 超文本传输协议Cookie | Cookie: $Version=1; Skin=new;                                |
| Date                | 发送该消息的日期和时间(按照 RFC 7231 中定义的"超文本传输协议日期"格式来发送) | Date: Tue, 15 Nov 1994 08:12:31 GMT                          |
| Expect              | 表明客户端要求服务器做出特定的行为                           | Expect: 100-continue                                         |
| From                | 发起此请求的用户的邮件地址                                   | From: [user@example.com](mailto:user@example.com)            |
| Host                | 服务器的域名(用于虚拟主机 )，以及服务器所监听的传输控制协议端口号。如果所请求的端口是对应的服务的标准端口，则端口号可被省略。 | Host: en.wikipedia.org:80                                    |
| If-Match            | 仅当客户端提供的实体与服务器上对应的实体相匹配时，才进行对应的操作。主要作用时，用作像 PUT 这样的方法中，仅当从用户上次更新某个资源以来，该资源未被修改的情况下，才更新该资源。 | If-Match: “737060cd8c284d8af7ad3082f209582d”                 |
| If-Modified-Since   | 允许在对应的内容未被修改的情况下返回304未修改（ 304 Not Modified ） | If-Modified-Since: Sat, 29 Oct 1994 19:43:31 GMT             |
| If-None-Match       | 允许在对应的内容未被修改的情况下返回304未修改（ 304 Not Modified ） | If-None-Match: “737060cd8c284d8af7ad3082f209582d”            |
| If-Range            | 如果该实体未被修改过，则向我发送我所缺少的那一个或多个部分；否则，发送整个新的实体 | If-Range: “737060cd8c284d8af7ad3082f209582d”                 |
| If-Unmodified-Since | 仅当该实体自某个特定时间已来未被修改的情况下，才发送回应。   | If-Unmodified-Since: Sat, 29 Oct 1994 19:43:31 GMT           |
| Max-Forwards        | 限制该消息可被代理及网关转发的次数。                         | Max-Forwards: 10                                             |
| Origin              | 发起一个针对 跨来源资源共享 的请求。                         | Origin: [http://www.example-social-network.com](http://www.example-social-network.com/) |
| Pragma              | 与具体的实现相关，这些字段可能在请求/回应链中的任何时候产生多种效果。 | Pragma: no-cache                                             |
| Proxy-Authorization | 用来向代理进行认证的认证信息。                               | Proxy-Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==      |
| Range               | 仅请求某个实体的一部分。字节偏移以0开始。参见字节服务。      | Range: bytes=500-999                                         |
| Referer             | 表示浏览器所访问的前一个页面，正是那个页面上的某个链接将浏览器带到了当前所请求的这个页面。 | Referer: [http://en.wikipedia.org/wiki/Main_Page](https://en.wikipedia.org/wiki/Main_Page) |
| TE                  | 浏览器预期接受的传输编码方式：可使用回应协议头 Transfer-Encoding 字段中的值； | TE: trailers, deflate                                        |
| Upgrade             | 要求服务器升级到另一个协议。                                 | Upgrade: HTTP/2.0, SHTTP/1.3, IRC/6.9, RTA/x11               |
| User-Agent          | 浏览器的浏览器身份标识字符串                                 | User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:12.0) Gecko/20100101 Firefox/21.0 |
| Via                 | 向服务器告知，这个请求是由哪些代理发出的。                   | Via: 1.0 fred, 1.1 example.com (Apache/1.1)                  |
| Warning             | 一个一般性的警告，告知，在实体内容体中可能存在错误。         | Warning: 199 Miscellaneous warning                           |

----

### keep-alive和closer的区别

Connection 头（header） 决定当前的事务完成后，是否会关闭网络连接。如果该值是“keep-alive”，网络连接就是持久的，不会关闭，使得对同一个服务器的请求可以继续在该连接上完成。

#### 详细说明

HTTP协议采用“请求-应答”模式，当使用普通模式，即非KeepAlive模式时，每个请求/应答客户和服务器都要新建一个连接，完成之后立即断开连接（HTTP协议为无连接的协议）；当使用Keep-Alive模式（又称持久连接、连接重用）时，Keep-Alive功能使客户端到服务器端的连接持续有效，当出现对服务器的后继请求时，Keep-Alive功能避免了建立或者重新建立连接。

*   短连接
    所谓短连接，就是每次请求一个资源就建立连接，请求完成后连接立马关闭。每次请求都经过“创建tcp连接->请求资源->响应资源->释放连接”这样的过程

*   长连接
    所谓长连接(persistent connection)，就是只建立一次连接，多次资源请求都复用该连接，完成后关闭。要请求一个页面上的十张图，只需要建立一次tcp连接，然后依次请求十张图，等待资源响应，释放连接。

*   并行连接
    所谓并行连接(multiple connections)，其实就是并发的短连接。