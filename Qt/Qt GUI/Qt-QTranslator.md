# QTranslator

QTranslator类为文本输出提供国际化支持。

### load()

```c++
bool QTranslator::load(const QString &filename, const QString &directory = QString(), const QString &search_delimiters = QString(), const QString &suffix = QString());
bool QTranslator::load(const QLocale &locale, const QString &filename, const QString &prefix = QString(), const QString &directory = QString(), const QString &suffix = QString())
```

加载文件名+后缀(”.qm”(如果未指定后缀)，它可以是绝对文件名，也可以是相对于目录的。如果翻译成功加载，则返回true;否则返回false。

如果没有指定directory，则使用当前目录(即作为currentPath())。

此转换器对象的先前内容将被丢弃。

如果该文件名不存在，则按以下顺序尝试其他文件名:

* 没有附加后缀的文件名。

* 去掉search_delimiter字符后面的文本(如果是空字符串，则“_.”是search_delimiter的默认值)和后缀的文件名。

* 去掉文件名，没有附加后缀。

* 文件名进一步剥离，等等。

例如，在fr_CA地区(讲法语的加拿大)运行的应用程序可能调用load("foo.fr_ca"， "/opt/傻瓜")。load()会尝试从列表中打开第一个现有的可读文件:

1. `/opt/foolib/foo.fr_ca.qm`
2. `/opt/foolib/foo.fr_ca`
3. `/opt/foolib/foo.fr.qm`
4. `/opt/foolib/foo.fr`
5. `/opt/foolib/foo.qm`
6. `/opt/foolib/foo`

```c++
bool QTranslator::load(const uchar *data, int len, const QString &directory = QString())
```

这个函数会重载load()。

将长度为len的QM文件数据加载到转换器中。

没有复制数据。调用者必须能够保证数据不会被删除或修改。

directory仅用于在加载QM文件的依赖项时指定基目录。如果文件没有依赖项，则忽略此参数。