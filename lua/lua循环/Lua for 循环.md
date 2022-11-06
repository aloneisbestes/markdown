# Lua for 循环

## Lua for 循环

Lua 编程语言中 for 循环语句可以重复执行指定语句，重复次数可在 for 语句中控制。

Lua 编程语言中 for语句有两大类：：

-   数值for循环
-   泛型for循环

------

## 数值for循环

Lua 编程语言中数值for循环语法格式:

```lua
for var=exp1,exp2,exp3 do  
    <执行体>  
end  
```

var从exp1变化到exp2，每次变化以exp3为步长递增var，并执行一次"执行体"。exp3是可选的，如果不指定，默认为1。

### 实例

```lua
for i=1,f(x) do
    print(i)
end
 
for i=10,1,-1 do
    print(i)
end
```

for的三个表达式在循环开始前一次性求值，以后不再进行求值。比如上面的f(x)只会在循环开始前执行一次，其结果用在后面的循环中。

验证如下:

```lua
#!/usr/local/bin/lua
function f(x)  
    print("function")  
    return x*2   
end  
for i=1,f(5) do print(i)  
end  
```

以上实例输出结果为：

```
function
1
2
3
4
5
6
7
8
9
10
```

可以看到 函数f(x)只在循环开始前执行一次。

------

## 泛型for循环

泛型for循环通过一个迭代器函数来遍历所有值，类似java中的foreach语句。

Lua 编程语言中泛型for循环语法格式:

```lua
--打印数组a的所有值  
for i,v in ipairs(a) 
	do print(v) 
end  
```

i是数组索引值，v是对应索引的数组元素值。ipairs是Lua提供的一个迭代器函数，用来迭代数组。

### 实例

循环数组 days：

```lua
#!/usr/local/bin/lua  
days = {"Suanday","Monday","Tuesday","Wednesday","Thursday","Friday","Saturday"}  
for i,v in ipairs(days) do  print(v) end   
```

以上实例输出结果为：

```
Suanday
Monday
Tuesday
Wednesday
Thursday
Friday
Saturday
```

