# Future

```java
package io.netty.util.concurrent;

public interface Future<V> extends java.util.concurrent.Future<V> {
	//...
}
```

Netty中的Future继承至`java.util.concurrent.Future`，用于**获取异步操作的结果**。

`java.util.concurrent.Future`接口中定义的方法如下：

| 返回类型 |               方法名称                |                           方法说明                           |
| :------: | :-----------------------------------: | :----------------------------------------------------------: |
| boolean  | cancel(boolean mayInterruptIfRunning) |                      尝试取消执行此任务                      |
|    V     |                 get()                 |                 等待计算完成，然后检索其结果                 |
|    V     |   get(long timeout, TimeUnit unit)    | 如果需要等待最多在给定的时间计算完成，然后检索其结果（如果可用） |
| boolean  |             isCancelled()             |         如果此任务在正常完成之前被取消，则返回`true`         |
| boolean  |               isDone()                |                   返回`true`如果任务已完成                   |

## Future实现类

Future实现类关系图如下

### AbstractFuture

### ChannelFuture



# Promise

