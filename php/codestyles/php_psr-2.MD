#### PSR-2代码样式
    
&emsp;&emsp;这个section是基础代码规范(PSR-1)的继承和扩展.

&emsp;&emsp;为了尽可能的提升阅读别人代码的效率，下面列举了一系列的通用规则，特别是关于PHP代码风格的。当开发者们在多个项目中合作时，本指南将会成日所有这些项目中共同的一组代码规范.

#### 1.概述

* 代码`必须`遵守PSR-1

* 代码`必须`使用四个空格来进行缩进，而不是制表符

* 一行代码的长度`不建议`有硬限制，软限制`必须`为120个字符，`建议`每行代码80个字符或者更少

* 在命名空间的申明下面`必须`有一个空行，而且在use的申明下面也必须有一个空行

* 类的左花括号`必须`放在其申明下面自称一行，右花括号则必须放在类主体的下面自成一行

* 方法(method)的左花括号`必须`放在其申明下面自成一行，右花括号则`必须`放在方法主体的下一行

* 所有的属性属性(property)和方法(method)`必须`有可访问的申明,抽象(abstract)和终结(final)申明必须在可访问的申明之前，而金泰申明必须在可访问申明之后

* 在控制结构的关键字后面`必须`有一个空格；而方法(method)和函数(function)的关键字后面`不能`有空格

* 控制结果的做花括号`必须`和其放在同一行，右花括号`必须`放在该控制结构代码主题的下一行

* 控制结果的左括号之后不可有空格,右花括号之前也不可以有空格

#### 1.1示例

这个示例展示了上下文提到的一些规则:

```
<?php
namespace Vendor\Package;

use BarCLass as Bar;
use FooInterface;

class Foo extends Bar implements FooInterface
{
    public function sample sampleFunction($a, $b = null)
    {
        if ($a === $b) {
            bar();
        } elseif {
            $foo->var($arg1);
        } else {
            Bar::bar($arg1);
        }
    }

    final public static function bar()
    {
        // 方法主体
    }
}
```

#### 2.通则

#### 2.1 基础代码规范

代码必须遵守PSR-1中的所有规则

#### 2.2 源文件

* 所有的PHP源文件`必须`使用unix换行作为行结束符

* 所有的源文件必须以一个空行结束

* 纯PHP代码源文件的关闭标签?>必须省略

#### 2.3 行

* 行的长度`不可`有硬限制 

* 行长度的软限制`必须`是120个字符;对于软限制，代码分格检查器`必须`警告但不可报错

* 一行代码的长度`不建议`超过80个字符；较长的行`建议`拆分成多个不超过80个字符的子行

* 在非空行后面`不可以`有空格 

* 空行`可以`用来增强可读性和区分相关代码快 

* 一行`不可以`多于一个语句

#### 2.4 缩进

* 代码必须使用4个空格，且`不可`使用制表符来缩进

* 注意:代码中只使用空格，且不和制表符混合使用，将会对避免代码差异，不定、历史和注解中的一些问题有帮助.空格的使用还可以使通过调整细微的缩进来改进行间对齐变的更加简单。

#### 2.5 关键字和True/False/Null

* PHP的关键字(keyword)`必须`使用小写字母

* PHP的常量true，false和null`必须`使用小写字母

#### 3. 命名空间(namespace)和导入(use)申明

* 命名空间(namespac)的申明后面`必须`有一行空行

* 所有的导入(use)申明`必须`放在命名空间(namespace)申明的下面

* 一句申明中，`必须`只有一个导入(use)关键字

* 在导入(use)申明代码块后面`必须`有一会空行

示例:

```
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

// .... 其它的PHP代码...

```

#### 4. 类(class)，属性(property)和方法(method)

&emsp;&emsp;术语`类`指的是所有的类(class),接口(interface)和特型(trait)

#### 4.1 扩展(extends)和实现(implement)

1. 一个类的扩展(extends)和实现(implement)关键词必须和类名(classname)在同一行

2. 类(class)的左花括号`必须`放在下面自成一行;右花括号必须放在类(class)主体后面自成一行

```
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements \ArrayAccess,\Countable
{
    //常量、属性、方法
}
```

3. 实现(implement)列表`可以`被拆分为多个缩进了一次的子行。如果要拆成多个子行,列表的第一项`必须`要放在下一行,并且每行必须只有一个接口(interface)

