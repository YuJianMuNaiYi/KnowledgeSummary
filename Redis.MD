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
    ![](Images/Redis/Redis11.png)    
### 4.Redis客户端的使用
### 5.瑞士军刀Redis
  - #### 慢查询
    - #### 生命周期
    ![](Images/Redis/Redis12.png)    
    - #### 两个配置
      - #### slowlog-max-len
        - #### 先进先出队列
        - #### 固定长度
        - #### 保存在内存内
      - #### slowlog-log-slower-than
        - #### 慢查询阈值(单位：微秒)
        - #### slowlog-log-slower-than=0 记录所有命令
        - #### slowlog-log-slower-than<0 不记录任何命令
      - #### 默认值
        - #### config get slowlog-man-len=128
        - #### config get slowlog-log-slower-than=10000
      ![](Images/Redis/Redis13.png)    
      - #### 修改配置文件重启
      - #### 动态配置
    - #### 三个命令
      - #### slowlog get [n] 获取慢查询队列
      - #### slowlog len 获取慢查询队列长度
      - #### slowlog reset 清空慢查询队列
    - #### 运维经验
      - #### slowlog-man-len不要设置过大，默认10ms，通常设置1ms
      - #### slowlog-log-slower-than 不要设置过小，通常设置1000左右
      - #### 理解命令生命周期
      - #### 定期持久化慢查询
  - #### pipline
      ![](Images/Redis/Redis14.png)    
  - #### 发布订阅
    - #### 角色
      - #### 发布者(publisher)
      - #### 订阅者(subscriber)
      - #### 频道(channel)
    - #### 模型
      ![](Images/Redis/Redis15.png)    
      ![](Images/Redis/Redis16.png)    
    - #### API
      - #### publish
        - #### publish channel message
      - #### subscribe
        - #### subscribe [channel] 订阅一个或多个频道
      - #### unsubscribe
        - #### unsubscribe [channel] 订阅一个或多个频道
      - #### 其他API
      ![](Images/Redis/Redis17.png)            
    - #### 发布订阅与消息队列
  - #### Bitmap
    - #### setbit key offset value 给位图指定索引设置值
    - #### getbit key offset 获取位图指定索引的值
  - #### HyperLogLog
  - #### GEO
### 6.Redis持久化的取舍和选择
  - #### 持久化的作用(Redis所有数据保存在内存中，对数据的更新将异步地保存在磁盘上)
    - #### 持久化方式
      - #### 快照
        - #### MySql Dump
        - #### Redis RDB
      - #### 写日志
        - #### MySql Binlog
        - #### Hbase HLog
        - #### Redis AOF
  - #### RDB
      ![](Images/Redis/Redis18.png)            
    - #### 触发机制 主要三种方式
      - #### save(同步)
      ![](Images/Redis/Redis19.png)            
      ![](Images/Redis/Redis20.png)       
      ![](Images/Redis/Redis21.png)       
      - #### bgsave(异步)
      ![](Images/Redis/Redis22.png)       
      - #### 自动
      ![](Images/Redis/Redis23.png)       
    - #### 触发机制 不容忽略方式
      - #### 全量复制
      - #### debug reload
      - #### shutdown
    - #### RDB总结
      - #### RDB是Redis内存到硬盘的快照，用于持久化
      - #### save通常会阻塞Redis
      - #### bgsave不会阻塞Redis,但是会fork新进程
      - #### save自动配置满足任一就会被执行
      - #### 有些触发机制不容忽视
  - #### AOF
      ![](Images/Redis/Redis25.png)       
    - #### RDB现存问题
      ![](Images/Redis/Redis24.png)       
      - #### 耗时耗性能
      - #### 不可控、丢失数据
    - #### AOF三种策略
      - #### always
      ![](Images/Redis/Redis26.png)       
      - #### everysec(默认值)
      ![](Images/Redis/Redis27.png)       
      - #### no
      ![](Images/Redis/Redis28.png)     
      ![](Images/Redis/Redis29.png)       
      - #### AOF重写
        - #### 减少磁盘占用量
        - #### 加快恢复速度
      - #### AOF重写实现两种方式
        - #### bigwriteaof
      ![](Images/Redis/Redis30.png)       
      ![](Images/Redis/Redis31.png)       
      ![](Images/Redis/Redis32.png)       
      ![](Images/Redis/Redis33.png)       
  - #### RDB和AOF的抉择
    - #### RDB和AOF比较
      ![](Images/Redis/Redis34.png)       
    - #### RDB最佳策略
      ![](Images/Redis/Redis35.png)       
    - #### AOF最佳策略
      ![](Images/Redis/Redis36.png)       
    - #### 最佳策略
      ![](Images/Redis/Redis37.png)       
### 7.Redis复制的原理和优化
  - #### 主从复制
      ![](Images/Redis/Redis38.png)       
      - #### 一主一从
      - #### 一主多从
      ![](Images/Redis/Redis39.png)       
      - #### 主从复制作用
        - #### 数据副本
        - #### 扩展读性能
      - #### 总结
        - #### 一个master可以有多个slave
        - #### 一个slave只能有一个master
        - #### 数据流向是单向的，master到slave
  - #### 复制的配置
    - #### 两种方式
      - #### slaveof命令
        ![](Images/Redis/Redis40.png)       
        ![](Images/Redis/Redis41.png)       
      - #### 配置
      ![](Images/Redis/Redis42.png)     
    ![](Images/Redis/Redis43.png)           
  - #### 全量复制和部分复制
    - #### 全量复制开销
      - #### bgsave时间
      - #### RDB文件网络传输时间
      - #### 从节点清空数据时间
      - #### 从节点加载RDB的时间
      - #### 可能的AOF重写时间
    - #### 部分复制
    ![](Images/Redis/Redis44.png)           
  - #### 故障处理
    - #### slave 故障
    ![](Images/Redis/Redis45.png)           
    - #### master 故障
  - #### 开发运维常见的问题
    - #### 读写分离(读流量分摊到从节点)
    ![](Images/Redis/Redis46.png)           
      - #### 可能遇到的问题
        - #### 复制数据延迟
        - #### 读到过期数据
        - #### 从节点故障
    - #### 主从配置不一致
      - #### 例如maxmemoery不一致:丢失数据
      - #### 例如数据结构优化参数(hash-max-siplist-entries):内存不一致
    - #### 规避全量复制
      - #### 第一个全量复制
        - #### 第一个不可避免
        - #### 小主节点、低峰
      - #### 节点运行ID不匹配
        - #### 主节点重启后(运行ID变化)
        - #### 故障转移，例如哨兵或集群
      - #### 复制积压缓冲区不足
        - #### 网络中断，部分复制无法满足
        - #### 增大复制缓冲区配置rel_backlog_size,网络"增强"
    - #### 规避复制风暴
      - #### 单主节点复制风暴
        - #### 问题:主节点重启，多从节点复制
          - #### 解决:更换复制拓扑
            ![](Images/Redis/Redis47.png)           
      - #### 单机器复制风暴
        - #### 机器宕机后，大量全量复制
            ![](Images/Redis/Redis48.png)         
        - #### 主节点分散多机器  
### 8.Redis Sentinel(高可用)
### 9.Redis Cluster(分布式)