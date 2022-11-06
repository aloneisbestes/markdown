# QTableWidget Class

QTableWidget类提供了一个具有默认模型的基于项目的表视图。

## 公共槽函数

### clear()

```c++
void QTableWidget::clear()
```

删除视图中的所有项。这也将删除所有的选择项和标题。如果您不想删除标题，请使用QTableWidget::clearContents()。表的尺寸保持不变。

### clearContents()

```c++
void QTableWidget::clearContents()
```

从视图中移除标题之外的所有项。这也将删除所有的选择。表的尺寸保持不变。Qt4.2之后

### insertColumn()

```c++
void QTableWidget::insertColumn(int column)
```

将空列插入位于column的表中。

### insertRow()

```c++
void QTableWidget::insertRow(int row)
```

将空行插入位于row的表中。

### removeColumn()

```c++
void QTableWidget::removeColumn(int column)
```

从表中删除列column及其所有项。

### removeRow()

```c++
void QTableWidget::removeRow(int row)
```

从表中删除行row及其所有项。

### scrollToItem()

```c++
void QTableWidget::scrollToItem(const QTableWidgetItem *item, QAbstractItemView::ScrollHint hint = EnsureVisible)
```

如果需要，滚动视图以确保项目可见。hint参数更精确地指定了操作后项应该位于的位置。

## 信号函数

### cellActivated()

```c++
void QTableWidget::cellActivated(int row, int column)
```

当激活行和列指定的单元格时发出此信号。这个函数是Qt 4.1中引入的。

### cellChanged()

```c++
void QTableWidget::cellChanged(int row, int column)
```

每当由行和列指定的单元格中项目的数据发生更改时，就发出此信号。这个函数是Qt 4.1中引入的。

### cellClicked()

```c++
void QTableWidget::cellClicked(int row, int column)
```

每当单击表中的单元格时，就会发出此信号。指定的行和列是被单击的单元格。这个函数是Qt 4.1中引入的。

### cellDoubleClicked()

```c++
void QTableWidget::cellDoubleClicked(int row, int column)
```

每当双击表中的单元格时，就会发出此信号。指定的行和列是双击的单元格。这个函数是Qt 4.1中引入的。

### cellEntered()

```c++
void QTableWidget::cellEntered(int row, int column)
```

当鼠标光标进入单元格时发出此信号。单元格由行和列指定。

只有当mouseTracking打开时，或者当移动到某项时按下鼠标按钮时，才会发出此信号。这个函数是Qt 4.1中引入的。

### cellPressed()

```c++
void QTableWidget::cellPressed(int row, int column)
```

每当按下表中的单元格时，就会发出此信号。指定的行和列是按下的单元格。这个函数是Qt 4.1中引入的。

### currentCellChanged()

```c++
void QTableWidget::currentCellChanged(int currentRow, int currentColumn, int previousRow, int previousColumn)
```

每当当前单元格发生变化时，就会发出此信号。由previousRow和previousColumn指定的单元格是先前拥有焦点的单元格，由currentRow和currentColumn指定的单元格是新的当前单元格。Qt 4.1中引入的。

### currentItemChanged()

```c++
void QTableWidget::currentItemChanged(QTableWidgetItem *current, QTableWidgetItem *previous)
```

每当当前项发生更改时，就会发出此信号。前一项是先前拥有焦点的项，当前项是新的当前项。

### itemActivated()

```c++
void QTableWidget::itemActivated(QTableWidgetItem *item)
```

该信号在指定的项目被激活时发出

### itemChanged()

```c++
void QTableWidget::itemChanged(QTableWidgetItem *item)
```

每当项目的数据发生更改时，就会发出此信号。

### itemClicked()

```c++
void QTableWidget::itemClicked(QTableWidgetItem *item)
```

每当单击表中的项时，就会发出此信号。指定的项就是被单击的项。

### itemDoubleClicked()

```c++
void QTableWidget::itemDoubleClicked(QTableWidgetItem *item)
```

每当双击表中的项时，就会发出此信号。指定的项就是双击的项。
### itemEntered

```c++
void QTableWidget::itemEntered(QTableWidgetItem *item)
```

当鼠标光标进入一个项时发出此信号。项目是输入的项目。

只有当mouseTracking打开时，或者当移动到某项时按下鼠标按钮时，才会发出此信号。

### itemPressed()

```c++
void QTableWidget::itemPressed(QTableWidgetItem *item)
```

每当按下表中的项时，就会发出此信号。指定的项是按下的项。

### itemSelectionChanged()

```c++
void QTableWidget::itemSelectionChanged()
```

每当选择发生变化时，就会发出此信号。参见selectedItems()和QTableWidgetItem::isSelected()。
