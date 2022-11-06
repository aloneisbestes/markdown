# Qt 模块

## 一、基础模块

Qt 基础模块分为以下几个：

- Qt Core，提供核心的非 GUI 功能，所有模块都需要这个模块。这个模块的类包括了动画框架、定时器、各个容器类、时间日期类、事件、IO、JSON、插件机制、智能指针、图形（矩形、路径等）、线程、XML 等。所有这些类都可以通过 头文件引入。
- Qt Gui，提供 GUI 程序的基本功能，包括与窗口系统的集成、事件处理、OpenGL 和 OpenGL ES 集成、2D 图像、字体、拖放等。这些类一般由 Qt 用户界面类内部使用，当然也可以用于访问底层的 OpenGL ES 图像 API。Qt Gui 模块提供的是所有图形用户界面程序都需要的通用功能。
- Qt Multimedia，提供视频、音频、收音机以及摄像头等功能。这些类可以通过 引入，而且需要在 pro 文件中添加 QT += multimedia。
- Qt Network，提供跨平台的网络功能。这些类可以通过 引入，而且需要在 pro 文件中添加 QT += network。
- Qt Qml，提供供 QML（一种脚本语言，也提供 JavaScript 的交互机制） 使用的 C++ API。这些类可以通过 引入，而且需要在 pro 文件中添加 QT += qml。
- Qt Quick，允许在 Qt/C++ 程序中嵌入 Qt Quick（一种基于 Qt 的高度动画的用户界面，适合于移动平台开发）。这些类可以通过 引入，而且需要在 pro 文件中添加 QT += quick。
- Qt SQL，允许使用 SQL 访问数据库。这些类可以通过 引入，而且需要在 pro 文件中添加 QT += sql。
- Qt Test，提供 Qt 程序的单元测试功能。这些类可以通过 引入，而且需要在 pro 文件中添加 QT += testlib。
- Qt Webkit，基于 WebKit2 的实现以及一套全新的 QML API（顺便说一下，Qt 4.8 附带的是 QtWebkit 2.2）。