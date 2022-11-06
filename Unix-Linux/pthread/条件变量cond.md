# 条件变量 cond

## 1. 设置 timedwait 超时时间

### 1.1 时间简介

时间单位：
  秒（second），时间单位 ： s，
  毫秒(millisecond），时间单位：ms
  微秒（microsecond），时间单位:μs

时间换算:
      1s【秒】 = 1000ms【毫秒】
  1ms【毫秒】 = 1000μs【微秒】
  1μs【微秒】 = 1000ns【纳秒】

### 1.2 时间结构体

``` c++
struct timespec {
		time_t tv_sec;    /* Seconds,秒 */
		long tv_nsec;     /* Nanoseconds,纳秒 */
};

struct timeval{
		__time_t tv_sec;        /* Seconds.秒 */
		__suseconds_t tv_usec;  /* Microseconds.微秒 */
};
```

### 1.3 设置超时时间

``` c++
struct timespec abstime;
struct timeval now;
/* 设置超时时间为 100 ms */
long timeout_ms = 100; // wait time 100ms
/* 获取当前时间 */
gettimeofday(&now, NULL);
/* 
	将得到的当前时间加上设置的超时时间
	now.tv_usec * 1000: 表示把微秒转化为纳秒
	(timeout_ms % 1000) * 1000000: 表示将毫秒转化为纳秒
	*/
long nsec = now.tv_usec * 1000 + (timeout_ms % 1000) * 1000000;
/* 
	得到当前的秒数
	nsec / 1000000000: 表示得到 nsec 当前的秒数
	timeout_ms / 1000: 表示得到 timeout_ms 的秒数
	*/
abstime.tv_sec=now.tv_sec + nsec / 1000000000 + timeout_ms / 1000;
/*
	得到纳秒数
	nsec % 1000000000: 表示得到设置的超时时间的纳秒数
	*/
abstime.tv_nsec=nsec % 1000000000;
```

