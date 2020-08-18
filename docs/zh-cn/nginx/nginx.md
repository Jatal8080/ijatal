```nginx
# 测试配置文件是否有语法错误
/usr/sbin/nginx -t
# 查看服务状态
systemctl status nginx.service
# 刷新nginx配置，重启服务
systemctl restart nginx.service
# 刷新nginx配置
nginx -s reload

# 其他命令
start nginx：打开 nginx
nginx -s reopen：重启Nginx
nginx -s reload：重新加载Nginx配置文件，然后以优雅的方式重启Nginx
nginx -s stop：强制停止Nginx服务
nginx -s quit：优雅地停止Nginx服务（即处理完所有请求后再停止服务

```

#### 安装nginx过程中报错：

./configure: error: the HTTP rewrite module requires the PCRE library.

安装pcre-devel解决问题
yum -y install pcre-devel

 

错误提示：./configure: error: the HTTP cache module requires md5 functions
from OpenSSL library.   You can either disable the module by using
--without-http-cache option, or install the OpenSSL library into the system,
or build the OpenSSL library statically from the source with nginx by using
--with-http_ssl_module --with-openssl=<path> options.

解决办法：

yum -y install openssl openssl-devel

 

总结：

yum -y install pcre-devel openssl openssl-devel

./configure --prefix=/usr/local/nginx

make

make install

#### nginx问题查找记录：

1. 查找错误位置

grep "error_log" /etc/nginx/* -R



2. 查看错误日志

例：tail -n 10 /var/log/nginx/error.log



3. 可以看到许多 (13: Permission denied) while connecting 错误，而这个错误一般是由SELinux引起的

(13: Permission denied) while connecting to upstream:[nginx]

4. 输入
setsebool -P httpd_can_network_connect 1
