#### php推荐标准(PSR)

&emsp;&emsp; psr(英文全称:PHP Standards Recommendation), 是一个叫[FIG](http://www.php-fig.org/)的组织指定的一套标准php编码规范,是PHP开发的建议标准。

&emsp;&emsp; psr原本有四个规范，分别是:

&emsp;&emsp;&emsp;&emsp; 1、[PSR-0](http://www.php-fig.org/psr/psr-0/) 自动加载

&emsp;&emsp;&emsp;&emsp; 2、[PSR-1](http://www.php-fig.org/psr/psr-1/) 基本代码规范

&emsp;&emsp;&emsp;&emsp; 3、[PSR-2](http://www.php-fig.org/psr/psr-2/) 代码样式

&emsp;&emsp;&emsp;&emsp; 4、[PSR-3](http://www.php-fig.org/psr/psr-3/) 日志接口

&emsp;&emsp;&emsp;&emsp; 5、[PSR-4](http://www.php-fig.org/psr/psr-4/) 自动加载增强版，PSR-4和PSR-0在功能上有所重复,最大的区别是:PSR-4类名中的下划线无任何意义,PSR-0中定义类名中的下划线会被转换成目录分割符号。

---------

#### PSR-0自动加载规范

---------

#### PSR-1基本代码规范

&emsp;&emsp; 这个section将重点讨论一下基本的代码规范的问题,依次作为将来讨论更高级别的代码分享和技术互用的基础.[RFC 2119](http://www.ietf.org/rfc/rfc2119.txt)中的必须(MUST)，不可[MUST NOT]，建议[SHOULD]，不建议[SHOULD NOT]，可能[MAY]，不可能[MAY NOT]将在这里重点讲述.

&emsp;&emsp;1、概述

&emsp;&emsp;&emsp;&emsp; (1) 源文件必须只使用<?php 和 <?= 这两种标签

&emsp;&emsp;&emsp;&emsp; (2) 源文件中的代码的编码格式必须只能使用无BOM(字节顺序标记)的UTF-8编码

&emsp;&emsp;&emsp;&emsp; (3) 一个源文件建议只使用来做申明(类(class),函数(function),常量(constant),入口文件(index.php)) 或者只用来做一些引起副作用的操作(例如：输出信息，修改.ini配置等),但不建议同时做这两件事情 

&emsp;&emsp;&emsp;&emsp; (4) 命名空间(namespace)和类(class)必须遵守PSR-0标准

&emsp;&emsp;&emsp;&emsp; (5) 类名(classname)必须使用大驼峰命名法(首字母大写)

&emsp;&emsp;&emsp;&emsp; (6) 类中的常量必须只由大写字母(A-Z)和下划线组成(_)

&emsp;&emsp;&emsp;&emsp; (7) 方法名(methodname)必须使用大驼峰命名法(首字母小写)

---------

&emsp;&emsp;2、文件

&emsp;&emsp;&emsp;&emsp; (1) PHP标签: PHP代码中必须只使用长标签<?php ?>或者短标签<?= ?>。不可以使用其它的标签

&emsp;&emsp;&emsp;&emsp; (2) PHP字符编码: php代码的编码格式必须只能使用无BOM的UTF-8

&emsp;&emsp;&emsp;&emsp; (3) 副作用: 一个源文件建议只用来做申明(类(class),函数(function),常量(constant)等)或者只用来做一些引起副作用的操作(例如:输出信息，修改.ini配置等)，但不建议同时做这两件事情。短语副作用的意思是:在包含文件时所执行的逻辑与所申明的类(class),函数(function),常量(constant)等没有直接的关系

&emsp;&emsp;&emsp;&emsp; (4)

&emsp;&emsp;&emsp;&emsp;

&emsp;&emsp;&emsp;&emsp;

&emsp;&emsp;&emsp;&emsp;


#### PSR-2代码样式

---------

#### PSR-3 日志接口

---------

#### PSR-4 自动加载增强版


