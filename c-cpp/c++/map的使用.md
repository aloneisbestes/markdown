# map的使用

### 判断 key 是否存在

```c++
// 函数
iterator find ( const key_type& key );
```

#### 方法一

```c++
if (mymap.find(key) == mymap.end())
    cout << "没有这个key" << endl;
```

#### 方法二

```c++
if (mymap.count(key) == 0)
    cout << "no this key" << endl;
```

