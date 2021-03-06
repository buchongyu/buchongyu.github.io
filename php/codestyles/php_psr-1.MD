#### PSR-1基本代码规范

&emsp;&emsp; 这个section将重点讨论一下基本的代码规范的问题,依次作为将来讨论更高级别的代码分享和技术互用的基础.[RFC 2119](http://www.ietf.org/rfc/rfc2119.txt)中的必须(MUST)，不可[MUST NOT]，建议[SHOULD]，不建议[SHOULD NOT]，可能[MAY]，不可能[MAY NOT]将在这里重点讲述.

-------

#### 1、概述

(1) 源文件必须只使用<?php 和 <?= 这两种标签

(2) 源文件中的代码的编码格式必须只能使用无BOM(字节顺序标记)的UTF-8编码

(3) 一个源文件建议只使用来做申明(类(class),函数(function),常量(constant),入口文件(index.php)) 或者只用来做一些引起副作用的操作(例如：输出信息，修改.ini配置等),但不建议同时做这两件事情 

(4) 命名空间(namespace)和类(class)必须遵守PSR-0标准

(5) 类名(classname)必须使用大驼峰命名法(首字母大写)

(6) 类中的常量必须只由大写字母(A-Z)和下划线组成(_)

(7) 方法名(methodname)必须使用大驼峰命名法(首字母小写)

-------

#### 2、文件

(1) PHP标签: PHP代码中必须只使用长标签<?php ?>或者短标签<?= ?>。不可以使用其它的标签

(2) PHP字符编码: php代码的编码格式必须只能使用无BOM的UTF-8

(3) 副作用: 一个源文件建议只用来做申明(类(class),函数(function),常量(constant)等)或者只用来做一些引起副作用的操作(例如:输出信息，修改.ini配置等)，但不建议同时做这两件事情。短语副作用的意思是:在包含文件时所执行的逻辑与所申明的类(class),函数(function),常量(constant)等没有直接的关系.

&emsp;副作用包含但是不局限于:产生输出，显示地require和include,链接外部服务,修改ini配置,触发错误或者异常，修改全局或者静态变量，读取或者修改文件等等.

避免使用的例子:
```php
<?php

// 副作用:修改了ini配置
ini_se('error_reporting', E_ALL);

// 副作用:载入了文件
include 'file.php';

// 副作用:产生了输出
echo "<html>"

// 申明
function foo()
{
    // 申明函数体
}
```


应该使用的例子:

```php
<?php

// 申明
function foo()
{
    // 函数体
}

// 条件式申明不算副作用
if (!function_exists('bar')) {
    function bar()
    {
        // 函数体
    }
}
```

-------

#### 3、命名空间(namespace)和类名(classname)

(1) 命名空间(namespace)和类(class)必须遵守PSR-0.

(2) 一个源文件中只能有一个类(class),并且每个类(class)至少有一级空间名(namespace),即一个顶级的组织名(vendor name)

(3) 类名(classname)必须使用大驼峰命名法

(4) PHP5.3之后的代码必须使用正式的命名空间(namespace),PHP5.2之前的代码建议使用伪命名空间 Vendor_作为类名的前缀(classname)

PHP5.3之后的使用命名空间的例子:

```
<?php
// PHP 5.3之后
namespace Vendor\Model;

class Foo
{
    // class body
}

```

PHP5.2之前的代码建议使用伪命名空间Vendor_作为类名(class name)的前缀

```
<?php
// PHP 5.2.x之前
class Vendor_Model_Foo
{
    // class body
}
```

-------

#### 4、类的常量、属性和方法

术语类(class)指所有的类(class),接口(interface)和特型(trait)

(1)、常量:类常量必须只由大写字母和下划线(_)组成。

(2)、属性:一般使用小驼峰命名法

(3)、方法:方法名必须使用小驼峰命名法来申明.

简单的类的示例:

```
<?php

namespace Vendor\Model;

class Foo
{
    const VERSION = '1.0';
    const DATE_APPROVED = '2012-06-01';

    public $foo;

    public function fooDisplay()
    {

    }
}
```
