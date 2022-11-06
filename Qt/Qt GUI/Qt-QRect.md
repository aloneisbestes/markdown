# QRect Class

QRect类使用整数精度定义平面中的矩形。

---

## Public Functions

### contains

```c++
bool QRect::contains(const QPoint &point, bool proper = false) const
```

如果给定点在矩形的内部或边缘上，则返回true，否则返回false。如果proper为true，则此函数仅在给定点位于矩形内(即，不在边缘上)时返回true。

### topLeft

```c++
QPoint QRect::topLeft() const
```

返回矩形左上角的位置。