# Qt-QTextCodec

QTextCodec类提供文本编码之间的转换。

### tataic 函数

#### codecForName()

```c++
QTextCodec *QTextCodec::codecForName(const QByteArray &name)
QTextCodec *QTextCodec::codecForName(const char *name)
```

搜索所有已安装的QTextCodec对象，并返回与名称最匹配的对象;匹配不区分大小写。如果找不到与名称name匹配的编解码器，则返回0。

#### setCodecForLocale()

```c++
void QTextCodec::setCodecForLocale(QTextCodec *c)
```

将编解码器设置为c;这将由codecForLocale()返回。如果c为nullptr，则将编解码器重置为默认值。

对于一些希望使用自己的机制来设置语言环境的应用程序，这可能是必需的。

**警告:此函数不可重入**。参见codecForLocale()。