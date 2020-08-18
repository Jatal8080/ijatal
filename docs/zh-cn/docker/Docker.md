#### Docker常用命令：

```dockerfile
# 查看docker镜像
docker images
# 查看docker容器
docker ps -a
#
docker ps
# 启动、停止、重启docker
systemctl start docker
systemctl stop docker
systemctl restart docker
# 启动某docker容器
docker start test
# 删除某docker容器
docker rm test_id
# 删除某docker镜像
```



#### 一.Docker安装mysql 5.7

1. 查看mysql镜像包 `docker search mysql`

2. 选择一个mysql版本并安装

   ```
   docker pull mysql:5.7
   ```

3. 查看docker容器命令：`docker images `,你会发现mysql5.7已经安装完毕。

4. 运行myql容器

   ```properties
   # 启动mysql实例
   # --name 为mysql的实例设置别名
   # -p 3307 为对外暴露的端口，3306是内部端口
   # -e MYSQL_ROOT_PASSWORD 设置mysql登录密码 
   # -d 以守护进程运行（后台运行）
   # 最后的 mysql 是镜像名称
   docker run -p 3307:3306 -d --name mysql57 -v /docker/mysql/data:/usr/share/mysql -e MYSQL_ROOT_PASSWORD=123456 mysql:5.7
   ```

5. docker操作mysql

   ```properties
   # 查看在运行的
   docker ps
   # 输入命令, mysql57 是上边运行时为容器取的别名 也可以用id替代
   docker exec -it mysql57 bash
   # 输入密码连接mysql进行操作
   mysql -uroot -p
   ```

   

   1. 输入命令 `docker exec -it mysql57 bash`
   2. `mysql -uroot -p` 输入密码连接mysql进行操作。

#### 二.Docker安装redis

1. 安装redis镜像 `docker pull redis:3.2`

2. 运行redis容器

   ​                        

   ```properties
   docker run -p 6379:6379 -d --name myredis -v /docker/redis/data:/data redis:3.2 redis-server --appendonly yes
   ```

3. docker操作redis `docker exec -it myredis redis-cli`



#### 三.Docker部署springboot项目                      (待后续完善)

- springboot项目打包为jar包,上传到服务器。

- docker创建项目镜像以及容器，并启动容器

  > 注意：项目中的端口号、mysql配置密码等应当与服务器上一致

##### 1. 打包springboot项目

这里就不详细说了，请参考:

- [springboot项目打包成jar,同时解析jar](https://blog.csdn.net/my_ha_ha/article/details/94183113)
- [springboot打包部署](https://blog.csdn.net/qq_35618489/article/details/88228360).

##### 2. docker生成项目镜像和容器

1. 安装docker `yum -y install docker`

2. 启动docker `service docker start`

3. 安装JDK8镜像 `docker pull java:8`

4. 创建Dockerfile文件生成镜像`sudo vim Dockerfile`

   ​                        

   ```
   创建镜像文件docker默认必须是Dockerfile,路径任意
   ```

   ```
   FROM java:8
      
   COPY springcloud-2.0-eureka-server.jar app.jar
      
   EXPOSE 8080
      
   ENTRYPOINT ["java","-jar","/app.jar","--spring.profiles.active=prod"]
   ```

5. 生成镜像 `docker build -t test` (test为任意名字)

6. 创建容器 `docker create --name test -t -p 8010:8010 test `

7. 启动容器 `docker start test`

8. 查看启动日志 `docker logs -f test`

参考链接：

- [SpringBoot生成docker镜像，完成容器部署](https://blog.csdn.net/qq_35618489/article/details/88232406)
- [docker安装mysql和redis](https://www.cnblogs.com/codehui/p/docker_mysql_redis.html)
- [Docker镜像和容器的导入与导出](https://www.jianshu.com/p/4e862a2a2d03)



# Docker修改mysql映射端口

操作步骤：

1、停止docker

#systemctl  stop docker

2、修改mysql容器hostconfig.json文件、如下图

![img](https://img-blog.csdnimg.cn/20190216103415709.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Nzd3F6eA==,size_16,color_FFFFFF,t_70)

```
vi  hostconfig.json 
```

3306/tcp是容器端口, HostPort是宿主机端口.

![img](https://img-blog.csdnimg.cn/20190216103521109.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Nzd3F6eA==,size_16,color_FFFFFF,t_70)

3、 启动docker服务(systemctl start docker)
4、启动容器、测试mysql连接。

#### 其他相关：

- [docker部署mysql 并实现远程连接（navicat）](https://blog.csdn.net/tyt_XiaoTao/article/details/84621087?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.compare&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.compare)


- [CentOS7-Docker 配置国内镜像源](https://www.cnblogs.com/reasonzzy/p/11127359.html)