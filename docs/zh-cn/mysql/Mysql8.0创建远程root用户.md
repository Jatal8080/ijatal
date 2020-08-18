# Mysql 8 使用mysql_native_password加密方式创建远程用户

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200420104510145.png" alt="image-20200420104510145" style="zoom:70%;" />

#### mysql 8.0 修改了加密的插件方式(mysql8使用了caching_sha2_password的加密方式，mysql5用的是sha256_password加密方式，所以导致mysql8连接时报错。)，导致很多旧版本的navicat无法正常访问。为了方便访问，创建一个原来加密方式的账号。

```mysql
create user 'Jatal'@'%' identified  by 'Jatal@123';
grant all on *.* to 'Jatal'@'%';
alter user 'Jatal'@'%' identified  with mysql_native_password by 'Jatal@123';
flush privileges;
```

#### 1.创建用户

####  `create user 'Jatal'@'%' identified  by 'Jatal@123'`;

#### 2.用户授权

#### grant all on *.* to 'Jatal'@'%';

#### 3.修改成原来的加密方式

#### alter user 'Jatal'@'%' identified  with mysql_native_password by 'Jatal@123';

#### 4.刷新MySQL系统权限相关表

#### flush privileges;