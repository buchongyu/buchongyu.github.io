#### PHP.INI（php的初始化文件）:
&emsp;&emsp;php的初始化文件(配置文件)，通常被叫做php.ini，它负责配置php行为的许多方面。对于服务器模块版本的php.ini，仅仅会在第一次启动的时候读取配置文件,cli和cgi的版本，每次调用都会读取，如果配置文件中指令未设置（或者删除），php将会用默认值来填充，大部分指令可以在运行时动态设置(ini_set)，少部分的不可以。php提供两形式的ini文件，一种用于开发环境，一种用生产环境。

&emsp;&emsp;配置的指令比较简单，都是key=value的类型，大小写敏感，value可以是字符串，数字、常量(On, Off, True, False, Yes, No and None)、表达式(E_ALL & ~E_NOTICE)、引号字符串（"foo"）、先前设置的变量${foo}。

&emsp;&emsp;英文分号表示注释，会被忽略掉，section[]也会被忽略掉(除了[PATH=]和[HOST=]外)，空白和换行也会被忽略掉。

&emsp;&emsp;php.ini的表达式操作符只能有：位操作符和圆括号。位操作符如下：
  
&emsp;&emsp;&emsp;&emsp; |  bitwise OR

&emsp;&emsp;&emsp;&emsp; ^  bitwise XOR

&emsp;&emsp;&emsp;&emsp; &  bitwise AND

&emsp;&emsp;&emsp;&emsp; ~  bitwise NOT

&emsp;&emsp;&emsp;&emsp; !  boolean NOT

&emsp;&emsp;boolean值，On,True,Yes，1 表示真值；Off,False,No,0 表示假值

&emsp;&emsp;字符串值，None和空白表示空字符串，如果是字符串None，需要加上"None"

&emsp;&emsp;[PATH=/site]只会影响/site目录下的文件,[HOST=dev.domain]只会影响dev.domain下的文件

-------
#### 默认的情况下，php在下面的一系列位置寻找php.ini:

&emsp;&emsp;1. SAPI模块指定的位置，如：

&emsp;&emsp;&emsp;&emsp;(1)、apache的PHPIniDir指定的路径

&emsp;&emsp;&emsp;&emsp;(2)、cgi或者cli模式的php -c 所指定的路径

&emsp;&emsp;&emsp;&emsp;(3)、php-fpm -c 指定的路径

&emsp;&emsp;2. 当前的工作目录（针对cli模式）

&emsp;&emsp;3. web 服务器目录（对于 SAPI 模块）或 PHP 所在目录

&emsp;&emsp;4. --with-config-file-path

#### 查看配置文件位置的办法:

&emsp;&emsp;1. php --ini

&emsp;&emsp;2. php -r 'phpinfo();'

-------

#### php常见的运行模式:

&emsp;&emsp;1. cgi(Common Gateway Interface)模式，如：

&emsp;&emsp;&emsp;&emsp;LoadModule php5_module modules/libphp5.so，Action application/x-httpd-PHP /cgi-bin/

&emsp;&emsp;2. FastCGI，常驻 (long-live) 型的 CGI)，如：

&emsp;&emsp;&emsp;&emsp;(1)、nginx(php-fpm)

&emsp;&emsp;&emsp;&emsp;(2)、lighttpd(spawn-fcgi)

&emsp;&emsp;&emsp;&emsp;(3)、apache(mod_fastcgi)

&emsp;&emsp;3. apache的模块模式(mod_php5)

&emsp;&emsp;4. 命令行模式(cli)

&emsp;&emsp;&emsp;&emsp;(1)、php -r 'echo "Hello World";'

&emsp;&emsp;&emsp;&emsp;(2)、echo '<% print "Hello World";' | php

&emsp;&emsp;&emsp;&emsp;(3)、php [-f] filename.php

&emsp;&emsp;5、ISAPI模式(windows下)

-----

#### php.ini文件的详细介绍

