# QMouseEvent Class

QMouseEvent类包含描述鼠标事件的参数。

## Public Functions

### globalPos

```C++
QPoint QMouseEvent::globalPos() const
```

返回事件发生时鼠标光标的全局位置。这在像X11这样的异步窗口系统中很重要。每当您移动小部件以响应鼠标事件时，globalPos()可能与当前指针位置QCursor::pos()和QWidget::mapToGlobal(pos())有很大不同。

### button

```c++
Qt::MouseButton QMouseEvent::button() const
```

返回引起事件的按钮。

注意，对于鼠标移动事件，返回值总是Qt::NoButton。

### pos

```c++
QPoint QMouseEvent::pos() const
```

返回相对于接收事件的小部件的鼠标光标的位置。

如果由于鼠标事件而移动小部件，请使用globalPos()返回的全局位置来避免晃动动作。

请参见x()、y()和globalPos()。