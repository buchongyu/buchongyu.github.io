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

