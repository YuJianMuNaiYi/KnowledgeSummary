# Redis
### 1.特点
- ### 开源
- ### 速度快
  - ### 数据存在于内存中
  - ### 是用C语言编写
  - ### 单线程模型
- ### 高性能Key-Value服务器
- ### 持久化
  - ### Redis所有数据保持在内存中，对数据的更新将异步地保存到磁盘上
- #### 多种数据结构
  - #### BitMap 位图
  - #### HyperLogLog 超小内存唯一值计数
  - #### GEO 地理信息定位
- #### 支持多种编程语言
- #### 丰富的功能
  - #### 发布订阅
  - #### Lua脚本
  - #### 事务
  - #### pipeline
- #### 简单
  - #### 不依赖外部库
  - #### 单线程模型
- #### 主从复制
- #### 支持高可用分布式
### 2.Redis初始
  - #### Redis典型应用场景
    - #### 缓存系统
    - #### 计数器
    - #### 消息队列系统
    - #### 排行榜
    - #### 社交网络
    - #### 实时系统
  - #### Redis安装
  - #### 可执行文件说明
    - #### redis-server 启动redis服务器
    - #### redis-cli redis命令行客户端
    - #### redis-benchmark redis性能测试工具
    - #### redis-check-aof AOF文件修复工具
    - #### redis-check-dump RDB文件检查工具
    - #### redis-sentinel Sentinel服务器(2.8以后)
  - #### 三种启动方式
    - #### 最简启动
    - #### 动态参数启动
    - #### 配置文件启动
  - #### 三种启动方式比较
    - #### 生产环境选择配置文件启动
    - #### 单机多实例配置文件可以用端口区分开
  - #### 简单的客户端连接
  - #### Redis客户端返回值
    ![](Images/Redis/Redis01.png)
    ![](Images/Redis/Redis02.png)
  - #### Redis常用配置
    - #### daemonize 是否是守护进程(no|yes)
    - #### port Redis对外端口号
    - #### logfile Redis系统日志
    - #### dir Redis工作目录
  - #### 查看Redis配置
    ![](Images/Redis/Redis03.png)
  - #### 查看Redis配置(配置文件名称:redis-6381.conf,去除配置文件中注释部分以及空格部分)
    ![](Images/Redis/Redis04.png)
### 3.API的理解和使用
- #### 通用命令
  - #### 通用命令
    - #### keys(遍历所有key)
        ![](Images/Redis/keys.png)
    - #### dbsize(计算key的总数)
    - #### exists key(检查key是否存在)
    - #### del key(删除指定key-value)
    - #### expire key seconds key过期时间
    - #### ttl key(查看key剩余的过期时间)
    - #### persist key(去掉Key的过期时间)
    - #### type key(返回key的类型)
    ![](Images/Redis/Redis05.png)  
  - #### 数据结构和内部编码
    ![](Images/Redis/Redis06.png)  
  - #### 单线程架构
- ####  字符串类型
    ![](Images/Redis/Redis07.png)  
- #### 哈希类型
  - #### hget key field 获取hash key对应的field的value
  - #### hset key field 设置hash key对应的field的value
  - #### hdel key field 删除hash key对应的field的value
  - #### hexists key field 判断hash key是否有field
  - #### hlen key 获取hash key field的数量
  - #### hgetall key 获取hash key对应所有的field和value
  - #### hvals key 获取hash key对应所有field的value
  - #### hkeys key 获取hash key对应所有的field
- #### 列表类型(有序，重复，左右两边插入弹出)
    ![](Images/Redis/Redis08.png)  
- #### 集合类型(无序，无重复，支持集合间操作)
  - #### sadd key element 向集合key添加element(如果element已经存在，添加失败)
  - #### srem key element 将集合key中的element移除掉
  - #### scard 计算集合大小
  - #### sismember 判断某个元素是否存在于集合中
  - #### srandmember 从集合中随机取出一个元素，不会破坏集合
  - #### smembers 获取集合中的所有元素
  - #### spop 从集合中弹出一个元素
  - #### sdiff 差集
  - #### sinter 交集
  - #### sunion 并集
    ![](Images/Redis/Redis09.png)  
    ![](Images/Redis/Redis10.png)    
- #### 有序集合类型(无重复元素，有序，element+score)
  - #### zadd key score element (可以是多对，添加score和element)
  - #### zrem key element (可以是多个) 删除元素
  - #### score key element 返回元素的分数
  - #### zincrby key inscrScore element 增加或减少元素的分数
  - #### zcard key 返回元素的总个数
  - #### zrank 获取元素排名
  - #### zrange key start end [withscores] 返回指定索引范围内的升序元素[分值]
### 4.Redis客户端的使用
### 5.瑞士军刀Redis
### 6.Redis持久化的取舍和选择
### 7.Redis复制的原理和优化
### 8.Redis Sentinel(高可用)
### 9.Redis Cluster(分布式)