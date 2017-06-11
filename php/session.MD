#### SESSION（会话）

&emsp;&emsp;Session 对象存储特定用户会话所需的属性及配置信息(由http无状态每个请求都是独立,无记忆)。Session 的工作机制是：为每个访问者创建一个唯一的 id (UID)，并基于这个 UID 来存储变量。UID 存储在 cookie 中，亦或通过 URL 进行传导。

#### PHP SESSION_ID 生成方法

&emsp;&emsp;PHPSESSIONID = hash_func(客户端IP + 当前时间（秒）+ 当前时间（微妙）+ PHP自带的随机数生产器)。从以上hash_func(*)中的数据采样值的内容分析，多个用户在同一台服务器时所生产的PHPSESSIONID重复的概率极低（至少为百万份之一），设想，但台动态Web Server能到2000/rps已经很强悍了。默认机制，用磁盘文件来实现PHP会话。php.ini配置：session.save_handler = files。也可以使用redis和memcache来实现。

#### PHP SESSION实现机制

&emsp;&emsp;用户第一次请求的过程中，服务端生成session_id存储到本地：ini_get(session.save_path). '/' . 'SESS_'.session_id()文件中。并且设置COOKIE，如下：

&emsp;&emsp;setcookie(session_name(),session_id(),session.cookie_lifetime,session.cookie_path,session.cookie_domain)，cookie_path默认为跟路径下面，如有需要用户完全可以自己实现一套php session处理机制

#### PHP SESSION处理流程

&emsp;&emsp;SESSOIN ID的处理流程:

&emsp;&emsp;&emsp;&emsp;1、session_start()是session机制的开始（在此之前不予许有任何输入值），它有一定概率开启垃圾回收,因为session是存放在文件中，PHP自身的垃圾回收是无效的，SESSION的回收是要删文件的，这个概率是根据php.ini的配置决定的，概率 = gc_probability/gc_divisor * 100%

&emsp;&emsp;&emsp;&emsp;2、session会判断当前是否有$_COOKIE[session_name()];session_name()返回保存session_id的COOKIE键值，php.ini中session.name = PHPSESSID 

&emsp;&emsp;&emsp;&emsp;3、如果不存在会生成一个session_id,然后把生成的session_id作为COOKIE的值传递到客户端，这一步执行了setcookie()操作，COOKIE是在header头中发送的

&emsp;&emsp;&emsp;&emsp;4、 如果存在那么session_id =$_COOKIE[session_name]，去ini_get(session.save_path). '/' . 'SESS_'.session_id()寻找文件，读取并饭序列化

&emsp;&emsp;SESSION增删操作:

&emsp;&emsp;&emsp;&emsp;1、如新添加一个值$_SESSION['test'] ='blah'; 那么这个$_SESSION只会维护在内存中，当脚本执行结束的时候，用把$_SESSION的值写入到session_id指定的文件夹中，然后关闭相关资源

&emsp;&emsp;&emsp;&emsp;2、在脚本结束的时候会执行SESSION写入操作，把$_SESSION中值写入到session_id命名的文件中，可能已经存在，可能需要创建新的文件

&emsp;&emsp;&emsp;&emsp;3、SESSION发出去的COOKIE一般属于即时COOKIE，保存在内存中，当浏览器关闭后，才会过期，假如需要人为强制过期，比如 退出登录，而不是关闭浏览器，那么就需要在代码里销毁SESSION

#### PHP SESSION 注意事项 

&emsp;&emsp;1、如果使用基于cookie的session(cookie-based sessions),那么在使用Session_start()、session_regenerate_id()等session操作之前之前浏览器不能有任何输出，否则会出现"Cannot send session cache limiter – headers already sent"错误,所以首先要确保Session_start()在开始输出之前执行,一般直接放到PHP文件的最上方.

&emsp;&emsp;2、SESSION的垃圾收集机制是比较坑爹的，他是根据概率来gc的，如果lifetime这段时间内没有请求，session无法回收。严格设置session的过期时间如下:

&emsp;&emsp;&emsp;&emsp;(1)、设置客户端cookie的lifetime为XX分钟

&emsp;&emsp;&emsp;&emsp;(2)、设置session的最大存活周期也为XX分钟(如构造请求，有漏洞)

&emsp;&emsp;&emsp;&emsp;(3)、为每个session值加入时间戳，然后在php程序调用时进行判断

&emsp;&emsp;&emsp;&emsp;(4)、使用Memcache或者redis中（前提：save_handler不是file的情况）

&emsp;&emsp;&emsp;&emsp;(5)、自己写脚本删除(肯定没有php程序调用时判断准确)

&emsp;&emsp;3、使用session_regenerate_id函数之后，会把之前设置的session变量同步到新的sid中

&emsp;&emsp;4、使用die等函数不会保存session
