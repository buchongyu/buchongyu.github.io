#### autoconf 和 automake

configure.ac文件格式

AC_PREREQ                               文件要求的autoconf版本

AC_INIT([xxx], [yyy], [zzz], [aaa])     四个参数，前三个必须。第一个是软件包的名字，一个字符串(可以用空格，不需要引号)，第二个是版本号，第三个是报告bug的email，第四个是make dist时候创建的名字。
                                        如果这个域不填写的话默认为xxx，(但是会有变化，比如:xxx为My hello则创建my-hello.tar.gz)

AM_MAINTAINER_MODE                      关闭缺省时仅供程序维护者使用的makefile目标，并修改以使configure能理解 --enable-maintainer-mode选项。--enable-maintainer-mode将maintaineronly目标重新打开。
                                        仅供维护者使用的makefile目标允许最终用户清除自动生成的文件，比如configure，这意味着要修复编译故障，必须安装有autoconf和automake软件。注意，
                                        因为autogen.sh脚本主要是给开发人员用的，autogen.sh会自动传递一个--enable-maintainer-mode选项给configure。

AC_CONFIG_SRCDIR                        检查源文件是否存在,来确定源码目录的有效性。
AC_CONFIG_HEADERS                       用来生成config.h文件,以便autoheader命令使用。
AC_CONFIG_MACRO_DIR                     指定使用m4目录存放第三方宏;然后在最外层的Makefile.am中加入ACLOCAL_AMFLAGS = -I m4

AC_ARG_VAR(var-name, help-string)       申明变量和帮助字符串,需要使用AC_SUBST来生效到Makefile中。https://autotools.io/autoconf/arguments.html
                                        https://autotools.io/autoconf/arguments.html

case

esac

AC_SUBST                                输出一个变量到由configure生成的文件中(一般是Makefile和Makefile.in),执行AC_OUTPUT宏时，configure脚本处理包含有两个@符号标志的变量(例如@PACKAGE@)的文件。
                                        只有用AC_SUBST输出了变量，它才能识别这些变量(许多在上面讨论过的预先写好的宏都用AC_SUBST定义变量)。    
AS_IF                                   

AC_CANONICAL_TARGET
AM_INIT_AUTOMAKE
AC_ARG_WITH

AC_PROG_CC
AC_PROG_CXX
AC_PROG_CXX_FOR_BUILD
AC_LANG([C++])
ACX_USE_SYSTEM_EXTENSIONS

m4_ifdef([AM_PROG_AR], [AM_PROG_AR])
AM_CONDITIONAL(GCC, test "$GCC" = yes)
AC_PROG_OBJC
AC_PROG_LIBTOOL

AC_MSG_CHECKING
CXXFLAGS


AC_HEADER_STDC
AC_FUNC_MEMCMP
AC_FUNC_STRTOD
AC_CHECK_HEADERS
AC_CHECK_LIB
AC_CHECK_FUNCS
ACX_CHECK_SUNCC

AC_COMPILE_IFELSE
AC_LANG_PROGRAM

AC_MSG_FAILURE
ACX_PTHREAD

AC_CXX_STL_HASH
AC_SEARCH_LIBS

OBJC_CONFORMANCE_TEST
AX_CXX_COMPILE_STDCXX

export CFLAGS
export CXXFLAGS

AC_CONFIG_SUBDIRS
AC_CONFIG_FILES         生成相应的Makefile文件
AC_OUTPUT               用来指定生成的Makefile,AC_OUTPUT列出由configure脚本创建的文件。这些文件都是由带.in后缀的同名文件生成的。例如，src/Makefile是由src/Makefile.in生成的，config.h是由config.h.in生成的。
                        在执行AC_OUTPUT宏时，configure脚本处理包含有两个@符号标志的变量(例如@PACKAGE@)的文件。只有用AC_SUBST输出了变量，它才能识别这些变量

AC_DISABLE_OPTION_CHECKING
m4_include

ACX_NONCANONICAL_BUILD
ACX_NONCANONICAL_HOST
ACX_NONCANONICAL_TARGET

AC_PROG_INSTALL
ACX_PROG_LN
AC_PROG_LN_S
AC_PROG_SED
AC_PROG_AWK

AC_ARG_ENABLE
