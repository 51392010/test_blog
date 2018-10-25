---
layout: post
title: Collection 集合类
date: 2018-09-09
tag: JAVA
---


### Collection 结构图

![image](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1536640717084&di=dde5bc25a83d06fdde8ca83065aa7abf&imgtype=jpg&src=http%3A%2F%2Fimg0.imgtn.bdimg.com%2Fit%2Fu%3D3491376720%2C2233445223%26fm%3D214%26gp%3D0.jpg)

### Collection 接口介绍
Collection是最基本的集合接口，一个Collection代表一组Object，它的内部之间有所区分，比如：一些集合可以排序，另一些则不能。一些集合内能存储相同的元素，而另一些不能。还有就是JAVA SDK不允许一个类直接继承Collection，你只能继承Collection的子类。

### Collection 的子类

- ##### List 是一个允许有重复元素的有序集合。它的子类有：
1）`ArrayList：`是基于数组实现的，是一个动态的数组队列。查询速度要比LinkedList速度要快。插入和删除速度比LinkedList慢。<br/>
问：为什么插入和删除速度比LinkedList慢？
```
ArrayList：
    public boolean add(E e) {
        ensureCapacityInternal(size + 1);  // 判断是否增量
        elementData[size++] = e;
        return true;
    }

LinkedList：
    public boolean add(E e) {
        linkLast(e);
        return true;
    }
```
原因：因为ArrayList插入时需要判断是否增量，删除的时候要将数组移位，有一个复制操作，而LinkedList则不需要，插入和删除都是直接操作。
<br/>
<br/>
2）`LinkedList：`是基于链表实现的，是一个双向循环链表，可以当做堆栈使用。
<br/>
<br/>
3）`Vector：`是基于数组实现的，是一个矢量队列，是线程安全的。
<br/>
<br/>
4）`Stack：`继承自`Vector`，它的实现原理也是基于数组是实现。
- ##### Set 是一个不允许有重复元素的无序集合，它的子类有：
1）`HashSet：`
是一个无序的集合，基于HashMap实现；HashSet集合中允许有null值。
<br/>
<br/>
2）`TreeSet：`TreeSet是一个有序的集合，基于TreeMap实现；TreeSet中不允许有null值。

- ##### Map 键值对、键唯一、值不唯，无序的集合，支持序列化
1）`HashMap：`它是通过哈希表来存储key-value键值对的，每个key对应一个value，并且允许key-value为空。HashMap线程不安全。
<br/>
<br/>
2）`Hashtable：`它是一个散列表，它的存储内容也是键值对(key-value)的形式，不允许key-value为空，Hashtable是线程安全的。
<br/>
<br/>
HashMap与Hashtable总结：虽然Hashtable是线程安全的，但是在多线程的情况下，也不一定用它，因为效率太低。HashMap配合Collections工具类来实现线程安全。同时，也可以选择使用ConcurrentHashMap；该类的线程安全使用Lock实现的，效率都高于Hashtable。

> ArrayList和HashMap默认大小?

- 在 Java 7 中，ArrayList 的默认大小是 10 个元素，HashMap 的默认大小是16个元素。这就是 Java 7 中 ArrayList 和 HashMap 类的代码片段。

> 如何实现集合排序?

你可以使用有序集合，如 TreeSet 或 TreeMap，你也可以使用有顺序的的集合，如 list，然后通过 Collections.sort() 来排序。

<br/>

<br/>

*参考资源：*[JAVA集合类汇总](https://blog.csdn.net/pengjwhx/article/details/69525087)