	
	容器我们从几个方面去学习它，整体架构，增删改查。


## 整体架构
	
	双向链表

![整体架构](https://camo.githubusercontent.com/23195b49d138a1a43ae146469123026b0f38ebf57a2fc5f911d4b8b0be75163d/68747470733a2f2f646576796b2e6f73732d636e2d71696e6764616f2e616c6979756e63732e636f6d2f626c6f672f32303230303332373137303731302e6a706567)


	为什么叫链表，可以想象成那种链子，环环相扣，每个链子都有头个尾，中间是它的内容，这样环环相扣形成一个锁链，还可以想想成

![大概这个样子](./img/201510301446149081308_8.jpeg)

![锁链](https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg1.cache.netease.com%2Fcatchpic%2F4%2F41%2F41597A58C478A659BA5A4D37291B4165.jpg&refer=http%3A%2F%2Fimg1.cache.netease.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1628402367&t=2322d7d103364199acabf1a2ca83f1a6)
	可以把链表分成两部分

### 整体
		
	整条锁链看成一体，也就是new LinkedList(),这个里面管理链表本身数据，还有增删改查的一系列操作。只需要记录，first 和 last 还有本身的大小size,

```java
	LinkedList linkedList = new LinkedList()

class LinkedList<E>{
	Node<E> first;
	Node<E> last;
	int size;
}
```

### 链扣(Node)
	
	可以想想一个🔗如果想把它变成链子，我们需要链接，我们需要链接上前面一个链扣，和后面一个链扣才能实现真正的链接
	其中prev 代表前一个链接，next代表下一个链接

```java

class Node<E>{
	 Node<E> prev;
	 Node<E> next;
	 E item;	//链扣里面的具体内容
}

```

### 添加
![添加](https://camo.githubusercontent.com/a4a172833e5e8556e43da9c97925e73f203d300883c5e94b1fe6113e96bfda54/68747470733a2f2f646576796b2e6f73732d636e2d71696e6764616f2e616c6979756e63732e636f6d2f626c6f672f32303230303332373137303831342e676966)
	
	想象一下链子平铺，我们如果想添加一个链扣，我们怎么做最省事？ 头部添加，就是把新的链扣尾巴添加到first链表的prev上面，这样新添加的链扣就变成了prev链，尾部添加也一样。

1. 头链添加
```java

void linkFirst(node){
	Node tmpNode = first.prev;
	tmpNode.prev = node;		//
	node.next = tmpNode;
	first = node;
	size++;
	modCount++;

```

2. 尾部添加
```java
void linkLast(Node){
	
}
```


### 删除

	把一个完整的链子其中一个链扣去掉我们该怎么做？
	1. 找到那个链扣
	2. 找到那个链扣上一一节和下一节
	3. 断开上一节链扣的next,和下一节链扣的prev
	4. 把上一节链扣的next 接到下一节上面， 下一节prev接到上一节上面，找到那个链扣不用管它，值为空，等待gc回收，自动消失。

	








