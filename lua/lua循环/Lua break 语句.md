# Lua break 语句

## Lua break 语句

Lua 编程语言 break 语句插入在循环体中，用于退出当前循环或语句，并开始脚本执行紧接着的语句。

如果你使用循环嵌套，break语句将停止最内层循环的执行，并开始执行的外层的循环语句。

### 语法

Lua 编程语言中 **break** 语句语法格式:

```lua
break
```

流程图：

![Lua break 语句](/Users/alone/Desktop/note/markdown/images/cpp_break_statement-20221017231109353.jpg)

### 实例

以下实例执行 while 循环，在变量 a 小于 20 时输出 a 的值，并在 a 大于 15 时终止执行循环：

```lua
--[ 定义变量 --]
a = 10

--[ while 循环 --]
while( a < 20 )
do
   print("a 的值为:", a)
   a=a+1
   if( a > 15)
   then
      --[ 使用 break 语句终止循环 --]
      break
   end
end
```

以上代码执行结果如下：

```
a 的值为:	10
a 的值为:	11
a 的值为:	12
a 的值为:	13
a 的值为:	14
a 的值为:	15
```