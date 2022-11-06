# C语言内存相关操作

## 1. 内存拷贝函数头文件

```c
#include <string.h>
```

## 2. 内存相关操作函数

### 1. 内存拷贝函数 memcpy

memcpy函数是一个用于拷贝两个不相关的内存块的函数。memcpy函数会从src的位置开始向后复制count个字节的数据到dest的内存位置，并返回dest的首地址。

#### 1 函数原型

```c
// 函数原型
void *memcpy( void *dest, const void *src, size_t count );
```

*   dest：目标内存地址
*   src：源内存地址，即需要拷贝的数据所在的内存地址
*   count：拷贝的大小
*   若dest和src有任意重叠，复制的结果都是未定义的（未拷贝内容被覆盖）。

#### 2 返回值

成功返回 dest 的所地址，失败返回 NULL

---

### 2. 内存初始化函数 memset

C 库函数 **void \*memset(void \*str, int c, size_t n)** 复制字符 **c**（一个无符号字符）到参数 **str** 所指向的字符串的前 **n** 个字符。

#### 1 函数原型

```c
void *memset(void *str, int c, size_t n);
```

-   **str** -- 指向要填充的内存块。
-   **c** -- 要被设置的值。该值以 int 形式传递，但是函数在填充内存块时是使用该值的无符号字符形式。
-   **n** -- 要被设置为该值的字符数。

#### 2 返回值

该值返回一个指向存储区 str 的指针。

---

### 3. 内存移动函数 memmove

C 库函数 **void \*memmove(void \*str1, const void \*str2, size_t n)** 从 **str2** 复制 **n** 个字符到 **str1**，但是在重叠内存块这方面，memmove() 是比 memcpy() 更安全的方法。如果目标区域和源区域有重叠的话，memmove() 能够保证源串在被覆盖之前将重叠区域的字节拷贝到目标区域中，复制后源区域的内容会被更改。如果目标区域与源区域没有重叠，则和 memcpy() 函数功能相同。

#### 1. 函数原型

```c
void *memmove(void *str1, const void *str2, size_t n);
```

-   **str1** -- 指向用于存储复制内容的目标数组，类型强制转换为 void* 指针。
-   **str2** -- 指向要复制的数据源，类型强制转换为 void* 指针。
-   **n** -- 要被复制的字节数。

#### 2. 返回值

该函数返回一个指向目标存储区 str1 的指针。

---

### 4. 内存对比函数 memcmp

C 库函数 **int memcmp(const void \*str1, const void \*str2, size_t n))** 把存储区 **str1** 和存储区 **str2** 的前 **n** 个字节进行比较。

#### 1. 函数原型

```c
int memcmp(const void *str1, const void *str2, size_t n)
```

-   **str1** -- 指向内存块的指针。
-   **str2** -- 指向内存块的指针。
-   **n** -- 要被比较的字节数。

#### 2. 返回值

-   如果返回值 < 0，则表示 str1 小于 str2。
-   如果返回值 > 0，则表示 str1 大于 str2。
-   如果返回值 = 0，则表示 str1 等于 str2。

---

