# QWidget Class

QWidget类是所有用户界面对象的基类。

## Protected Functions

### mousePressEvent

```C++
[virtual protected] void QWidget::mousePressEvent(QMouseEvent *event)
```

这个事件事件的事件处理程序可以在子类中重新实现，以接收小部件的鼠标按下事件。

如果您在mousePressEvent()中创建了新的小部件，mouseReleaseEvent()可能不会出现在您期望的位置，这取决于底层窗口系统(或X11窗口管理器)、小部件的位置等等。

默认实现在单击窗口外时关闭弹出窗口小部件。对于其他类型的小部件，它什么也不做。

请参见mouseReleaseEvent()、mouseDoubleClickEvent()、mouemoveevent()、event()、QMouseEvent和Scribble Example。

### mouseReleaseEvent

```c++
[virtual protected] void QWidget::mouseReleaseEvent(QMouseEvent *event)
```

这个事件的事件处理程序可以在子类中重新实现，以接收小部件的**鼠标释放**事件。

参见mousePressEvent()、mouseDoubleClickEvent()、mouemoveevent()、event()、QMouseEvent和Scribble Example。

### resizeEvent

```c++
[virtual protected] void QWidget::resizeEvent(QResizeEvent *event)
```

这个事件处理程序可以在子类中重新实现，以接收在事件参数中传递的小部件调整大小事件。当调用resizeEvent()时，小部件已经有了新的几何图形。旧的大小可以通过QResizeEvent::oldSize()访问。

小部件将被擦除，并在处理调整大小事件后立即接收绘制事件。在这个处理程序中不需要(或者不应该)进行绘图。

请参见moveEvent()、event()、resize()、QResizeEvent、paintEvent()和Scribble Example。

### moveEvent

```c++
[virtual protected] void QWidget::moveEvent(QMoveEvent *event)
```

这个事件处理程序可以在子类中重新实现，以接收在事件参数中传递的小部件移动事件。当小部件接收到此事件时，它已经位于新位置。

旧位置可以通过QMoveEvent::oldPos()访问。

请参见resizeEvent()、event()、move()和QMoveEvent。

### setMouseTracking

```c++
void setMouseTracking(bool enable)
```

此属性保存小部件是否启用了鼠标跟踪

如果禁用了鼠标跟踪(默认值)，则当移动鼠标时至少有一个鼠标按钮被按下时，小部件才会接收鼠标移动事件。

如果启用了鼠标跟踪，即使没有按下按钮，小部件也会接收到鼠标移动事件。

### setCursor

```c++
void setCursor(const QCursor &)
```

此属性保存此小部件的光标形状

当鼠标光标经过这个小部件时，它将呈现这个形状。有关一系列有用的形状，请参阅预定义游标对象列表。

编辑器小部件可能使用工字型游标:

```c++
setCursor(Qt::IBeamCursor);
```

如果没有设置游标，或者在调用unsetCursor()之后，将使用父游标。

默认情况下，该属性包含一个具有Qt::ArrowCursor形状的游标。

一些底层窗口实现将重置光标，如果它离开一个小部件，即使鼠标被捕获。如果希望为所有小部件设置光标，甚至在窗口外设置光标，请考虑QApplication::setOverrideCursor()。