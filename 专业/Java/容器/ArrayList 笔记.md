
	只是用于学习记录，主要内容还是来自学习资料



**学习**


整体架构

![图片](./img/68747470733a2f2f646576796b2e6f73732d636e2d71696e6764616f2e616c6979756e63732e636f6d2f626c6f672f32303230303332373136353233312e6a706567.jpeg)

注释
	允许pull null值，会自动扩容
	时间复杂度都是O(1)
	线程非安全的
	增强for循环或使用迭代器迭代过程中，如果数组大小被改变，会快速失败，抛出异常



源码解析
	初始化
		1. 无参数直接初始化
			- 无参数初始化，默认大小是空数组，10是在第一次add时候扩容的数组值。
		2. 指定大小初始化
		3. 指定初始化数据初始化
			- 
			- 
	新增和扩容实现
		1. 判断是否需要扩容，如果需要执行扩容操作。
	扩容的本质
	删除
	迭代器
		hasNext
		next
		remove
	时间复杂度
	线程安全




## 链接
[ArrayList](https://github.com/yangkun19921001/Blog/blob/master/%E7%AC%94%E8%AF%95%E9%9D%A2%E8%AF%95/Android%E9%AB%98%E7%BA%A7%E5%B7%A5%E7%A8%8B%E5%B8%88%E9%9D%A2%E8%AF%95%E5%BF%85%E5%A4%87/Java/%E5%AE%B9%E5%99%A8/ArrayList.md)
[时间复杂度](https://www.zhihu.com/search?type=content&q=%E6%97%B6%E9%97%B4%E5%A4%8D%E6%9D%82%E5%BA%A6%E2%80%9CO%E2%80%9D)
