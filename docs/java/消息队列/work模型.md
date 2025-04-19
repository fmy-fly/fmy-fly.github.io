# work模型

!!! 定义
    Work queue,任务模型。让多个消费者绑定到一个队列，共同消费队列中的消息。


## 消费者代码

```java

@Slf4j
@Component
public class MqListeners {

    @RabbitListener(queues = "work") // 启动多个消费者线程
    public void listenSimpleQueue1(String msg) throws InterruptedException {
        System.out.println("消费者1 收到了work的消息：[" + msg + "]" );
   
    }


    @RabbitListener(queues = "work") // 启动多个消费者线程
    public void listenSimpleQueue2(String msg) throws InterruptedException {
        System.err.println("消费者2 收到了work的消息。。。：[" + msg + "]" );
    }
}
```
## 生产者代码


```java
@Test
void testWorkQueue() throws InterruptedException {
    String queueName = "work";
    for (int i = 1; i <= 50; i++) {
        String msg = "hello world， " + i;
        rabbitTemplate.convertAndSend(queueName, msg);
        Thread.sleep(20);
    }
}
```


## 消费者消息推送机制
默认情况下，RabbitMQ的会将消息依次轮询投递给队列上的每一个消费者。但这并没有考虑到消费者是否已经处理完消息，可能出现**消息堆积**。

因此我们需要修改application.yml，设置preFetch值为1，确保同一时刻最多投递给消费者1条消息。处理快的人可以多处理。

```yaml
spring:
  rabbitmq:
    host: 127.0.0.1
    port: 5672
    virtual-host: /hmall
    username: fmy
    password: 123456

    listener:
      simple:
        prefetch: 1

```

## work模型的使用

- 多个消费者绑定到一个队列，可以加快消息处理速度
- 同一条消息只会被一个消费者处理
- 通过设置prefetch来控制消费者预取的消息数量，处理完一条再处理下一条，实现能者多劳
