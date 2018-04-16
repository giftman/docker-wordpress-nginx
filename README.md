# docker-wordpress-nginx

A Dockerfile that installs the latest wordpress, nginx, php-apc and php-fpm.

NB: A big thanks to [jbfink](https://github.com/jbfink/docker-wordpress) who did most of the hard work on the wordpress parts!

You can check out his [Apache version here](https://github.com/jbfink/docker-wordpress).

thanks eugeneware~

This version add https support.

## Installation

If you'd like to build the image yourself then:

```bash
$ git clone https://github.com/giftman/docker-wordpress-nginx.git
$ cd docker-wordpress-nginx

//这里把证书复制到要目录下  更改网站域名和对应的证书名

//nginx-site.conf
//server_name www.babytoygarden.com;
//ssl_certificate 1_babytoygarden.com_bundle.crt;
//ssl_certificate_key 2_babytoygarden.com.key;

//Dockerfile
//ADD ./1_babytoygarden.com_bundle.crt /etc/nginx/1_babytoygarden.com_bundle.crt
//ADD ./2_babytoygarden.com.key /etc/nginx/2_babytoygarden.com.key

$ sudo docker build -t="giftman/wordpress" .
```

## Usage

To spawn a new instance of wordpress on port 80.  The -p 80:80 maps the internal docker port 80 to the outside port 80 of the host machine.

```bash
$ sudo docker run -p 80:80 -p 443:443 --name docker-wordpress-nginx -d giftman/wordpress
```

See If any error:

```
$ sudo docker logs docker-wordpress-nginx
```

Start your newly created docker.

```
$ sudo docker start docker-wordpress-nginx
```

After starting the docker-wordpress-nginx check to see if it started and the port mapping is correct.  This will also report the port mapping between the docker container and the host machine.

```
$ sudo docker ps

0.0.0.0:80 -> 80/tcp docker-wordpress-nginx
```

You can the visit the following URL in a browser on your host machine to get started:

```
http://127.0.0.1:80

sudo docker ps 
sudo docker exec -it contain_name /bin/sh

service mysql restart

mysql -uroot -pXXX

删除端口映射规则

a. 获取规则编号  
    iptables -t nat -nL --line-number
b. 根据编号删除规则  
    iptables -t nat -D DOCKER $num
```
