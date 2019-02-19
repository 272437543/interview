# interview
哈希表
实现：发布一个内存空间作为hashmap存储空间大小为N，hash-key为对象的hash值取模N得到k。放入存储空间
如果空间发生冲突，就在这个空间之上建立链表存储这个物体。访问时用hash-key访问，当出现有多个链路时便利这个链表。哈希空间太小会访问过慢。太大又浪费空间。

==和equal区别
==用于比较基本数据类型。equal用来比较类。（一般重写）不重写的话和==一样比较类的地址。（基本数据类型没有地址这一情况）

引用传递和值传递
值传递是传递变量的一个副本。操作不对原变量有影响。
引用传递给地址，操作会有影响

多线程
实现：继承thread和实现runnable
重写run方法。start启动线程
区别：继承了thread类不能继承其他类。接口可以多实现。创建对象时实现了runnable接口的对象必须丢到thread的构造方法里面。

线程池
在开发中，频繁的创建和销毁一个线程，是很耗资源的，为此找出了一个可以循环利用已经存在的线程来达到自己的目的，线程池顾名思义，也就是线程池的集合，通过线程池执行的线程任务，可以很有效的去规划线程的使用。
newSingleThreadPool 单线程池，只能执行一个线程，执行完成执行下一个，有点像队列
newFixedThreadPool 固定长度线程池，每当提交一个任务时就创建一个线程池，直到达到线程池的最大数量，这时线程池的规模将不再变化。
newCacheThreadPool (推荐使用)可缓存的线程池，如果线程池的当前规模超过了处理需求时，那么将回收空闲的线程，当需求增加时，则可以添加新的线程，线程池的规模不存在任何限制。
newScheduledThreadPool 延迟任务的固定长度的线程池，而且以延迟或定时的方式来执行任务，类似于Timer。
拿newCacheThreadPool来说，每次submit一个线程进去都会进行执行，执行完成自动填充下一个任务。
例子：开一堆线程来计算斐波那契数列前30个：
![image](https://github.com/272437543/interview/blob/master/%E7%BA%BF%E7%A8%8B%E6%B1%A0%E7%BB%93%E6%9E%9C.png)
当线程1执行完成后，马上线程池又给它按排上了新的线程（第二行和第五行）

tcp/ip模型
OSI的七层模型，TCP/IP协议集的四层模型
![image](https://github.com/272437543/interview/blob/master/20170321140028195.jpg)

三次握手 四次挥手
连接(.connect()方法调用后)
第一次：客户端发送消息给服务器，请求连接的服务器端口，和初始序列。客户端进入已发送状态
第二次：服务器接收到消息后，发回确认消息
第三次：客户端再次发确认消息，进入连接状态，服务器收到后进入连接状态
断开连接(.close()方法调用后)
第一次：客户端发送断开连接请求
第二次：服务器收到后返回一个确认消息，但还没准备好断开，客户端收到后等待服务器断开
第三次：服务器准备好断开后，再次发出确认消息给客户端，可以断开，之后进入断连状态
第四次：客户端收到后断开连接，进入断连状态

http的应用

http报文 

get 
向服务器发送数据，参数也是url的一部分：如xxx.html?a=10

post 
数据包形式发送，不会显示在url上，用ajax发送表单

常用状态码

json
是Javascript的对象表示法
如：{"Student":{"name":"drake","age":"18"}}
这段字符串即可表示一个学生对象，并赋值名字为drake，年龄18（当然没有复制的话就是默认值）
通过eval()方法来建立原生的js对象

hashmap和hashtable的区别
1.实现接口不同(hashtable:dictionary, hashmap:map)。
2.线程安全不同(table自带synchronized)。
3.hashmap允许null，hashtable不允许null。

Python中元组tuple，列表list的区别：
tuple和list一样为线性链表，而tuple不允许进行修改。list可以进行修改。

Redis：数据结构，string list hash set sort-set，解决了什么问题
redis作为缓存：缓存用来做什么，什么情况下用，如何评估缓存是否生效，缓存穿透
mq工作原理
mybatis用了哪些技能，特性
rpc解决了什么问题，工作原理

Java的设计模式（参考：http://www.runoob.com/design-pattern/design-pattern-intro.html ）

算法题：
b+树 （检索文件）

栈的最大值
入栈时设定最大值，遇到比当前值大的值就更新，并push当前值减去最大值
出栈时pop的值加上最大值，如果pop值为正，相加后将最大值减去这个pop出的值。

斐波那契数列
（1 1 2 3 5 8 13）
实现：递归和非递归
特殊法：矩阵相乘o（logn）
![image](https://github.com/272437543/interview/blob/master/TIM%E6%88%AA%E5%9B%BE20181204175524.png)
公式法o（logN，因为是求N次幂，最快logN）
前n项和Sn=a（n+2）-1

合并两个有序数组（时间复杂度O(M + N)）
同时遍历两个数组，每次选择两个数组中最小的值

各种排序：O(NlogN)快速排序，堆排序，归并排序

杨氏矩阵的查询（查第K小数：最快O(N)，查询是否有M：最快O(长+宽)）
