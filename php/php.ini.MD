#### PHP.INI（php的初始化文件）:
&emsp;&emsp;php的初始化文件(配置文件)，通常被叫做php.ini，它负责配置php行为的许多方面。对于服务器模块版本的php.ini，仅仅会在第一次启动的时候读取配置文件,cli和cgi的版本，每次调用都会读取。

&emsp;&emsp;如果配置文件中指令未设置（或者删除），php将会用默认值来填充，大部分指令可以在运行时动态设置(ini_set)，少部分的不可以。php提供两形式的ini文件，一种用于开发环境，一种用生产环境。

&emsp;&emsp;配置的指令比较简单，都是key=value的类型，大小写敏感，value可以是字符串，数字、常量(On, Off, True, False, Yes, No and None)、表达式(E_ALL & ~E_NOTICE)、引号字符串（"foo"）、先前设置的变量${foo}。

&emsp;&emsp;英文分号表示注释，会被忽略掉，section[]也会被忽略掉(除了[PATH=]和[HOST=]外)，空白和换行也会被忽略掉。

&emsp;&emsp;php.ini的表达式操作符只能有：位操作符和圆括号。位操作符如下：

&emsp;&emsp;&emsp;&emsp; |  bitwise OR

&emsp;&emsp;&emsp;&emsp; ^  bitwise XOR

&emsp;&emsp;&emsp;&emsp; &  bitwise AND

&emsp;&emsp;&emsp;&emsp; ~  bitwise NOT

&emsp;&emsp;&emsp;&emsp; !  boolean NOT

&emsp;&emsp;boolean值，On,True,Yes，1 表示真值；Off,False,No,0 表示假值

&emsp;&emsp;字值，None和空白表示空字符串，如果是字符串None，需要加上"None"

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

#### php.ini指令的详细介绍

| 指令名称  | 默认值| 默认值解释|备注|
|:--------|---------:|:-------:|:-------:|
| user_ini.filename| .user.ini | 默认搜索路径 |PHP 会在每个目录下搜寻的文件名；如果设定为空字符串则 PHP 不会搜寻.从被执行的 PHP 文件所在目录开始一直上升到 web 根目录（DOCUMENT_ROOT 所指定的）。如果被执行的 PHP 文件在 web 根目录之外，则只扫描该目录,只有具有 PHP_INI_PERDIR 和 PHP_INI_USER 模式的 INI 设置可被.user.ini识别|
| user_ini.cache_ttl| 300| 单位（秒），也就是5分钟|重新读取用户 INI 文件的间隔时间|
| engine| On| 开启php文件的解析|只在apache下开启下生效，On表示开启解析，Off表示关闭解析|
| short_open_tag| On| 开启php的短标记|因为xml和其它语言使用了这种标记，服务器很容易解析错误,我们不推荐使用.考虑到历史包袱的问题,该标记现在还是支持的.<? ?> 或者 <?="Hello World" ?>|
|precision|14|浮点数有效数字的位数||
|output_buffering|Off|单位字节，也就是4kb| 控制输出,cli模式下是关闭的.使用var_dump,print,echo 等输出数据的时候,数据默认被写入到output_buffering中,直到写满,才会将这些数据通过tcp传递给前端.也可以是用ob_start()和ob_end_flush()函数.ob_start()开启php的缓存,ob_start会把缓存设置的足够大,即使数据超过了output_buffering,也不会发给浏览器,直到脚本运行结束或者使用了ob_end_flush才会把数据发给浏览器.|
|output_handler|空值|将脚本的所有输出,重定向到一个函数来处理.如mb_output_handler,字符的编码将被修改为指定的编码.|不能同时使用 mb_output_handler() 和 ob_iconv_handler()，也不能同时使用 ob_gzhandler() 和 zlib.output_compression|
|zlib.output_compression|Off|输出使用zlib压缩|取值可以是On,Off,buffer size|
|zlib.output_compression_level|-1|压缩值|1-5，6实际压缩效果不好,cpu很高.|
|zlib.output_handler|空值||zlib.outour_compression如果被激活,不能使用zlib.output_handler.二者相互冲突. 这个设置和output_handler一样但是顺序不同.|
|implicit_flush|Off|如果设置为On,每次调用完echo,print等后,自动调用flush(),立即输出|cli模式下，改选项默认设置为On|
|unserialize_callback_func|空值|反序列化回调函数| 反序列化,如果类没有定义,则使用unserialize_callback_func定义的函数来处理.|
|serialize_precision|17|默认值能保证浮点型数据被解序列化程序解码时不会丢失数据|将浮点型和双精度型数据序列化存储时的精度(有效位数)。(注意：有效位数不会超过precision设置的值)|
