#  运行时数据区域
![image](https://raw.githubusercontent.com/jinweida/worker/master/JVM%E8%99%9A%E6%8B%9F%E6%9C%BA/145540ib3ztwzt8rj13ow1.png.thumb.jpg)
#### 1.程序计数器

- 是一块较小的内存空间，它可以看作是当前线程所执行的字节码的行号指示器

- 如果线程正在执行一个Java方法，这个计数器记录的是正在执行的虚拟机字节码指令的地址

- 如果正在执行的是Native方法，这个计数器值则为空（undefined），此区域是唯一没有OutOfMemoryError情况的区域
- 线程私有的
    
#### 2.虚拟机栈

- 线程私有的
- 描述的是Java方法执行的内存模型，每个方法执行的同时都会创建一个栈帧（Stack Frame）用于存储局部变量表，操作数栈，动态连接方法出口等信息。每个方法从调用直至执行完成的过程，就对应着一个栈帧在虚拟机中入栈到出栈的过程
- 局部变量表存放了编译期的各种数据类型（boolean，byte，char，short，int，float，long，double），对象引用（reference）类型（指针或者句柄）
- 此区域 出现异常

    - 如果线程请求的栈深度大雨虚拟机所允许的深度，将抛出StackOverflowError异常
    - 如果虚拟机栈可以动态扩展，如果扩展是无法申请到足够的内存，就会抛出OutOfMemoryError异常