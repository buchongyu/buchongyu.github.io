

https://github.com/tinyproxy/tinyproxy/archive/1.8.3.tar.gz
https://github.com/tinyproxy/tinyproxy/

依赖包:

如果没有安装asciidoc会提示
   checking for a2x... no
   configure: error: Test for asciidoc failed. See the file 'INSTALL' for help.

1. 方法一
https://sourceforge.net/directory/os:mac/?q=asciidoc
wget https://jaist.dl.sourceforge.net/project/asciidoc/asciidoc/8.6.9/asciidoc-8.6.9.tar.gz --no-check-certificate

./configure --prefix=$HOME/tinyproxy/asciidoc
make -j8 && make install

2. 方法二
wget https://jaist.dl.sourceforge.net/project/asciidoc/asciidoc/8.2.2/asciidoc-8.2.2.tar.gz --no-check-certificate

修改install.sh 然后执行: bash -x install.sh 即可


接下来:
修改后配置环境变量:
AC_PATH_PROG 检查通用的程序和文件，参考:
https://www.gnu.org/software/autoconf/manual/autoconf-2.68/html_node/Generic-Programs.html

最后安装tinyproxy:

./configure --prefix=$HOME/tinyproxy/tinyproxy  --enable-reverse --enable-transparent
a2x: failed: file not found: /home/users/buchongyu/tinyproxy/asciidoc/bin/docbook-xsl/manpage.xsl

创建文件夹:
/home/users/buchongyu/tinyproxy/tinyproxy/var/run/tinyproxy

启动: ./tinyproxy -c ../etc/tinyproxy.conf
