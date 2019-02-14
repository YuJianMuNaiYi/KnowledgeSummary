# Mybatis
### 1.Mybatis配置文件SqlMapConfig.xml
### 2.Mybatis核心
  - ### Mybatis输入映射
    - ### parameterType
      - #### 在映射文件中通过parameterType指定输入参数的类型
    - ### retultType
      - #### 在映射文件中通过resultType指定输出结果的类型
    - ### #{}和&sect;{}
      - #### #{}表示一个占位符。
        - #### #{}接收输入参数，类型可以是简单类型，pojo,hashmap。如果接收简单类型，#{}可以写成value或其他名称。
        - #### #{}接收pojo对象值，通过OGNL表达式读取对象中的属性值，通过属性.属性。
      - #### &sect;{}表示一个拼接符号，会引用sql注入，所以不建议使用。${}接收输入参数，类型可以是简单类型，pojo,hashmap。如果接收简单类型，#{}只能写成value
    - ### selectOne和selectList
      - #### selectOne表示查询出一条记录进行映射。如果使用selectOne可以实现，使用selectList也可以实现(list中只有一个对象)。
      - #### selectList表示查询出一个列表(多条记录)进行映射。
  - ### Mybatis输出映射
    - #### resultType
      - #### 使用resultType进行输出映射，只有查询出来的列名和pojo中的属性名一致，该列才可以映射成功。
      - #### 如果查询出来的列名和pojo中的属性名全部不一致，则不会创建pojo对象。
      - #### 只要查询出来的列名和pojo中的属性有一个一致，就会创建pojo对象。
    - #### resultMap
      - #### 可以通过resultmap完成一些高级映射。
      - #### 如果查询到的列名和映射的pojo的属性名不一致时，通过resultmap设置列名和属性名之间的对应关系(映射关系)，完成映射。
      - #### 高级映射
        - #### 将关联查询到的列映射到一个pojo属性中。(一对一)
        - #### 将关联查询的列映射到一个list<pojo>中。(一对多)
  - ### Mybatis和hibernate本质区别和应用场景
    - #### hibernate
      - #### 是一个标准ORM框架(对象关系映射)，入门门槛较高的，不需要程序写sql,sql语句自动生成了。对sql语句进行优化，修改比较困难。
      - #### 应用场景：适用于需求变化不多的中小型项目，比如，后台管理系统，erp,cms,oa。
    - #### Mybatis
      - #### 专注是sql本身，需要程序员自己编写sql语句，sql修改、优化比较方便。Mybatis是一个不完全的ORM框架，虽然程序员自己写sql，Mybatis也可以实现映射(输入映射、输出映射)。
      - #### 应用场景：适用于需求变化较多的项目，比如，互联网项目。
### 3.SqlMapConfig.xml
  - #### properties 属性
  - #### settings 全局参数配置
  - #### typeAliases 别名
    - #### 默认支持的别名
      | 别名 |映射的类型
      | ------ | ------ |
      | _byte | byte
      |_long | long
      |_short | short
      |_int | int
      |_integer|int
      |_double| double
      |_float|float
      |_boolean|boolean
      |string|String
      |byte|Byte
      |long|Long
      |short|Short
      |int|Integer
      |integer|Integer
      |double|Double
      |float|Float
      |boolean|Boolean
      |date|Date
      |decimal|BigDecimal
      |bigdecimal|BigDecimal
      |map|Map
    - #### 自定义别名
      - #### 单个别名定义
      - #### 批量别名定义
### 4.动态Sql
  - #### if判断
  - #### where
  - #### foreach
  - #### Sql片段
### 5.高级映射
  - #### 实现一对一查询、一对多查询、多对多查询。
  - #### 延迟加载
### 6.查询缓存
  - #### 一级缓存
  - #### 二级缓存(了解Mybatis二级缓存应用场景)
### 7.Mybatis框架
