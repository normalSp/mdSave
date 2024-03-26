# 1. Spring Cache介绍

![image-20240326164334735](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240326164334735.png)

![image-20240326164450513](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240326164450513.png)

```java
/**
 * CachePut：将方法返回值放入缓存
 * value：缓存的名称，每个缓存名称下面可以有多个key
 * key：缓存的key
 */
@CachePut(value = "userCache",key = "#user.id")
@PostMapping
public User save(User user){
    userService.save(user);
    return user;
}
```

```java
/**
 * CacheEvict：清理指定缓存
 * value：缓存的名称，每个缓存名称下面可以有多个key
 * key：缓存的key
 * p0、root.args[0]代表获取方法第一个参数
 */
@CacheEvict(value = "userCache",key = "#p0")
//@CacheEvict(value = "userCache",key = "#root.args[0]") 
//@CacheEvict(value = "userCache",key = "#id")
@DeleteMapping("/{id}")
public void delete(@PathVariable Long id){
    userService.removeById(id);
}
```

```java
/**
 * Cacheable：在方法执行前spring先查看缓存中是否有数据，如果有数据，则直接返回缓存数据；若没有数据，调用方法并将方法返回值放到缓存中
 * value：缓存的名称，每个缓存名称下面可以有多个key
 * key：缓存的key
 * condition：条件，满足条件时才缓存数据
 * unless：满足条件则不缓存
 */
@Cacheable(value = "userCache",key = "#id",unless = "#result == null")
@GetMapping("/{id}")
public User getById(@PathVariable Long id){
    User user = userService.getById(id);
    return user;
}
```



# 2. Spring Cache 使用方法

![image-20240326171411112](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240326171411112.png)