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
