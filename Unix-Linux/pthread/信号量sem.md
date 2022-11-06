# 信号量 sem

linux sem 信号量是一种特殊的变量，访问具有原子性， 用于解决进程或线程间共享资源引发的同步问题。

用户态进程对 sem 信号量可以有以下两种操作：

*   等待信号量
    当信号量值为 0 时，程序等待；当信号量值大于 0 时，信号量减 1，程序继续运行。
*   发送信号量
    将信号量值加 1

通过对信号量的控制，从而实现共享资源的顺序访问。

## 1. sem 的操作

```c++
int    sem_close(sem_t *);
int    sem_destroy(sem_t *);
int    sem_getvalue(sem_t *, int *);
int    sem_init(sem_t *, int, unsigned int);
sem_t *sem_open(const char *, int, ...);
int    sem_post(sem_t *);
int    sem_trywait(sem_t *);
int    sem_unlink(const char *);
int    sem_wait(sem_t *);
```

## 2. 相关函数说明

linux 信号量相关函数都声明头文件 semaphore.h 头文件中，所以使用信号量之前需要先包含头文件

```c++
#include <semaphore.h>
```

信号量的创建就像声明一般的变量一样简单，例如：sem_t sem，之后对该信号量进行初始化和使用。

### 2.1 sem_init

该函数用于创建信号量，其原型如下：

```c++
int sem_init(sem_t *sem, int pshared, unsigned int value);
```

该函数初始化由 sem 指向的信号对象，并给它一个初始的整数值 value。

pshared 控制信号量的类型，值为 0 代表该信号量用于多线程间的同步，值如果大于 0 表示可以共享，用于多个相关进程间的同步

参数 pshared > 0 时指定了 sem 处于共享内存区域，所以可以在进程间共享该变量

**返回值**

*   **sem_init()** 在成功完成之后会返回零。其他任何返回值都表示出现了错误。如果出现以下任一情况，该函数将失败并返回对应的值。

### 2.2 sem_wait

```c++
int sem_wait(sem_t *sem); 

int sem_trywait(sem_t *sem);
```

sem_wait 是一个阻塞的函数，测试所指定信号量的值，它的操作是原子的。若 sem value > 0，则该信号量值减去 1 并立即返回。若sem value = 0，则阻塞直到 sem value > 0，此时立即减去 1，然后返回。

sem_trywait 函数是非阻塞的函数，它会尝试获取获取 sem value 值，如果 sem value = 0，不是阻塞住，而是直接返回一个错误 EAGAIN。

**返回值**

*   **sem_wait()** 在成功完成之后会返回零。其他任何返回值都表示出现了错误。如果出现以下任一情况，该函数将失败并返回对应的值。

### 2.3 sem_post

把指定的信号量 sem 的值加 1，唤醒正在等待该信号量的任意线程。

```c+++
int sem_post(sem_t *sem);
```

**返回值**

*   **sem_post()** 在成功完成之后会返回零。其他任何返回值都表示出现了错误。如果出现以下任一情况，该函数将失败并返回对应的值。

### 2.4 sem_getvalue

```c++
int sem_getvalue(sem_t *sem, int *sval);
```

获取信号量 sem 的当前值，把该值保存在 sval，若有 1 个或者多个线程正在调用 sem_wait 阻塞在该信号量上，该函数返回阻塞在该信号量上进程或线程个数。

### 2.5 sem_destroy

该函数用于对用完的信号量的清理。它的原型如下：

```c++
int sem_destroy(sem_t *sem);
```

**返回值**

*   成功则返回 0，失败返回 -1