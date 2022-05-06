CentOs配置Nginx图片服务器

使用yum安装nginx

~~~java
yum install -y nginx
~~~

运行nginx

~~~java
systemctl status nginx
~~~

在conf.d文件夹下 创建cxl.config

~~~java
server {
    listen       8081;#访问端口
    server_name  localhost;

    #access_log  /var/log/nginx/cxl.access.log  main;

    location / {
        root   /home/image;#图片访问路径
    }

    #error_page  404              /404.html;

    # redirect server error pages to the static page /50x.html
    #
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }

    # proxy the PHP scripts to Apache listening on 127.0.0.1:80
    #
    #location ~ \.php$ {
    #    proxy_pass   http://127.0.0.1;
    #}

    # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    #
    #location ~ \.php$ {
    #    root           html;
    #    fastcgi_pass   127.0.0.1:9000;
    #    fastcgi_index  index.php;
    #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
    #    include        fastcgi_params;
    #}

    # deny access to .htaccess files, if Apache's document root
    # concurs with nginx's one
    #
    #location ~ /\.ht {
    #    deny  all;
    #}
}


~~~

重启服务

~~~java
systemctl status nginx
~~~

