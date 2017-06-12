#### linux下php编译安转以及php的运行方式

#### PHP源码常见下载地址：

&emsp;&emsp; [官网下载地址](http://php.net/downloads.php) or [php-7.1.6.tar.bz2](http://jp2.php.net/distributions/php-7.1.6.tar.bz2) or [php-5.5.38.tar.bz2](http://jp2.php.net/distributions/php-5.5.38.tar.bz2) or [php-5.4.45.tar.bz2](http://jp2.php.net/distributions/php-5.4.45.tar.bz2)

#### PHP源码安装介绍:

&emsp;&emsp;1、wget http://jp2.php.net/distributions/php-7.1.6.tar.bz2

&emsp;&emsp;2、tar -jxvf php-7.1.6 && cd php-7.1.6

&emsp;&emsp;3、./configure --prefix=$prefix --with-mysqli=mysqlnd --with-pdo-mysql=mysqlnd 

&emsp;&emsp;&emsp;&emsp;--with-config-file-path=/tmp/php/etc/php.ini --with-config-file-scan-dir=/tmp/php/etc/conf.d --with-libedit --enable-fpm

&emsp;&emsp;&emsp;&emsp;http://blog.csdn.net/juan083/article/details/51155880


#### 编译安装各种配置项以及依赖库

| 配置项 |备注|
|:--------:|:-------:|
|--prefix|php的安装prefix(路径)|
|--enable-fpm|启用fast cgi的fpm支持|
|--with-mysql|php7中Mysql扩展被正式的移除,使用Mysqli和pdo|
|--enable-mysqlnd|php原生驱动|
|--with-mysqli=mysqlnd|安装mysqli|
|--with-pdo-mysql=mysqlnd|安装php的pdo|
|--with-config-file-path=$prefix/etc/php.ini|指定ini文件的路径|
|--with-config-file-scan-dir=$prefix/etc/conf.d|指定ini文件的其它搜寻路径|
|--with-curl=$curl_path|如果不在include目录下,需要手动指定依赖库目录|

#### PHP的各种扩展安装依赖的库
|依赖库|配置选项|备注|
|:-------:|:-------:|:-------:|
|[libcurl](https://curl.haxx.se/download/curl-7.54.0.tar.bz2)| --with-curl=libcurl安装目录|需要先安装[libcurl](https://curl.haxx.se/download/curl-7.54.0.tar.bz2),配置命令:./configure --enable-shared --with-pic ---disable-gopher|
