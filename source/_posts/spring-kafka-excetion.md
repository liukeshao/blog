---
title: spring kafka 异常处理
date: 2018-03-22 16:24:25
categories:
  - spring
tags:
  - spring kafka consumer error 
  - spring kafka producer error 
---

spring  kafka 1.x consumer and producer 异常处理

<!-- more -->

spring kafka version 1.3.3

## consumer 异常处理：

consumer 使用 @KafkaListener 注解

`@KafkaListener(topics={"kafka"}, errorHandler="myKafkaListenerErrorHandler")`

指定 `errorHandler` 属性，值需要是spring bean

实现 `KafkaListenerErrorHandler` 接口

```java
@Component
public class MyKafkaListenerErrorHandler implements KafkaListenerErrorHandler {
    
    @Override
    public Object handleError(Message<?> message, ListenerExecutionFailedException exception) throws Exception {
		// 这里做失败处理
        // 接口返回值会被忽略，所以不需要处理
        // @return the return value is ignored.
        return null;
    }
}

```



## producer 异常处理：

实现 `ProducerListener` 接口的 `onError` 接口

> ProducerListenerAdapter 是 ProducerListener 的空实现

```java
public class MyProducerListener<K, V> extends ProducerListenerAdapter<K, V> {
  
    @Override
    public void onError(String topic, Integer partition, K key, V value, Exception exception) {
  		// 这里做失败处理
    }
}

```

在需要的的覅方，替换 `kafkaTemplate ` 默认的 `ProducerListener`

```java
kafkaTemplate.setProducerListener(new MyProducerListener<>());
```

> 我使用的是 spring boot，利用spring boot 的 CommandLineRunner 接口，在启动完成后，将kafkaTemplate 默认的 ProducerListener 替换成自己的实现

```java
@Component
public class InitKafkaTemplate implements CommandLineRunner {

    @Autowired
    private KafkaTemplate<String, String> kafkaTemplate;
    
    @Override
    public void run(String... strings) throws Exception {
        kafkaTemplate.setProducerListener(new MyProducerListener<>());
    }
}
```

