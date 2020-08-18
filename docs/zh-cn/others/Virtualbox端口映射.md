### 通过虚拟机端口转发（端口映射）进行远程访问


#### 前言
本文各电脑均在统一网段内，如果是公司的网络，应该可以保证全部电脑都在同一网段中的

#### 所用机器
通过virtualbox安装的一台ubuntu虚拟机(ip:1.0.7.8)
宿主机（Ip:1.2.3.4）
电脑1(ip:1.2.3.5)

#### 操作步骤
##### 1.设置-网络-连接方式（NAT）-高级-端口转发

![这里写图片描述](https://img-blog.csdn.net/20180802180646913?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zNzIyODk3Nw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

![这里写图片描述](https://img-blog.csdn.net/20180802180710866?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zNzIyODk3Nw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##### 2.右侧加号新增一条端口转发规则
主机ip:1.2.3.4 （通过cmd-ipconfig可获得）
主机端口：2333 需要填写一条宿主机未被占用的端口号
子系统ip:1.0.7.8 (ubuntu通过terminal-ifconfig获得)
子系统端口：8080 填写的是虚拟机需要被转发的一个端口号（这里选择Tomcat默认端口号，当然，实际得看你的项目所在的Tomcat用的哪个端口）
（这里之所以不用填写主机IP和子系统IP是因为主机和子系统对应的是同一台电脑上的宿主机和虚拟机，所以localhost可以自动获取）
点击ok确认~~

![这里写图片描述](https://img-blog.csdn.net/20180802180816250?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zNzIyODk3Nw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##### 3.可以开始访问啦
虚拟机和宿主机只需要localhost就可以访问，其他电脑需要用宿主机的ip地址

| 机器名 | IP      | 访问地址              |
| ------ | ------- | --------------------- |
| 虚拟机 | 1.0.7.8 | localhost:8080/项目名 |
| 宿主机 | 1.2.3.4 | localhost:2333/项目名 |
| 电脑1  | 1.2.3.5 | 1.2.3.4:2333/项目名   |

​		



后续整理：

![image-20200714103831857](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200714103831857.png)



![image-20200714103906837](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200714103906837.png)



![image-20200714103923445](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200714103923445.png)



![image-20200714103934644](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200714103934644.png)



![image-20200714103850324](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200714103850324.png)





