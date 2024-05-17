# Redisson
Redisson是一个在Redis的基础上实现的Java驻内存数据网格（In-Memory Data Grid）。它不仅提供了一系列的分布式的Java常用对象，还提供了许多分布式服务，其中就包含了各种分布式锁的实现。

## 引入依赖

```xml
<dependency>
    <groupId>org.redisson</groupId>
    <artifactId>redisson</artifactId>
    <version>3.17.7</version>
</dependency>
```
## 配置Redisson客户端


```java
@Configuration
public class RedisConfig {
    @Bean    
    public RedissonClient redissonClient() {
        // 配置类
        Config config = new Config();
        // 添加redis地址，这里添加了单点的地址，也可以使用config.useClusterServers()添加集群地址         
        config.useSingleServer().setAddress("redis://172.18.84.81:6379");        
        // 创建客户端        
        return Redisson.create(config);    
    }
}


```

## 使用Redisson分布式锁
```java
@Resource
private RedissonClient redissonClient;
@Test
void testRedisson() throws InterruptedException {
    // 获取锁（可重入），指定锁的名称
    RLock lock = redissonClient.getLock("anyLock");   
     // 尝试获取锁，参数分别是：获取锁的最大等待时间（期间会重试），锁自动释放时间，时间单位
    boolean isLock = lock.tryLock(1, 10, TimeUnit.SECONDS);    
    // 判断释放获取成功    
    if(isLock){       
         try {            
             System.out.println("执行业务");        
         }finally {            
             // 释放锁           
             lock.unlock();
         }    
    }
}
```