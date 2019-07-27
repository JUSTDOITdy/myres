



![1560328053118](C:\Users\DYY\AppData\Roaming\Typora\typora-user-images\1560328053118.png)

避免重复用的是hash值即h，不是hashcode值,hashcode值默认是jvm地址

```java
static class Entry<K,V> implements Map.Entry<K,V> {
        final K key;
        V value;
        Entry<K,V> next;//存储指向下一个Entry的引用，单链表结构
        int hash;//对key的hashcode值进行hash运算后得到的值，存储在Entry，避免重复计算

        /**
         * Creates new entry.
         */
        Entry(int h, K k, V v, Entry<K,V> n) {
            value = v;
            next = n;
            key = k;
            hash = h;
        }
```

java1.8后hashmap的储存下标的计算步骤，高16位异或低16位

![img](https://img-blog.csdn.net/20180721235229659?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3YxMjM0MTE3Mzk=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)



1.8后hashmap结构变成，底层实现由之前的“数组+链表”改为“数组+链表+红黑树”，只有当链表8个以上才变成红黑树，而且在64容量之前，不会出现红黑树，达到8个只会扩容2倍

## treeifyBin方法扩容

## treeify方法构建红黑树

