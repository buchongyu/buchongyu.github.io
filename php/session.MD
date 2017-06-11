#### SESSION（会话）

&emsp;&emsp;Session 对象存储特定用户会话所需的属性及配置信息(由http无状态每个请求都是独立,无记忆)。Session 的工作机制是：为每个访问者创建一个唯一的 id (UID)，并基于这个 UID 来存储变量。UID 存储在 cookie 中，亦或通过 URL 进行传导。

#### PHP SESSION_ID 生成方法

&emsp;&emsp;PHPSESSIONID = hash_func(客户端IP + 当前时间（秒）+ 当前时间（微妙）+ PHP自带的随机数生产器)。从以上hash_func(*)中的数据采样值的内容分析，多个用户在同一台服务器时所生产的PHPSESSIONID重复的概率极低（至少为百万份之一），设想，但台动态Web Server能到2000/rps已经很强悍了。默认机制，用磁盘文件来实现PHP会话。php.ini配置：session.save_handler = files。也可以使用redis和memcache来实现。

#### PHP SESSION实现机制

&emsp;&emsp;用户第一次请求的过程中，服务端生成session_id存储到本地：ini_get(session.save_path). '/' . 'SESS_'.session_id()文件中。并且设置COOKIE，如下：

&emsp;&emsp;setcookie(session_name(),session_id(),session.cookie_lifetime,session.cookie_path,session.cookie_domain)，cookie_path默认为跟路径下面，如有需要用户完全可以自己实现一套php session处理机制

#### PHP SESSION 注意事项 

&emsp;&emsp;1、如果使用基于cookie的session(cookie-based sessions),那么在使用Session_start()、session_regenerate_id()之前浏览器不能有任何输出，否则会出现"Cannot send session cache limiter – headers already sent"错误,所以首先要确保Session_start()在开始输出之前执行,一般直接放到PHP文件的最上方.

&emsp;&emsp;2、SESSION的垃圾收集机制是比较坑爹的，他是根据概率来gc的，如果lifetime这段时间内没有请求，session无法回收。严格设置session的过期时间如下:

&emsp;&emsp;&emsp;&emsp;(1)、设置客户端cookie的lifetime为XX分钟

&emsp;&emsp;&emsp;&emsp;(2)、设置session的最大存活周期也为XX分钟(如构造请求，有漏洞)

&emsp;&emsp;&emsp;&emsp;(3)、为每个session值加入时间戳，然后在php程序调用时进行判断

&emsp;&emsp;&emsp;&emsp;(4)、使用Memcache或者redis中（前提：save_handler不是file的情况）
