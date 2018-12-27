# Shiro
### 1.什么是Shiro
#### Apache shiro是一个基于Java的开源的安全管理框架，它干净利落地处理身份认证，授权，企业回话管理和加密，缓存等功能。
  ![](Images/Shiro/Shiro1.png)
  - #### Authentication:认证
    - #### 验证用户是否合法。也就是登录
      - #### 需要提交身份和凭证给shiro。
      - #### Principals 用户的身份信息，是Subject的标识属性。能够唯一标识Subject。如：电话，号码，电子邮箱，身份证号码等。
      - #### Credentials 凭证：密码。是只被Subject知道的秘密值。可以是密码，也可以是数字证书。
      - #### Principals/Credentials最常见的组合：用户名/密码。在shiro中通常使用UserNamePasswordToken来指定身份和认证信息。
      - #### 认证流程
        ![](Images/Shiro/Shiro2.png)
  - #### Authorization:授权
    - #### 授予谁具有访问某些资源的权限。
  - #### Session Managemeent:回话管理
    - #### 用户登录后的用户信息通过Session Management来进行管理，不管是在什么应用中。
  - #### Cryptography:加密
    - #### 提供了常见的一些加密算法，使得在应用中可以很方便的实现数据安全。并且使用很便捷。
  - #### Web Support:web应用程序支持
    - #### shiro可以很方便的集成到web应用程序中。
  - #### Caching:缓存
    - #### Shiro提供了对缓存的支持。支持多种缓存架构：ehcache还支持缓存数据库，Redis
  - #### Concurrency:并发支持
    - #### 支持多线程并发访问
  - #### Testing:测试
  - #### Run As
    - #### 支持一个用户在允许的前提下使用另外一个身份登录。
  - #### Remember Me:记住我
### 2.Shiro架构
  ![](Images/Shiro/Shiro2.jpg)
### 3.Shiro与Spring Security比较
  - #### Shiro
    - #### 简单、灵活
    - #### 可脱离Spring
    - #### 粒度较粗
  - #### Spring Security
    - #### 复杂、笨重
    - #### 不可脱离Spring
    - #### 粒度更细

