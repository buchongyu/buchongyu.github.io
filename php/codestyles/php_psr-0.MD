#### PSR-0自动加载规范

> 已经deperate 推荐使用PSR-4

下文描述了若要使用一个通用的`自动加载器`，你需要遵守的规范:

#### 规范

- 一个完全标准的命名空间(namespace)和类(class)的结构是这样定义的: \<Vendor Name>\(<Namespace>\)*<Class Name>

- 每个命名空间(namespace)都必须有一个顶级的空间名(nemspace)(组织名(Vendor Name))

- 每个命名空间(namespace)中可以更具需要使用任意数量的子命名空间(sub-namespace)

- 从文件系统中加载资源时，命名空间中的分割符将被转为DIRECTORY_SEPARATOR

- 类名(class name)中的每个下滑线_都被转换成一个DIRECTORY_SEPARATOR，下划线_在空间名(namespace)中没有什么特殊的意义。

- 完全标准的命名空间(namespace)和类(class)从文件系统加载源文件时将会加上.php后缀

- 组织名(vendor name)，空间名(namespace)，类名(class name)都由大小写字母组合而成

#### 示例

- \Doctrine\Common\IsolatedClassLoader  => /path/to/project/lib/vendor/Doctrine/Common/IsolatedClassLoader.php

- \Symfony\Core\Request                 => /path/to/project/lib/vendor/Symfony/Core/Request.php

- \Zend\Acl                             => /path/to/project/lib/vendor/Zend/Acl.php

- \Zend\Mail\Message                    => /path/to/project/lib/vendor/Zend/Mail/Message.php

#### 空间名(namespace) 和类名(classname) 中的下划线

以下是我们为实现通用的自动加载而指定的最低标准。可以利用php 5.3类的SplClassLoader来测试代码是否符合标准

- \namespace\package\Class_Name => /path/to/project/lib/vendor/namespace/package/Class/Name.php
- \namespace\package_name\Class_Name => /path/to/project/lib/vendor/namespace/package_name/Class/Name.php

#### 实例

下面是一个咋样利用上述标准来实现自动加载的示例函数，也可以使用`spl_autoload_register`函数

```
<?php

function autoload($className)
{
    $className = ltrim($className, '\\');
    $fileName  = '';
    $namespace = '';
    if ($lastNsPos = strrpos($className, '\\')) {
        $namespace = substr($className, 0, $lastNsPos);
        $className = substr($className, $lastNsPos + 1);
        $fileName  = str_replace('\\', DIRECTORY_SEPARATOR, $namespace) . DIRECTORY_SEPARATOR;
    }
    $fileName .= str_replace('_', DIRECTORY_SEPARATOR, $className) . '.php';

	require $fileName;
}
```

#### SplClassLoader的实现

下面的gist是一个按照上面建议的标准来自动加载类的SplClassLoader实例。这是依据这些标准来加载PHP 5.3类的推荐方案。

+ [gist](http://gist.github.com/221634)
