#### linux下php编译安转以及php的运行方式

#### PHP源码常见下载地址：

&emsp;&emsp; [官网下载地址](http://php.net/downloads.php) or [php-7.1.6.tar.bz2](http://jp2.php.net/distributions/php-7.1.6.tar.bz2) or [php-5.5.38.tar.bz2](http://jp2.php.net/distributions/php-5.5.38.tar.bz2) or [php-5.4.45.tar.bz2](http://jp2.php.net/distributions/php-5.4.45.tar.bz2)

#### PHP源码安装介绍:

&emsp;&emsp;1、wget http://jp2.php.net/distributions/php-7.1.6.tar.bz2

&emsp;&emsp;2、tar -jxvf php-7.1.6 && cd php-7.1.6

&emsp;&emsp;3、./configure --prefix=$prefix --with-mysqli=mysqlnd --with-pdo-mysql=mysqlnd 

&emsp;&emsp;&emsp;&emsp;--with-config-file-path=/tmp/php/etc/php.ini --with-config-file-scan-dir=/tmp/php/etc/conf.d --with-libedit --enable-fpm

#### 编译安装各种配置项以及依赖库(先升级bison、re2c)

| 配置项 |备注|
|:--------:|:-------:|
|--prefix|php的安装prefix(路径)|
|--enable-fpm|启用fast cgi的fpm支持|
|--enable-mysqlnd|php原生驱动|
|--enable-embed|启用php的嵌入式sapi库|
|--enable-maintainer-zts|激活线程安全机制|
|--enable-debug|激活调试模式|
|--enable-phpdbg|启用php的调试利器phpdbg|
|--enable-phpdbg-webhelper|启动php调试力气的web sapi|
|--enable-phpdbg-debug|在debug模式开启phpdbg|
|--enable-gcov|请用GCOV代码覆盖率（仅用于开发人员使用）|
|--enable-sigchild|用PHP自带的SIGCHLD处理器|
|--enable-libgcc|启用libgcc的精确链接|
|--enable-dmalloc|启用dmalloc（dmalloc是Linux C编程侦测记忆体溢出工具）|
|--enable-dtrace| 打开 DTrace 静态探针|
|--enable-fd-setsize|设置fd描述集的大小|
|--disable-all|禁用全部默认启用的扩展|
|--enable-bcmath|启用bcmatch|
|--enable-calendar|启用日历转换支持|
|--enable-dba=shared|捆绑模块的DBA。要建立扩展的共享模块使用--enable-dba=shared参数|
|--enable-exif|启用EXIF支持（从图片中获取元数据)|
|--enable-ftp|启用ftp支持|
|--enable-gd-native-ttf|启用TureType字符功能|
|--enable-gd-jis-conv|启用JIS-mapped日语字体支持|
|--enable-intl|一套稳定成熟、功能强大、轻便易用和跨平台支持Unicode 的开发包.ICU包|
|--enable-mbstring|启用多字节字符串的支持|
|--enable-embedded-mysqli|启用embedded支持|
|--enable-pcntl|支持php的多线程操作(仅限linux)|
|--enable-shmop|共享内存，只能按字节操作|
|--enable-soap|启用SOAP支持|
|--enable-sockets|启用sockets支持|
|--enable-sysvmsg|用sysvmsg支持|
|--enable-sysvsem|启用系统V共享内存支持|
|--enable-sysvshm|共享内存，和 shmop 的差别是提供的操作函数不同，支持 key、value操作|
|--enable-wddx|启用wddx,WDDX 是一项允许在保持数据完整性的前提下在系统格式中立的系统间交换数据和数据结构的XML技术|
|--enable-zip|包含zip读写支持|
|--disable-zend-signals|禁用zend信号量|
|--enable-shared|编译共享模块|
|--enable-static|编译静态模块|
|--disable-libtool-lock |避免死锁|
|--with-pic | 尝试生成pic代码|
|--with-xmlrpc=$dir|包含XMLRPC-EPI支持|
|--with-mysqlnd|php7中Mysql扩展被正式的移除,使用Mysqli和pdo|
|--with-mysqli=mysqlnd|安装mysqli|
|--with-pdo-mysql=mysqlnd|安装php的pdo|
|--with-config-file-path=$prefix/etc/php.ini|指定ini文件的路径|
|--with-config-file-scan-dir=$prefix/etc/conf.d|指定ini文件的其它搜寻路径|
|--with-curl=$curl_path|如果不在include目录下,需要手动指定依赖库目录|
|--with-openssl-dir=$dir|指定openssl的安装目录|
|--with-libedit=$dir|libedit readline更换|
|--with-zlib||

