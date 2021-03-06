#### php推荐标准(PSR)

psr(英文全称:PHP Standards Recommendation), 是一个叫[FIG](http://www.php-fig.org/)的组织指定的一套标准php编码规范,是PHP开发的建议标准。

psr原本有四个规范，分别是:

&emsp;&emsp; 1、[PSR-0](https://github.com/buchongyu/buchongyu.github.io/blob/master/php/codestyles/php_psr-0.MD) | [PIG](http://www.php-fig.org/psr/psr-0/) 自动加载

&emsp;&emsp; 2、[PSR-1](https://github.com/buchongyu/buchongyu.github.io/blob/master/php/codestyles/php_psr-1.MD) |  [PIG](http://www.php-fig.org/psr/psr-1/) 基本代码规范

&emsp;&emsp; 3、[PSR-2](https://github.com/buchongyu/buchongyu.github.io/blob/master/php/codestyles/php_psr-2.MD) | [PIG](http://www.php-fig.org/psr/psr-2/) 代码样式

&emsp;&emsp; 4、[PSR-3](https://github.com/buchongyu/buchongyu.github.io/blob/master/php/codestyles/php_psr-3.MD) [PIG](http://www.php-fig.org/psr/psr-3/) 日志接口

&emsp;&emsp; 5、[PSR-4](https://github.com/buchongyu/buchongyu.github.io/blob/master/php/codestyles/php_psr-4.MD) | [PIG](http://www.php-fig.org/psr/psr-4/) 自动加载增强版，PSR-4和PSR-0在功能上有所重复,最大的区别是:PSR-4类名中的下划线无任何意义,PSR-0中定义类名中的下划线会被转换成目录分割符号。

PHP中的代码[注释写法](https://github.com/phpDocumentor/fig-standards/blob/master/proposed/phpdoc.md) | [phpDocument](https://www.phpdoc.org/)

```
<?php
/**
 * class functional
 *
 * @package 说明:namespace
 * @author 作者信息
 */

 /**
  * A simole discription about clas
  *
  * 说明变量的作用
  * @var 变量的类型
  *
  * @param 说明参数类型
  * @access 说明访问权限
  * @ 说明反馈信息
  */
```

#### PHP代码格式化工具:

&emsp;&emsp; [PHP-CS-Fixer](https://github.com/stephpy/vim-php-cs-fixer)

#### PHP代码规范检查工具

&emsp;&emsp; [PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer/)

#### PHP Code Review工具

&emsp;&emsp; [Phabricator](https://www.phacility.com/) or [Gerrit](http://code.google.com/p/gerrit/downloads/list)

#### 项目管理和代码托管平台

&emsp;&emsp; [gitlab](https://about.gitlab.com/)

#### 版本控制系统

&emsp;&emsp; 1、[git](https://git-scm.com/)

&emsp;&emsp; 2、[svn](https://tortoisesvn.net/)

#### 项目管理软件

&emsp;&emsp; [禅道](http://www.zentao.net/)

#### 为什么要使用编码规范:

&emsp;&emsp;1、[MeteorSeed](http://www.cnblogs.com/MeteorSeed/archive/2012/03/21/2404656.html)

&emsp;&emsp;2、[Mark CC](http://www.aqee.net/google-coding-standards/)

&emsp;&emsp;2、[永无止境，上下求索](http://blog.csdn.net/kimylrong/article/details/7700311)

#### 参考:

&emsp;&emsp;1、[php-fig](http://www.php-fig.org/psr/)

&emsp;&emsp;2、[php psr标准](http://www.kkh86.com/it/code-standard/guide-psr-desc.html)

&emsp;&emsp;3、[google代码规范](https://github.com/zh-google-styleguide/zh-google-styleguide)
