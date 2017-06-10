#### php.ini（php的初始化文件）:
&emsp;&emsp;php的初始化文件(配置文件)，通常被叫做php.ini，它负责配置php行为的许多方面。对于服务器模块版本的php.ini，仅仅会在第一次启动的时候读取配置文件,cli和cgi的版本，每次调用都会读取。

&emsp;&emsp;默认的情况下，php在下面的一系列位置寻找php.ini:

&emsp;&emsp;&emsp;&emsp;1. SAPI模块指定的位置，如：

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(1)、apache的PHPIniDir指定的路径

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(2)、cgi或者cli模式的php -c 所指定的路径

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(3)、php-fpm -c 指定的路径

&emsp;&emsp;&emsp;&emsp;2. 当前的工作目录（针对cli模式）

&emsp;&emsp;&emsp;&emsp;3. web 服务器目录（对于 SAPI 模块）或 PHP 所在目录

&emsp;&emsp;&emsp;&emsp;4. --with-config-file-path

&emsp;&emsp;php常见的运行模式:

&emsp;&emsp;&emsp;&emsp;1. cgi(Common Gateway Interface)模式，如：

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;LoadModule php5_module modules/libphp5.so，Action application/x-httpd-PHP /cgi-bin/

&emsp;&emsp;&emsp;&emsp;2. FastCGI，常驻 (long-live) 型的 CGI)，如：

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(1)、nginx(php-fpm)

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(2)、lighttpd(spawn-fcgi)

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(3)、apache(mod_fastcgi)

&emsp;&emsp;&emsp;&emsp;3. apache的模块模式(mod_php5)

&emsp;&emsp;&emsp;&emsp;4. 命令行模式(cli)

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(1)、php -r 'echo "Hello World";'

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(2)、echo '<% print "Hello World";' | php

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(3)、php [-f] filename.php
