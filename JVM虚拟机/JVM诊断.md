#### 描述
从jdk7开始引入jvm诊断工具，可以向运行中的JVM发送诊断命令。可以查看jvm启动时的一些参数，例如：垃圾回收算法、堆大小等。

#### 查看JVM进程的PID

```
[root@10-23-196-181 ~]# jcmd -l
4981 sun.tools.jcmd.JCmd -l
3658 /usr/local/slssync/rpc-sls-sync.jar
3566 /usr/local/sls/rpc-sls.jar
[root@10-23-196-181 ~]# jps -l
3658 /usr/local/slssync/rpc-sls-sync.jar
3566 /usr/local/sls/rpc-sls.jar
5007 sun.tools.jps.Jps
[root@10-23-196-181 ~]# 
```
#### 查看进程3566的参数

```
[root@10-23-196-181 ~]# jcmd 3566 VM.flags 3566

-XX:CICompilerCount=4  #设置最大并行编译数
-XX:InitialHeapSize=262144000 #初始化堆大小 等同于-Xms
-XX:MaxHeapSize=4167041024 #最大堆大小 等同于 -Xmx
-XX:MaxNewSize=1388838912 #JVM堆区域新生代内存的最大可分配大小 等同于-Xmn
-XX:MinHeapDeltaBytes=524288 #the minimum change in heap space due to gc
-XX:NewSize=87031808 
-XX:OldSize=175112192 
-XX:+UseCompressedClassPointers #使用-XX:+UseCompressedClassPointers选项来压缩类指针，在64位os下才有效
-XX:+UseCompressedOops #压缩对象指针
-XX:+UseParallelGC #Use the parallel Scavenge garbage collector 
```
