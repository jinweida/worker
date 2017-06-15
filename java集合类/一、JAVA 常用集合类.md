# 一、概念介绍
- 线程安全就是多线程访问时，采用了加锁机制，当一个线程访问该类的某个数据时，进行保护，其他线程不能进行访问直到该线程读取完，其他线程才可使用。不会出现数据不一致或者数据污染
- 线程不安全就是不提供数据访问保护，多线程先后更改数据会产生数据不一致或者数据污染的情况
- 一般使用synchronized关键字加锁同步控制，来解决线程不安全问题。
- ![image](http://note.youdao.com/yws/res/1833/3A17AACDC0A34C7FBFCD60A460CC9046)
# Collection接口
Set和List实现了Collection。Set中不能包含重复的元素。List是一个有序的集合，可以包含重复的元素，提供了按索引访问的方式
# Map接口
Map和Collection接口没有关系，是相互独立的，但是都属于集合类的一部分。Map包含了key-value对。Map不能包含重复的key，但是可以包含相同的value。
# Iterator
所有的集合类，都实现了Iterator接口，这是一个用于遍历集合中元素的接口，主要包含以下三种方法：
1. hasNext()是否还有下一个元素。
2. next()返回下一个元素。
3. remove()删除当前元素。
# 二、ArrayList和LinkedList
ArrayList和LinkedList在用法上没有区别，但是在功能上还是有区别的。LinkedList经常用在增删操作较多而查询操作很少的情况下，ArrayList则相反。
1. ArrayList是实现了基于动态数组的数据结构，LinkedList基于链表的数据结构。 
2. 对于随机访问get和set，ArrayList觉得优于LinkedList，因为LinkedList要移动指针
3. 对于新增和删除操作add和remove，LinedList比较占优势，因为ArrayList要移动数据。
# 三、Map集合
> 实现类：HashMap、Hashtable、LinkedHashMap和TreeMap

- **HashMap**,它根据键的HashCode值存储数据，根据键可以直接获取它的值，具有很快的访问速度，遍历时，取得数据的顺序是完全随机的。因为键对象不可以重复，所以HashMap最多只允许一条记录的键为Null，允许多条记录的值为Null，是非同步的
- Hashtable,与HashMap类似，是HashMap的线程安全版，它支持线程的同步，即任一时刻只有一个线程能写Hashtable，因此也导致了Hashtale在写入时会比较慢，它继承自Dictionary类，不同的是它不允许记录的键或者值为null，同时效率较低。
- **ConcurrentHashMap**,线程安全，并且锁分离。ConcurrentHashMap内部使用段(Segment)来表示这些不同的部分，每个段其实就是一个小的hash table，它们有自己的锁。只要多个修改操作发生在不同的段上，它们就可以并发进行。
- **LinkedHashMap**,保存了记录的插入顺序，在用Iteraor遍历LinkedHashMap时，先得到的记录肯定是先插入的，在遍历的时候会比HashMap慢，有HashMap的全部特性。
- **TreeMap**,实现SortMap接口，能够把它保存的记录根据键排序，默认是按键值的升序排序（自然顺序），也可以指定排序的比较器，当用Iterator遍历TreeMap时，得到的记录是排过序的。不允许key值为空，非同步的；

- jdk1.5以后线程安全的集合及java.util.concurrent包的锁

    ConcurrentSkipListMap 一个并发的、可排序的 Map， SkipList 跳表，实现 SortedMap、NavigableMap、ConcurrentNavigableMap 
