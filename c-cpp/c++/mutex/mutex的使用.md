# mutex 的使用

### std::unique_lock

std::unique_lock为锁管理模板类，是对通用mutex的封装。**std::unique_lock对象以独占所有权的方式(unique owership)管理mutex对象的上锁和解锁操作，即在unique_lock对象的声明周期内，它所管理的锁对象会一直保持上锁状态；而unique_lock的生命周期结束之后，它所管理的锁对象会被解锁**。unique_lock具有lock_guard的所有功能，而且更为灵活。虽然二者的对象都不能复制，但是unique_lock可以移动(movable)，因此用unique_lock管理互斥对象，可以作为函数的返回值，也可以放到STL的容器中。
### std::move

-   传递的是左值，推导为左值引用，仍旧static_cast转换为右值引用。
-   传递的是右值，推导为右值引用，仍旧static_cast转换为右值引用。
-   在返回处，直接范围右值引用类型即可。还是通过renive_reference获得_Tp类型，然后直接type&&即可。

-   在《Effective Modern C++》中建议：**对于右值引用使用std::move，对于万能引用使用std::forward。**