```
<?php 

namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    //常量、属性、方法
}
```

#### 4.2 属性(property)

- 所有的属性(property)都必须申明其可见性

- 变量(var)关键字`不可`用来申明一个属性(property)

- 一条语句`不可`申明多个属性(property)

- 属性明(property name) `不推荐`用耽搁下划线作为前缀来申明其保护(protected)或者私有(private)的可见性

- 一个属性(property)申明看起来应该像下面一样:

```
<?php 
namespace Vendor\Package;

class ClassName
{
    public $foo = null;
}
```

#### 4.3 方法(method)

- 所有的方法(method)都`必须`申明其可见性

- 方法名(method name)不推荐用单个下换下作为前缀来表明其保护(protected)或者私有的可见性

- 方法名(method name)在其申明后面不可有空格跟随，其左花括号必须放在下面自称一行，且右花括号必须放在方法主体的下面自称一行。左括号后面不可以有空格，且右花括号前面也不可以有空格

- 一个方法(method)申明看起来应该像下面一样，注意括号，逗号，空格和花括号的位置:

```
<?php
namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, $arg2, $args3 = [])
    {
        // 方法主题部分
    }
}
```

#### 4.4 方法(method)的参数

- 在参数的列表中，逗号之前不可以有空格，而逗号之后则必须要一个空格

- 方法(method)中有默认值的参数必须放在参数列表的最后面

```
<?php
namespace Vendor\Package;

class ClassName
{
    public function foo($arg1, $arg2, $arg3 = [])
    {
        // 方法主题部分
    }
}
```

- 参数列表可以被拆分为多个缩进了一次的子行。如果要拆分成多个子行，参数列表的第一项必须放在下一行，并且每行必须只有一个参数.当参数列表被拆分成多个子行，右括号和花括号之间必须有一个空格并且自成一行。

```
<?php
namespace Vendor/Package;

class ClassName
{
    public function foo(
        $arg1,
        $arg2,
        array $arg3 = []
    ) {

    }
}
```

#### 4.5 抽象(abstract)，终结(final)和静态(static)

- 当用到抽象(abstract)和终结(final)来做类申明时，它们必须放在可见性申明的前面

- 而当用到静态(static)来做类申明时，则必须放在可见性申明的后面

```
<?php
namespace Vendor/Package;

abstract class ClassName
{
    protected static $foo;

    abstract protected function zim();

    final public static function bar()
    {
        // 方法主体的部分
    }
}
```

#### 4.6调用方法和函数

- 调用一个方法或者函数时，在方法名或者函数名和左括号之间不可有空格，左括号之后不可以有空格,又括号之前也不可有空格。参数列表中逗号之前不可以有空格，逗号之后则必须有一个空格。

```
<?php
bar();
$foo->var($arg1);
Foo::bar($arg1, $arg2);
```

- 参数列表可以被拆分成多个缩进了一次的子行。如果拆分成子行，参数列表中的第一项必须放在下一行，并且没一行必须只有一个参数。

```
<?php
$foo->bar(
    $longArgument,
    $intArgument,
    $arrArgument
);
```

#### 5. 控制结构

&emsp;&emsp;下面是对与空值结果代码风格的概括:

&emsp;&emsp; 1.控制结构的关键词之后必须有一个空格

&emsp;&emsp; 2.控制结构的左括号之后不可有空格

&emsp;&emsp; 3.控制结构的右括号之前之前不可以有空格

&emsp;&emsp; 4.控制结构的右括号和左花括号之间必须有一个空格

&emsp;&emsp; 5.控制结构的代码的主体必须进行一次缩进

&emsp;&emsp; 6.控制结构的右花括号必须放在主题的下一步

&emsp;&emsp; 每个控制结构的代码主题必须被括在花括号里面。这样可使代码看上去更加的标准化，并且加入新代码的时候哈可以因此而减少引入错误的可能

#### 5.1 if,elseif,else

&emsp;&emsp;下面是一个if条件控制结构的示例，注意：其中括号，空格和花括号的位置。同时注意:else和elseif 要和前一个条件控制结构的右花括号在同一行

```
<?php

if ($expr1) {
    // code segment
} elseif ($expr2) {
    // code segment
} else {
    // code segment
}
```

