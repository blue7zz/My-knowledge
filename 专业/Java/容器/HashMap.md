# HashMap

## 整体架构
		
		数组(链表+红黑树)
		当链表长度>=8，数组>64时，将链表转换为红黑树
		链表长度<6时，红黑树转换成链表(这句话？？？)

![图片](https://camo.githubusercontent.com/5f0798b39e94a0a9a8eec65f37083d741b105c64d626928fdeb9f7666d6efdb1/68747470733a2f2f646576796b2e6f73732d636e2d71696e6764616f2e616c6979756e63732e636f6d2f626c6f672f32303230303332373137303331392e6a706567)

	图中左边竖着的是 HashMap 的数组结构，数组的元素可能是单个 Node，也可能是个链表，也可能是个红黑树，比如数组下标索引为 2 的位置就是一个链表，下标索引为 9 的位置对应的就是红黑树，具体细节我们下文再说。

## 类
	1. 影响因子，默认值是）0.75  均衡了时间和空间损耗算出来的值， 不扩容的条件:数组容量>需要的数组大小/load factor(影响因子)
### 常见属性

```Java
//初始容量为 16
 static final int DEFAULT_INITIAL_CAPACITY = 1 << 4;

 //最大容量
 static final int MAXIMUM_CAPACITY = 1 << 30;

 //负载因子默认值
 static final float DEFAULT_LOAD_FACTOR = 0.75f;
 
 //桶上的链表长度大于等于8时，链表转化成红黑树
 static final int TREEIFY_THRESHOLD = 8;

 //桶上的红黑树大小小于等于6时，红黑树转化成链表
 static final int UNTREEIFY_THRESHOLD = 6;

 //当数组容量大于 64 时，链表才会转化成红黑树
 static final int MIN_TREEIFY_CAPACITY = 64;

 //记录迭代过程中 HashMap 结构是否发生变化，如果有变化，迭代时会 fail-fast
 transient int modCount;

 //HashMap 的实际大小，可能不准(因为当你拿到这个值的时候，可能又发生了变化)
 transient int size;

 //存放数据的数组
 transient Node<K,V>[] table;

 // 扩容的门槛，有两种情况
 // 如果初始化时，给定数组大小的话，通过 tableSizeFor 方法计算，数组大小永远接近于 2 的幂次方，比如你给定初始化大小 19，实际上初始化大小为 32，为 2 的 5 次方。
 // 如果是通过 resize 方法进行扩容，大小 = 数组容量 * 0.75
 int threshold;

 //链表的节点
 static class Node<K,V> implements Map.Entry<K,V> {
 
 //红黑树的节点
 static final class TreeNode<K,V> extends LinkedHashMap.Entry<K,V> {

```


## 添加
## 删除
## 查找
