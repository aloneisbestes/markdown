# Lua if…else 语句

## Lua if...else 语句

[![Lua 流程控制](/Users/alone/Desktop/note/markdown/images/up-20221017232127455.gif) Lua 流程控制](https://www.w3cschool.cn/lua/lua-decision-making.html)

------

## if...else 语句

Lua if 语句可以与 else 语句搭配使用, 在 if 条件表达式为 false 时执行 else 语句代码块。

Lua if...else 语句语法格式如下：

```lua
if(布尔表达式)
then
   --[ 布尔表达式为 true 时执行该语句块 --]
else
   --[ 布尔表达式为 false 时执行该语句块 --]
end
```

在布尔表达式为 true 时会if中的代码块会被执行，在布尔表达式为 false 时，else 的代码块会被执行。

Lua认为false和nil为假，true 和非nil为真。要注意的是Lua中 0 为 true。

if 语句流程图如下：

![Lua if...else 语句](/Users/alone/Desktop/note/markdown/images/if_else_statement.jpg)

### 实例

以下实例用于判断变量 a 的值：

```lua
--[ 定义变量 --]
a = 100;
--[ 检查条件 --]
if( a < 20 )
then
   --[ if 条件为 true 时执行该语句块 --]
   print("a 小于 20" )
else
   --[ if 条件为 false 时执行该语句块 --]
   print("a 大于 20" )
end
print("a 的值为 :", a)
```

以上代码执行结果如下：

```
a 大于 20
a 的值为 :	100
```

------

## if...else if...else 语句

Lua if 语句可以与 else if...else 语句搭配使用, 在 if 条件表达式为 false 时执行 else if...else 语句代码块，用于检测多个条件语句。

Lua if...else if...else 语句语法格式如下：

```lua
if( 布尔表达式 1)
then
   --[ 在布尔表达式 1 为 true 时执行该语句块 --]

else if( 布尔表达式 2)
   --[ 在布尔表达式 2 为 true 时执行该语句块 --]

else if( 布尔表达式 3)
   --[ 在布尔表达式 3 为 true 时执行该语句块 --]
else 
   --[ 如果以上布尔表达式都不为 true 则执行该语句块 --]
end
```

### 实例

以下实例对变量 a 的值进行判断：

```lua
--[ 定义变量 --]
a = 100

--[ 检查布尔条件 --]
if( a == 10 )
then
   --[ 如果条件为 true 打印以下信息 --]
   print("a 的值为 10" )
elseif( a == 20 )
then   
   --[ if else if 条件为 true 时打印以下信息 --]
   print("a 的值为 20" )
elseif( a == 30 )
then
   --[ if else if condition 条件为 true 时打印以下信息 --]
   print("a 的值为 30" )
else
   --[ 以上条件语句没有一个为 true 时打印以下信息 --]
   print("没有匹配 a 的值" )
end
print("a 的真实值为: ", a )
```

以上代码执行结果如下：

```
没有匹配 a 的值
a 的真实值为: 	100
```