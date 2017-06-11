#### SESSION（会话）

&emsp;&emsp;Session 对象存储特定用户会话所需的属性及配置信息(由http无状态每个请求都是独立,无记忆)。Session 的工作机制是：为每个访问者创建一个唯一的 id (UID)，并基于这个 UID 来存储变量。UID 存储在 cookie 中，亦或通过 URL 进行传导。

#### PHP SESSION_ID 生成方法

&emsp;&emsp;PHPSESSIONID = hash_func(客户端IP + 当前时间（秒）+ 当前时间（微妙）+ PHP自带的随机数生产器)。默认机制，用磁盘文件来实现PHP会话。php.ini配置：session.save_handler = files。也可以使用redis和memcache来实现。


