# libevent 宏定义

### 错误宏定义

```c
#define HTTP_OK			200	/**< request completed ok */
#define HTTP_NOCONTENT		204	/**< request does not have content */
#define HTTP_MOVEPERM		301	/**< the uri moved permanently */
#define HTTP_MOVETEMP		302	/**< the uri moved temporarily */
#define HTTP_NOTMODIFIED	304	/**< page was not modified from last */
#define HTTP_BADREQUEST		400	/**< invalid http request was made */
#define HTTP_NOTFOUND		404	/**< could not find content for uri */
#define HTTP_BADMETHOD		405 	/**< method not allowed for this uri */
#define HTTP_ENTITYTOOLARGE	413	/**<  */
#define HTTP_EXPECTATIONFAILED	417	/**< we can't handle this expectation */
#define HTTP_INTERNAL           500     /**< internal error */
#define HTTP_NOTIMPLEMENTED     501     /**< not implemented */
#define HTTP_SERVUNAVAIL	503	/**< the server is not available */
```

