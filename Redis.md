# 1. redis 入门

![image-20240325170707457](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325170707457.png)



## 1.1 下载与安装

![image-20240325170746046](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325170746046.png)

![image-20240325171035989](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325171035989.png)



## 1.2 启动与停止

![image-20240325171659627](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325171659627.png)

**设置后台运行：**

在 redis 文件根目录的 redis.conf 中的 daemonize 设为yes

运行时使用该配置文件：/usr/local/redis-4.0.0/src/redis-server ./redis.conf 



**进入服务：**

进入 redis 根目录下的 src 文件，运行 redis-cli 文件



**设置密码：**

在 redis.conf  文件中添加 requestpass <密码>



**登录：**

![image-20240326135409217](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240326135409217.png)

auth  <密码>

或者

![image-20240326135505123](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240326135505123.png)

-h 域名

-p 端口号

-a 密码



**远程连接：**

在redis.conf  文件中将 bind 127.0.0.1 注释

windows下连接： .\redis-cli.exe -h 39.106.77.183 -p 6379 -a 565034470 



## 1.3 redis 数据类型

![image-20240326140249856](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240326140249856.png)

![image-20240326140304119](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240326140304119.png)



# 2. redis 常用命令

![image-20240326140549883](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240326140549883.png)

- **string：**

![image-20240326140851976](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240326140851976.png)



- **hash：**

![image-20240326141422255](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240326141422255.png)



- **list：**

![image-20240326141922537](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240326141922537.png)

lrange list 0 -1 ：从头查到尾



- **set：**

![image-20240326142506072](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240326142506072.png)



- **sorted set**

![image-20240326142653541](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240326142653541.png)



- **通用命令**

![image-20240326142611567](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240326142611567.png)

select <数据库号>

默认配置了16个数据库，可以在 redis.conf 中修改：

![image-20240326144241180](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240326144241180.png)



# 3. 在 Java 中操作 redis

![image-20240326143208077](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240326143208077.png)

## 3.1 使用 Jedis 

```java
package com.itheima.test;

import org.junit.Test;
import redis.clients.jedis.Jedis;

import java.util.Set;

/**
 * 使用Jedis操作Redis
 */
public class JedisTest {

    @Test
    public void testRedis(){
        //1 获取连接
        Jedis jedis = new Jedis("39.106.77.183",6379);

        // 身份验证
        jedis.auth("565034470");

        //2 执行具体的操作
        jedis.set("username","xiaoming");

        String value = jedis.get("username");
        System.out.println(value);

        //jedis.del("username");

        jedis.hset("myhash","addr","bj");
        String hValue = jedis.hget("myhash", "addr");
        System.out.println(hValue);

        Set<String> keys = jedis.keys("*");
        for (String key : keys) {
            System.out.println(key);
        }

        //3 关闭连接
        jedis.close();
    }
}
```



## 3.2 使用 Spring Data Redis 

![image-20240326143800368](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240326143800368.png)

![image-20240326143903165](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240326143903165.png)

