# Lua repeat…until 循环

Lua 编程语言中 repeat...until 循环语句不同于 for 和 while循环，for 和 while循环的条件语句在当前循环执行开始时判断，而 repeat...until 循环的条件语句在当前循环结束后判断，类似 do ... while() 循环。

### 语法

Lua 编程语言中 repeat...until 循环语法格式:

```lua
repeat
   statements
until( condition )
```



repeat...until 是条件后行,所以repeat...until 的循环体里面至少要运行一次。

**statements(循环体语句)** 可以是一条或多条语句，**condition(条件)** 可以是任意表达式，在 **condition(条件)** 为 false 时执行循环体语句。

在**condition(条件)**为 true 时会跳过当前循环并开始脚本执行紧接着的语句。

Lua repeat...until 循环流程图如下：

![Lua repeat...until 循环](../../images/lua_repeat_until_loop.jpg)



>   注：该循环结构又被称为直到型循环，可以简单的理解为：直到condition为真才跳出循环

### 实例

```lua
--[ 变量定义 --]
a = 10
--[ 执行循环 --]
repeat
   print("a的值为:", a)
   a = a + 1
until( a > 15 )
```

执行以上代码，程序输出结果为：

```
a的值为:	10
a的值为:	11
a的值为:	12
a的值为:	13
a的值为:	14
a的值为:	15
```