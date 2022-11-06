# libevent 结构解析

### evhttp_cmd_type 请求类型

**结构原型**

```c
enum evhttp_cmd_type {
	EVHTTP_REQ_GET     = 1 << 0,
	EVHTTP_REQ_POST    = 1 << 1,
	EVHTTP_REQ_HEAD    = 1 << 2,
	EVHTTP_REQ_PUT     = 1 << 3,
	EVHTTP_REQ_DELETE  = 1 << 4,
	EVHTTP_REQ_OPTIONS = 1 << 5,
	EVHTTP_REQ_TRACE   = 1 << 6,
	EVHTTP_REQ_CONNECT = 1 << 7,
	EVHTTP_REQ_PATCH   = 1 << 8
};
```