#### PHP的各种扩展安装依赖的库
|依赖库|配置选项|备注|
|:-------:|:-------:|:-------:|
|[pcre]|||
|[libmcrypt](ftp://mcrypt.hellug.gr/pub/crypto/mcrypt/libmcrypt/libmcrypt-2.5.7.tar.gz)|配置命令:./configure --enable-shared=no --with-pic|[网址](http://mcrypt.hellug.gr/lib/)|
|[mhash](https://jaist.dl.sourceforge.net/project/mhash/mhash/0.9.9.9/mhash-0.9.9.9.tar.bz2)|配置命令:./configure --enable-shared=no --with-pic|
|[mcrypt](http://iweb.dl.sourceforge.net/project/mcrypt/MCrypt/2.6.8/mcrypt-2.6.8.tar.gz)|配置命令:./configure --enable-shared=no --with-pic --with-libmcrypt-prefix|依赖libmcrypt和mhash,mac中#include<malloc.h>需要改为#include<sys/malloc.h>|
|[zlib](https://jaist.dl.sourceforge.net/project/libpng/zlib/1.2.11/zlib-1.2.11.tar.gz)|./configure --prefix=/root/tools/thirtypary/zlib|[官网](http://www.zlib.net/)|
|[openssl](http://www.openssl.org/source/openssl-1.0.2h.tar.gz)|配置命令:./config --prefix=$openssl/ssl zlib shared|依赖zlib|
|[libcurl](https://curl.haxx.se/download/curl-7.54.0.tar.bz2)|配置命令:./configure --enable-shared --with-pic --disable-gopher|依赖[openssl](http://www.openssl.org/source/openssl-1.0.2h.tar.gz)|
|[libxml2](http://xmlsoft.org/downloads.html)|配置命令:./configure --enable-shared --with-pic --with-python=no|[官网](ftp://xmlsoft.org/libxml2/libxml2-2.9.2.tar.gz)|
|[ncurses](ftp://ftp.gnu.org/gnu/ncurses/ncurses-5.9.tar.gz)|配置命令:/configure --without-cxx|[官网](https://www.gnu.org/software/ncurses/)|
|[readline](http://cnswww.cns.cwru.edu/php/chet/readline/rltop.html)|配置命令:./configure --enable-shared --with-pic|官网(ftp://ftp.gnu.org/gnu/readline/readline-6.2.tar.gz)|依赖ncurses|
|[jpeg](http://www.ijg.org/files/jpegsrc.v9a.tar.gz)|配置命令:./configure --prefix=/root/tools/thirtypary/jpeg||
|[png](https://jaist.dl.sourceforge.net/project/libpng/libpng16/1.6.29/libpng-1.6.29.tar.gz)|配置命令:./configure --enable-shared --with-pic --with-zlib-prefix|依赖zlib|
|[freetype](http://ftp.twaren.net/Unix/NonGNU/freetype/freetype-2.8.tar.bz2)|配置命令:./configure --prefix=/root/tools/thirtypary/freetype --without-harfbuzz|依赖:zlib, bzip2, libpng, harfbuzz|[官网](http://ftp.twaren.net/Unix/NonGNU/freetype/)|
|[webp](http://downloads.webmproject.org/releases/webp/libwebp-0.6.0.tar.gz)|配置命令:./configure --enable-shared --with-pic|[官网](http://www.linuxfromscratch.org/blfs/view/svn/general/libwebp.html)|
|[gd](https://github.com/libgd/libgd/releases/download/gd-2.1.1/libgd-2.1.1.tar.bz2)|配置命令:./configure --enable-shared --with-freetype --with-jpeg --with-png --with-zlib--with-jpeg --with-pic|依赖:freetype,jpeg,libpng|
|[redis](http://download.redis.io/releases/redis-3.2.5.tar.gz)|配置命令:cd src,修改:Makefile make PREFIX=/usr/local/redis install|[官网](https://redis.io)|
|[yaml](http://pyyaml.org/download/libyaml/yaml-0.1.4.tar.gz)|配置命令:./configure --prefix=/root/tools/thirtypary/yaml --enable-shared --pic||
|[zookeeper](http://mirror.bit.edu.cn/apache//zookeeper/zookeeper-3.4.9/zookeeper-3.4.9.tar.gz)|./configure –prefix=/root/tools/thirtypary/zookeeper||
|[bzip2](http://www.bzip.org/1.0.6/bzip2-1.0.6.tar.gz)|修改Makefile PREFIX=/root/tools/thirtypary/bzip2, make -f Makefile-libbz2_so|[官网](http://www.bzip.org/downloads.html)|
|[libevent2](http://cloud.github.com/downloads/libevent/libevent/libevent-2.0.20-stable.tar.gz)|配置命令:./configure --prefix=/root/tools/thirtypary/libevent2|[官网](http://libevent.org/)|
|[imagick]|||
|[protobuf]|||
|[zeromq]|||
|[mongodb]|||

先升级[bison, re2c] (http://www.hdj.me/php7-install-note), libXpm 

#### 注意:
&emsp;&emsp;1、库文件安装完成后,最好配置:PATH,LD_LIBRARY_PATH,CFLAGS,LDFLAGS,C_INCLUDE_PATH,LIBRARY_PATH

&emsp;&emsp;2、mcrypt扩展安装需要LDFLAGS中有CFLAGS的一些标志.

#### 独立于库文件PHP的扩展
|扩展|下载路径|备注|
|:-------:|:-------:|:-------:|
|redis|https://github.com/nicolasff/phpredis/archive/master.zip|./configure --with-php-config|
|memcache|https://github.com/websupport-sk/pecl-memcache/archive/php7.zip|./configure --with-php-config|
|[zookeeper](http://blog.csdn.net/likunlun1234/article/details/46637919)|wget http://pecl.php.net/get/zookeeper-0.4.0.tgz|./configure --with-libzookeeper-dir|
|yaml|http://pecl.php.net/get/yaml-2.0.0RC1.tgz|./configure --with-php-config|
|event|http://pecl.php.net/get/event-2.3.0.tgz|./configure --with-php-config --with-libevent|
|swoole|https://github.com/swoole/swoole-src/archive/swoole-1.7.21-stable.tar.gz|./configure --with-php-config|
|yaconf|https://github.com/laruence/yaconf.git|./configure --with-php-config|
|yac|https://github.com/laruence/yac.git|./configure --with-php-config|
|yaf|https://github.com/laruence/yaf.git|./configure --with-php-config|
|yar|https://github.com/laruence/yar.git|./configure --with-php-config|
|apc||不支持|
|mysqlnd_ms||不支持|

#### kalfa-php扩展的实现

#### 安装详细命令:(前提:yum install libxpm-devel, bison, re2c)
> ./configure --prefix=/root/tools/thirtypary/php7 --with-mysqli=mysqlnd --with-pdo-mysql=mysqlnd  -with-config-file-path=/root/tools/thirtypary/php7/etc  --enable-fpm --with-libxml-dir=/root/tools/thirtypary/libxml2 --with-openssl-dir=/root/tools/thirtypary/openssl/  --with-mcrypt=/root/tools/thirtypary/libmcrypt/ --with-curl=/root/tools/thirtypary/libcurl/ --enable-sockets --enable-soap --enable-bcmath --enable-shmop --enable-calendar --with-zlib-dir=/root/tools/thirtypary/zlib --enable-pcntl --enable-ftp --with-xmlrpc --enable-mbstring --enable-zip -enable-sysvsem --enable-sysvshm --enable-sysvmsg  --enable-zip --with-bz2=/root/tools/thirtypary/bzip2 --with-gettext --with-mhash   --with-kerberos  --with-readline=/root/tools/thirtypary/readline/ --without-cxx --with-gd=/root/tools/thirtypary/libgd --with-freetype-dir=/root/tools/thirtypary/freetype/ --with-png-dir=/root/tools/thirtypary/libpng/ --with-jpeg-dir=/root/tools/thirtypary/jpeg --with-xpm-dir=/usr/lib64 --with-openssl=/root/tools/thirtypary/openssl/

&emsp;&emsp; 1、后面安装的时候注意,第三方库都安装到一个文件夹中.

&emsp;&emsp; 2、对于这些依赖环境需要有个项目专门处理安装软件.
