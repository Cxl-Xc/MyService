CentOs配置mysql

上传到根目录下 并解压

~~~java
tar -xvf mysql-8.0.13-1.el7.x86_64.rpm-bundle.tar
~~~

删除tar

~~~java
rm -rf *.tar
~~~

运行

~~~java
rpm -qa | grep mariadb
    
rpm -e mariadb-libs-5.5.68-1.el7.x86_64   --nodeps
    
yum -y install perl
    
rpm -ivh mysql-community-common-8.0.13-1.el7.x86_64.rpm 

rpm -ivh mysql-community-libs-8.0.13-1.el7.x86_64.rpm 
    
rpm -ivh mysql-community-client-8.0.13-1.el7.x86_64.rpm
    
rpm -ivh mysql-community-server-8.0.13-1.el7.x86_64.rpm
~~~

启动服务

~~~java
systemctl status mysqld
~~~

查看密码

~~~java
cat /var/log/mysqld.log | grep password
~~~

输入密码进入mysql

~~~java
mysql -uroot -p
~~~

修改密码

~~~java
ALTER USER 'root'@'localhost' IDENTIFIED BY '2020YYzsa!';
~~~

设置MYSQL可以远程登录

~~~java
update user set host ='%' where user='root';
flush privileges;
~~~







网址

~~~java
https://www.bilibili.com/video/BV1nZ4y1z7AW?spm_id_from=333.880.my_history.page.click
~~~





解决连接报错

~~~java
https://blog.csdn.net/m0_67403076/article/details/124105954
~~~

