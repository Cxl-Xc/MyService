CentOs配置jdk



卸载服务器自带的openjdk

先检查是否有自带的jdk

~~~java
rpm	-qa|grep jdk
~~~

如果有 先卸载

下载安装包 上传到服务器	/opt目录下

解压压缩包

~~~java
tar -zxvf jdk-11.0.13_linux-x64_bin.tar.gz
~~~

移动到 /usr/local目录下

~~~java
mv jdk-11.0.13 /usr/local
~~~

配置环境变量

~~~java
vim /etc/profile
~~~

按I进入编辑模式

~~~java
#在文件底部插入
    export JAVA_HOME=/usr/local/jdk-11.0.13
    export
    CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
    export PATH=$PATH:$JAVA_HOME/bin
~~~

点击ESC  SHIFT+冒号 wq

使配置文件立即生效

~~~java
source /etc/profile
~~~









### 第一步 卸载openjdk

```shell
# 查看服务器是否有安装openjdk
rpm -qa|grep jdk

# 卸载
rpm -e --nodeps java-1.8.0-openjdk-1.8.0.242.b08-1.el7.x86_64
rpm -e --nodeps java-1.7.0-openjdk-1.7.0.251-2.6.21.1.el7.x86_64
rpm -e --nodeps java-1.8.0-openjdk-headless-1.8.0.242.b08-1.el7.x86_64
rpm -e --nodeps java-1.7.0-openjdk-headless-1.7.0.251-2.6.21.1.el7.x86_64

# 验证
rpm -qa|grep java
?这个命令输入过后会看到还有三个java相关的东西存在，可以不用管
java -version
?这个命令输入过后，看不到java的版本了的话，就表示卸载成功了，如果，还能看到版本号，那一定是什么地方出了问题。
```

 

### 第二步 下载jdk安装包到本地

```shell
https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html
```

到这个网址去下载jdk1.8的压缩包，如果没有注册过的小伙伴需要先注册这个网站的会员才能进行下载。

 

### 第三步 上传安装包到服务器

```shell
# 通过filezilla把jdk安装包上传到服务器的文件夹
https://www.filezilla.cn/

# 我这里就上传到
/opt
```

 

### 第四步 解压到你想要的安装路径

```shell
# 解压
tar -zxvf jdk-8u251-linux-x64.tar.gz
# 移动
mv jdk1.8.0_251 /usr/local
```

### 第五步 配置环境变量

```shell
# 编辑配置文件
vim /etc/profile

# 在文件底部插入
export JAVA_HOME=/usr/local/jdk1.8.0_251
export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin

# 使配置文件立即生效
source /etc/profile
```

 

### 第六步 验证安装结果

```shell
java -version
```

如果可以看到java的版本号，说明安装成功，大功告成！









~~~java
网址：https://www.bilibili.com/video/BV1W5411a7uE?spm_id_from=333.880.my_history.page.click
~~~

