# fstream 文件流的使用

## ifstream 

### 1. 头文件

```c++
#include <fstream>
```

## 函数的使用

### is_open() 函数

检查流是否有关联文件

#### 1. 函数原型

```c++
bool is_open();					// (C++11 前)
bool is_open() const;		// (C++11 起)
```

#### 2. 返回值

若文件流有关联文件，则为 true ，否则为 false 。

### eof() 函数

检查是否到达了文件末尾

#### 1. 函数原型

```c++
bool eof() const;
```

#### 2. 返回值

若遇到文件尾条件则为 true ，否则为 false 。

#### 3. 注意

此函数只报告最近的 I/O 操作所设置的流状态；它不检测关联的数据源。例如，若最近的 I/O 为返回文件最后字节的 [`get()`](https://zh.cppreference.com/w/cpp/io/basic_istream/get) ，则 `eof()` 返回 false 。下个 `get()` 无法读取任何内容，并设置 `eofbit` 。之后 `eof()` 才返回 true 。

典型使用中，输入流处理在任何错误上停止。然后能用 `eof()` 和 [fail()](https://zh.cppreference.com/w/cpp/io/basic_ios/fail) 区别不同的错误条件。

### 文件偏移

*   ios::beg  文件头
*   ios::end  文件尾
*   ios::cur  当前位置

#### 1. 示例

```c++
file.seekg(0,ios::beg);   //让文件指针定位到文件开头 
file.seekg(0,ios::end);   //让文件指针定位到文件末尾 
file.seekg(10,ios::cur);   //让文件指针从当前位置向文件末方向移动10个字节 
file.seekg(-10,ios::cur);   //让文件指针从当前位置向文件开始方向移动10个字节 
file.seekg(10,ios::beg);   //让文件指针定位到离文件开头10个字节的位置
```

