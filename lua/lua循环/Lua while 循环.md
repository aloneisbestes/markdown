# Lua while 循环

## Lua while 循环

Lua 编程语言中 while 循环语句在判断条件为 true 时会重复执行循环体语句。

### 语法

Lua 编程语言中 while 循环语法：

```
while(condition)
do
   statements
end
```

**statements(循环体语句)** 可以是一条或多条语句，**condition(条件)** 可以是任意表达式，在 **condition(条件)** 为 true 时执行循环体语句。

流程图如下：

![Lua while 循环](/Users/alone/Desktop/note/markdown/images/lua_while_loop.jpg)

在以上流程图中我们可以看出在**condition(条件)**为 false 时会跳过当前循环并开始脚本执行紧接着的语句。

注：该循环结构又被称之为当型循环，可以理解为

### 实例

以下实例循环输出 a 的值：

```
a=10
while( a < 20 )
do
   print("a 的值为:", a)
   a = a+1
end
```

执行以上代码，输出结果如下：

```
a 的值为:	10
a 的值为:	11
a 的值为:	12
a 的值为:	13
a 的值为:	14
a 的值为:	15
a 的值为:	16
a 的值为:	17
a 的值为:	18
a 的值为:	19
```