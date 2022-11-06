# QPen Class

QPen类定义了QPainter如何绘制图形的线条和轮廓。

## Public Functions

### setStyle

```c++
void QPen::setStyle(Qt::PenStyle style)
```

将钢笔样式设置为给定的样式。

有关可用样式的列表，请参阅Qt::PenStyle文档。从Qt 4.1开始，也可以使用setDashPattern()函数来指定一个自定义的破折号图案，该函数隐式地将钢笔样式转换为Qt::CustomDashLine。

注意:这个函数将破折号偏移量重置为零。

### setColor

```c++
void QPen::setColor(const QColor &color)
```

将此笔的笔刷的颜色设置为给定的颜色。