&emsp;&emsp;推荐使用elseif来代替else if，以保持所有的条件控制关键字看起来像是一个单词.

#### 5.2 switch,case

下面是一个switch条件控制结构的示例:注意其中括号，空格和花括号的位置。case语句必须要缩进一级,而break关键字(或者其他终止关键字)必须和case结构的代码主体在同一个缩进层级。如果一个有主体代码的case结构故意的继续向下执行则要有一个类似于// no break的注释.

```
<?php
awitch ($expr) {
    case 0:
        echo "case 0";
        break;
    case 1:
        echo "case 1";
        break;
        // no break
    case 2:
    case 3:
    case 4:
        echo "case 4";
        return;
    default:
        echo "Default case";
        break;
}
```

#### 5.3 while,do while

- 下面是一个while循环控制结构的示例，注意其中括号，空格和花括号的位置.

```
<?php
while ($expr) {
    // stucture body
}
```

- 下面是一个do while循环控制结构的示例，注意：其中括号，空格和花括号的位置。

```
<?php
do {
    // structure body
} while ($expr);
```

#### 5.4 for

 下面是一个for循环控制结构的示例，注意其中括号，空格和花括号的位置。

```
<?php
for ($i = 0;$i < 10;$i++) {
    // for body
}
```

#### 5.5 foreach

 下面是一个foreach循环控制结构，注意其中括号，空格和花括号的位置。

```
<?php

foreach ($arr as $key => $value) {
    // foreach body
}
```

#### 5.6 try,catch

 下面是一个try,catch 异常处理控制结构的示例，注意其中括号，空格和花括号的位置。

```
<?php
try {
    // try body
} catch (FirstExceptionType $e) {
    // catch body
} catch (OtherExceptionType $e) {
    // catch body
}
```

#### 6. 闭包

- 申明闭包时所用的function关键字之后必须要有一个空格,而use关键字的前后都要有一个空格

- 闭包的左花括号必须跟其在同一行，而右花括号必须在闭包主体的下一行

- 闭包的参数列表和变量列表的左括号后面不可以有空格，右花括号的前面也不可以有空格

- 闭包的参数列表和变量列表中逗号前面不可以有空格，而逗号后面则必须有空格

- 闭包的参数列表中带默认值的参数必须放在参数列表的结尾部分

下面是一个闭包的示例。注意：括号，空格和花括号的位置:

```
<?php

$cloaureWithArgs = function ($arg1, $arg2) {
    // body
}

$clasureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
    // body
}
```

参数列表和变量列表可以被拆分成多个缩进了一级的子行。如果要拆分成多个子行，列表中的第一项必须放在下一行,并且没一行必须只放一个参数或者变量。

当列表(不管是参数还是变量)最终被拆分成多个子行，右括号与左括号之间必须要有一个空格并且自成一行。

下面是一个参数列表和变量列表被拆分成多个子行的示例:

```
<?php

$longArgNOVars = function(
    $longArgument,
    $intArgument,
    $floatArgument,
    $arrayArgument
) {
    // body
};

$boArgsLongVars = function() use (
    $longArgument,
    $intArgument,
    $floatArgument,
    $arrayArgument
) {
    // body
}

$longArgNOVars = function(
    $longArgument,
    $intArgument,
    $floatArgument,
    $arrayArgument
) use (
    $longVar,
    $intVar,
    $floatArgument,
    $arrayArgument
) {
    // body
};

$longArgNOVars = function(
    $longArgument,
    $intArgument,
    $floatArgument,
    $arrayArgument
) use ($arrayArgument) {
    // body
};

$longArgNOVars = function($arrayArgument) use (
    $longVar,
    $intVar,
    $floatArgument,
    $arrayArgument
) {
    // body
}
```

当闭包作为一个参数在函数或者方法中调用时，依然要遵守上述的规则。

```
<?php

$foo->bar(
    $arg1,
    function ($arg2) use (val2) {
        // body
    },
    $arg3
);
```

#### 7.0 结论

本指南有意的省略了许多元素的代码风格，主要包括:

- 全局变量与全局常量的申明

- 函数申明

- 操作符与赋值

- 行间对齐

- 注释与文档快

- 类名的前缀和后缀

- 最佳实践
