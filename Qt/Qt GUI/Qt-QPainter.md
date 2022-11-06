# QPainter Class

QPainter类在小部件和其他绘图设备上执行低级绘图。

## Public Functions

### save

```c++
void QPainter::save()
```

保存当前绘制器状态(将状态推入堆栈)。一个save()后面必须跟着一个相应的restore();end()函数的作用是:展开堆栈。

### setPen

```c++
void QPainter::setPen(const QPen &pen)
```

将画家的笔设置为给定的笔。笔定义了如何绘制线条和轮廓，它还定义了文本的颜色。

### drawRect

```c++
void QPainter::drawRect(const QRectF &rectangle)
```

使用当前钢笔和画笔绘制当前矩形。填充矩形的大小为rectangle.size()。描边矩形的大小为rectangle.size()加上钢笔宽度。

![image-20221101114738913](../../images/image-20221101114738913.png)

### pen

```c++
const QPen &QPainter::pen() const
```

返回画家当前的钢笔。

### restore

```c++
void QPainter::restore()
```

恢复当前的画师状态(弹出堆栈中保存的状态)。

### fillRect

```c++
void QPainter::fillRect(const QRect &rectangle, const QBrush &brush)
```

这是一个重载函数。用指定的画笔填充给定的矩形。
