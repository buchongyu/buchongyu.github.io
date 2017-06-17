#### linux(centos)下nginx编译安装

#### nginx源码安装依赖软件包:pcre、zlib、openssl，在安装nginx之前，需要先下载并解压软件包到指定目录。()

&emsp;&emsp;1、[pcre-8.40.tar.gz](https://ftp.pcre.org/pub/pcre/pcre-8.40.tar.gz),[pcre官网](http://www.pcre.org/)

&emsp;&emsp;2、[openssl-1.0.2h](https://www.openssl.org/),[openssl官网](http://www.openssl.org/source/openssl-1.0.2h.tar.gz)

&emsp;&emsp;3、[zlib-1.2.11](http://www.zlib.net/),[zlib官网](https://jaist.dl.sourceforge.net/project/libpng/zlib/1.2.11/zlib-1.2.11.tar.gz)

&emsp;&emsp;4、[nginx-1.12.1.tar.gz](http://nginx.org/download/nginx-1.13.1.tar.gz),[nginx官网](http://nginx.org/)


#### 安装过程:

&emsp;&emsp;1、解压pcre,openssl,zlib,nginx源码包到指定的目录

&emsp;&emsp;2、/configure --prefix=/root/tools/thirtypary/nginx

&emsp;&emsp;&emsp;&emsp;--with-http_ssl_module 

&emsp;&emsp;&emsp;&emsp;--with-threads 

&emsp;&emsp;&emsp;&emsp;--with-http_stub_status_module

&emsp;&emsp;&emsp;&emsp;--with-openssl=/root/tools/sources/openssl-1.0.2h/

&emsp;&emsp;&emsp;&emsp;--with-zlib=/root/tools/sources/zlib-1.2.11/

&emsp;&emsp;&emsp;&emsp;--with-pcre=/root/tools/sources/pcre-8.40/

&emsp;&emsp;3、注意: --with-openssl、--with-zlib和--with-pcre指定的是依赖包的源码路径，不是安装后的路径.
