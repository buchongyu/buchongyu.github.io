#### php.ini（php的初始化文件）:
&emsp;&emsp;php的初始化文件(配置文件)，通常被叫做php.ini，它负责配置php行为的许多方面。对于服务器模块版本的php.ini，仅仅会在第一次启动的时候读取配置文件,cli和cgi的版本，每次调用都会读取。

&emsp;&emsp;默认的情况下，php在下面的一系列位置寻找php.ini:

&emsp;&emsp;&emsp;&emsp;1. SAPI模块指定的位置，(apache的PHPIniDir指定的路径，cgi和cli模式的php -c 所指定的路径)

&emsp;&emsp;&emsp;&emsp;2. 当前的工作目录（针对cli模式）

&emsp;&emsp;&emsp;&emsp;3. web 服务器目录（对于 SAPI 模块）或 PHP 所在目录

&emsp;&emsp;&emsp;&emsp;4. --with-config-file-path