```java
package com.itheima.test;

import org.junit.Test;
import org.junit.runner.RunWith;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.data.redis.connection.DataType;
import org.springframework.data.redis.core.*;
import org.springframework.test.context.junit4.SpringRunner;

import java.util.List;
import java.util.Set;
import java.util.concurrent.TimeUnit;

@SpringBootTest
@RunWith(SpringRunner.class)
public class SpringDataRedisTest {

    @Autowired
    private RedisTemplate redisTemplate;

    /**
     * 操作String类型数据
     */
    @Test
    public void testString(){
        redisTemplate.opsForValue().set("city123","beijing");

        String value = (String) redisTemplate.opsForValue().get("city123");
        System.out.println(value);

        redisTemplate.opsForValue().set("key1","value1",10l, TimeUnit.SECONDS);

        Boolean aBoolean = redisTemplate.opsForValue().setIfAbsent("city1234", "nanjing");
        System.out.println(aBoolean);
    }

    /**
     * 操作Hash类型数据
     */
    @Test
    public void testHash(){
        HashOperations hashOperations = redisTemplate.opsForHash();

        //存值
        hashOperations.put("002","name","xiaoming");
        hashOperations.put("002","age","20");
        hashOperations.put("002","address","bj");

        //取值
        String age = (String) hashOperations.get("002", "age");
        System.out.println(age);

        //获得hash结构中的所有字段
        Set keys = hashOperations.keys("002");
        for (Object key : keys) {
            System.out.println(key);
        }

        //获得hash结构中的所有值
        List values = hashOperations.values("002");
        for (Object value : values) {
            System.out.println(value);
        }
    }

    /**
     * 操作List类型的数据
     */
    @Test
    public void testList(){
        ListOperations listOperations = redisTemplate.opsForList();

        //存值
        listOperations.leftPush("mylist","a");
        listOperations.leftPushAll("mylist","b","c","d");

        //取值
        List<String> mylist = listOperations.range("mylist", 0, -1);
        for (String value : mylist) {
            System.out.println(value);
        }

        //获得列表长度 llen
        Long size = listOperations.size("mylist");
        int lSize = size.intValue();
        for (int i = 0; i < lSize; i++) {
            //出队列
            String element = (String) listOperations.rightPop("mylist");
            System.out.println(element);
        }
    }

    /**
     * 操作Set类型的数据
     */
    @Test
    public void testSet(){
        SetOperations setOperations = redisTemplate.opsForSet();

        //存值
        setOperations.add("myset","a","b","c","a");

        //取值
        Set<String> myset = setOperations.members("myset");
        for (String o : myset) {
            System.out.println(o);
        }

        //删除成员
        setOperations.remove("myset","a","b");

        //取值
        myset = setOperations.members("myset");
        for (String o : myset) {
            System.out.println(o);
        }

    }

    /**
     * 操作ZSet类型的数据
     */
    @Test
    public void testZset(){
        ZSetOperations zSetOperations = redisTemplate.opsForZSet();

        //存值
        zSetOperations.add("myZset","a",10.0);
        zSetOperations.add("myZset","b",11.0);
        zSetOperations.add("myZset","c",12.0);
        zSetOperations.add("myZset","a",13.0);

        //取值
        Set<String> myZset = zSetOperations.range("myZset", 0, -1);
        for (String s : myZset) {
            System.out.println(s);
        }

        //修改分数
        zSetOperations.incrementScore("myZset","b",20.0);

        //取值
        myZset = zSetOperations.range("myZset", 0, -1);
        for (String s : myZset) {
            System.out.println(s);
        }

        //删除成员
        zSetOperations.remove("myZset","a","b");

        //取值
        myZset = zSetOperations.range("myZset", 0, -1);
        for (String s : myZset) {
            System.out.println(s);
        }
    }

    /**
     * 通用操作，针对不同的数据类型都可以操作
     */
    @Test
    public void testCommon(){
        //获取Redis中所有的key
        Set<String> keys = redisTemplate.keys("*");
        for (String key : keys) {
            System.out.println(key);
        }

        //判断某个key是否存在
        Boolean itcast = redisTemplate.hasKey("itcast");
        System.out.println(itcast);

        //删除指定key
        redisTemplate.delete("myZset");

        //获取指定key对应的value的数据类型
        DataType dataType = redisTemplate.type("myset");
        System.out.println(dataType.name());

    }
}
```

```yml
spring:
  application:
    name: springdataredis_demo
  #Redis相关配置
  redis:
    host: 39.106.77.183
    port: 6379
    password: 565034470
    database: 0 #操作的是0号数据库
    jedis:
      #Redis连接池配置
      pool:
        max-active: 8 #最大连接数
        max-wait: 1ms #连接池最大阻塞等待时间
        max-idle: 4 #连接池中的最大空闲连接
        min-idle: 0 #连接池中的最小空闲连接
```

只要配置了就能自动注入 

```java
@Autowired
private RedisTemplate redisTemplate;
```

默认写入 redis 的 key 会变形，若像保持正常，需要配置类：

```java
package com.itheima.config;

import org.springframework.cache.annotation.CachingConfigurerSupport;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.data.redis.connection.RedisConnectionFactory;
import org.springframework.data.redis.core.RedisTemplate;
import org.springframework.data.redis.serializer.StringRedisSerializer;

/**
 * Redis配置类
 */

@Configuration
public class RedisConfig extends CachingConfigurerSupport {

    @Bean
    public RedisTemplate<Object, Object> redisTemplate(RedisConnectionFactory connectionFactory) {

        RedisTemplate<Object, Object> redisTemplate = new RedisTemplate<>();

        //默认的Key序列化器为：JdkSerializationRedisSerializer
        redisTemplate.setKeySerializer(new StringRedisSerializer());
        redisTemplate.setHashKeySerializer(new StringRedisSerializer());

        redisTemplate.setConnectionFactory(connectionFactory);

        return redisTemplate;
    }

}
```

value 的序列化保持默认就行，因为 java 程序写入读出的时候会自动序列号。
