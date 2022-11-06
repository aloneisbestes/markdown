# QPoint Class

QPoint类使用整数精度定义平面上的一个点。

## Public Function

### manhattanLength

```c++
int QPoint::manhattanLength() const
```

返回x()和y()的绝对值之和，传统上称为向量从原点到该点的“曼哈顿长度”。例如:

```
QPoint oldPosition;

MyWidget::mouseMoveEvent(QMouseEvent *event)
{
    QPoint point = event->pos() - oldPosition;
    if (point.manhattanLength() > 3)
        // 鼠标从oldPosition移动超过3个像素
}
```