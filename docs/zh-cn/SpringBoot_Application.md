# SpringBoot 配置文件 

SpringBoot的配置文件有两种类型：一种是properties结尾的，一种是yml文件结尾的。
## 区别

yml文件的好处就是有着一目了然树状结构，但两者本质上是差不多的，只是官方给的demo，大多都是用yml文件配置的。

## 优先级
`.properties文件 > .yml文件 ` 

如果你的工程中同时存在application.properties和 application.yml两种配置文件，yml文件会先加载，而后加载的properties文件会覆盖yml文件。你可以试一下在两个文件中配置不同的端口号，最后你会发现读取的是properties的中端口号， 所以选用其中一种类型的文件即可。

## application.yml 文件配置方式

```yaml
server:
      port: 8088
spring:
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://106.53.76.229:3306/proname?useUnicode=true&characterEncoding=utf-8&useSSL=false&serverTimezone=GMT
    username: Jatal
    password: Jatal@123
  redis:
    host: 106.53.76.229
    port: 6379
    password: Jatal@123
    timeout: 1500
    jedis:
      pool:
        max-active: 8
        max-wait: -1
        max-idle: 8
        min-idle: 0
mybatis:
  mapper-locations: classpath:mapper/*Mapper.xml
```



## application.properties文件配置方式

```properties
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql://106.53.76.229:3306/proname?useUnicode=true&characterEncoding=utf-8&useSSL=false&serverTimezone=GMT
spring.datasource.username=Jatal
spring.datasource.password=Jatal@123

spring.redis.host=106.53.76.229
spring.redis.port=6379
spring.redis.password=Jatal@123

mybatis.mapper-locations=classpath: mapper/*.xml
```

##### 这里提供一个这两种文件的转换地址：[http://www.toyaml.com](http://www.toyaml.com/)