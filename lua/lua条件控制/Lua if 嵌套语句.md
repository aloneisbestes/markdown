# Lua if 嵌套语句

## Lua if 嵌套语句

------

## if...else 语句

Lua if 语句允许嵌套, 这就意味着你可以在一个 if 或 else if 语句中插入其他的 if 或 else if 语句。

### Lua if 嵌套语句语法格式如下：

```lua
if( 布尔表达式 1) then   
  --[ 布尔表达式 1 为 true 时执行该语句块 --]   
	if(布尔表达式 2) then      
    --[ 布尔表达式 2 为 true 时执行该语句块 --]   
  end
end 
```

你可以用同样的方式嵌套 **else if...else** 语句。

### 实例

以下实例用于判断变量 a 和 b 的值：

```lua
--[ 定义变量 --]
a = 100;
b = 200;

--[ 检查条件 --]
if( a == 100 )
then
   --[ if 条件为 true 时执行以下 if 条件判断 --]
   if( b == 200 )
   then
      --[ if 条件为 true 时执行该语句块 --]
      print("a 的值为 100 b 的值为 200" );
   end
end
print("a 的值为 :", a );
print("b 的值为 :", b );
```

以上代码执行结果如下：

```
a 的值为 100 b 的值为 200
a 的值为 :	100
b 的值为 :	200
```