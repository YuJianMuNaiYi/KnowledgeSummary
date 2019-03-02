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
- #### 列表类型
- #### 集合类型
- #### 有序集合类型
### 4.Redis客户端的使用
### 5.瑞士军刀Redis
### 6.Redis持久化的取舍和选择
### 7.Redis复制的原理和优化
### 8.Redis Sentinel(高可用)
### 9.Redis Cluster(分布式)