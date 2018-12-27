# Struts2
### 1.Struts2入门
#### Servlet 和 Filter
  - #### 共同点:
    - #### 都有3个常用方法初始化,销毁和核心方法(service,doFilter)
    - #### 他们的核心方法都有request和response
    - #### 他们都是单利对象,即一个应用只有一个对象
- #### 区别
  - #### 创建时间点不一样
    - #### Servlet 请求第一次到达时(默认情况下)
    - #### Filter 应用一加载就创建
  -  #### Filter 不是一个资源,不能通过地址栏访问
  -  #### Servlet 是一个资源,可以通过地址栏访问
#### Struts2的6个配置文件
  - #### default.properties
    - #### 应用中使用的编码
      - #### struts.i18n.encoding=UTF-8
    - #### 和spring框架整合有关
      - #### struts.objectFactory.spring.autoWire = name
    - #### 关于文件上传
      - #### struts.multipart.parser=jakarta
      - #### struts.multipart.saveDir=
      - #### struts.multipart.maxSize=2097152 默认上传大小为2MB
    - #### action后缀
      - #### struts.action.extension=action,,
    - #### 是否允许动态方法调用
      - #### struts.enable.DynamicMethodInvocation = false
    - #### 开发者模式(默认是false),开发模式:改了配置文件,不需要重启,输出更多的错误信息,开发阶段建议true
      - #### struts.devMode = false
    - #### 页面展示用的主题
       - #### struts.ui.theme=xhtml
- #### struts-default.xml(核心配置文件)
    ![](https://github.com/YuJianMuNaiYi/YuJianMuNaiYi.github.io/blob/master/images/Struts2/struts_default1.png)
  - #### 拦截器
    ![](https://github.com/YuJianMuNaiYi/YuJianMuNaiYi.github.io/blob/master/images/Struts2/interceptors.png)
#### Struts.xml配置文件说明
  ``` xml
  <?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE struts PUBLIC
        "-//Apache Software Foundation//DTD Struts Configuration 2.3//EN"
        "http://struts.apache.org/dtds/struts-2.3.dtd">
<struts>
    <!--开启开发者模式-->
    <constant name="struts.devMode" value="true"/>
    <constant name="struts.enable.DynamicMethodInvocation" value="false"/>
    <package name="myDefault" extends="struts-default" abstract="true">
        <!--全局结果视图-->
        <global-results>
            <result name="login">/login.jsp</result>
        </global-results>
    </package>
    <!-- package标签:
            作用:给访问的action进行分包管理,把配置文件按照面向对象的思想来管理。
            属性:
                name:指定包的名称。必须写,并且必须唯一。
                extends:指定当前包的父包,子包自动具备父包所定义的配置,我们的包一般都需要继承struts-default包。
                    该包在struts-default.xml文件中定义。如果不继承该包,则不能使用Struts2的核心功能。
                abstract:把当前包声明为抽象包.抽象包就是用来被继承的。里面定义的一般都是公共的配置.只有没有action标签的包,才能定义为抽象包。
                namespace:指定当前包的名称空间。它可以让我们的访问URL模块化。当我们指定了该属性，访问URL就变成了：名称空间+/hello
                    名称空间的写法：第一个字符必须是/，后面紧跟的字符必须是一个字母。其余内容可以是字母，也可以是数字。
                    名称空间有默认值：默认值是：“”
                    例如：我们访问用户
                        名称空间+/addUser.action
                        名称空间+/updateUser.action
    -->
    <!--继承自上面包名为myDefault-->
    <package name="p1" extends="myDefault">
        <!-- action标签：
                作用:建立动作名称，动作类和动作方法的对应关系
                属性：
                    name:指定动作名称，该名称是唯一的
                    class:指定动作类的全限定类名
                    method:指定动作方法名称
             动作类的三种创建方法
                第一种方式：无侵入式的     实际开发中用的不多
                    例如：HelloAction
                第二种方式：实现接口的方式  实际开发中用的不多
                    我们的动作类要实现一个接口：Action
                    例如：Hello2Action
                    默认动作方法：当我们要是执行的是execute方法时，method属性可以不写
                第三种方式：继承ActionSupport
                    例如：Hello3Action
                    默认动作类：
                        就是ActionSupport
        -->
        <action name="hello" class="com.munaiyi.web.action.HelloAction" method="sayHello">
            <!--result标签：
                  作用：用于配置结果视图(结果视图可以是一个jsp/html,也可以是一个action)
                  属性：
                    name:指定逻辑结果视图。作用就是和动作方法的返回值进行比较，当一致时，前往配置的页面或者action。不写的话默认值是:success 去哪儿
                    type:指定前往结果视图的方式。以何种方式前往。怎么去
                  type取值都是来源于struts-default.xml文件中的package名称是struts-default包中定义类型
                  常用的结果类型：
                    dispatcher:请求转发(默认值)
                    redirect：重定向
                    redirectAction：重定向到另外一个动作
                  响应浏览器的三种方式：
                    请求转发
                    重定向
                    使用流输出(如果只有一种方式，那就是此方式)
                  全局结果视图和局部结果视图
                    定义是放在action标签外面，在global-result标签内部的结果视图
                    可以在多个action中使用
                    优先级：先找局部，再找全局
            -->
            <result name="success" type="dispatcher">/success.jsp</result>
        </action>
        <action name="hello2" class="com.munaiyi.web.action.Hello2Action">
            <result name="success" type="dispatcher">/success.jsp</result>
        </action>
        <action name="hello3" class="com.munaiyi.web.action.Hello3Action">
            <result name="success" type="dispatcher">/success.jsp</result>
        </action>
        <action name="hello4">
            <result name="success" type="dispatcher">/success.jsp</result>
        </action>

        <!--<action name="addUser" class="com.munaiyi.web.action.UserAction" method="addUser">-->
        <!--<result name="success" type="dispatcher">/success.jsp</result>-->
        <!--</action>-->
        <!--<action name="updateUser" class="com.munaiyi.web.action.UserAction" method="updateUser">-->
        <!--<result name="success" type="dispatcher">/success.jsp</result>-->
        <!--</action>-->
        <!--<action name="deleteUser" class="com.munaiyi.web.action.UserAction" method="deleteUser">-->
        <!--<result name="success" type="dispatcher">/success.jsp</result>-->
        <!--</action>-->
        <!--<action name="findUser" class="com.munaiyi.web.action.UserAction" method="findUser">-->
        <!--<result name="success" type="dispatcher">/success.jsp</result>-->
        <!--</action>-->
    </package>

    <!--action的三种访问方式-->
    <!--第一种：全匹配配置访问方式
    <package name="user" extends="struts-default">
        <action name="addUser" class="com.munaiyi.web.action.UserAction" method="addUser">
            <result name="success">/success.jsp</result>
        </action>
        <action name="updateUser" class="com.munaiyi.web.action.UserAction" method="updateUser">
            <result name="success">/success.jsp</result>
        </action>
        <action name="deleteUser" class="com.munaiyi.web.action.UserAction" method="deleteUser">
            <result name="success">/success.jsp</result>
        </action>
        <action name="findUser" class="com.munaiyi.web.action.UserAction" method="findUser">
            <result name="success">/success.jsp</result>
        </action>
    </package>
    -->

    <!--第二种：使用通配符的访问方式 通配符是* -->
    <!--<package name="user" extends="struts-default">-->
    <!--<action name="*" class="com.munaiyi.web.action.UserAction" method="{1}">-->
    <!--<result name="success">/success.jsp</result>-->
    <!--<allowed-methods>addUser,updateUser,deleteUser,findUser</allowed-methods>-->
    <!--</action>-->
    <!--</package>-->

    <!--通配符高级用法 -->
    <!--<package name="user" extends="struts-default">
        <action name="*_*" class="com.munaiyi.web.action.{2}Action" method="{1}{2}">
            <result name="success">/success.jsp</result>
            <allowed-methods>addUser,updateUser,deleteUser,findUser</allowed-methods>
        </action>
    </package>-->
    <!--调用动态方法调用-->
    <package name="user" extends="struts-default">
        <action name="user" class="com.munaiyi.web.action.UserAction">
            <result name="success">/success.jsp</result>
            <allowed-methods>addUser,updateUser,deleteUser,findUser</allowed-methods>
        </action>
    </package>
</struts>
  ```
  - #### 关于Struts.xml中result标签的type取值说明
    ![](https://github.com/YuJianMuNaiYi/YuJianMuNaiYi.github.io/blob/master/images/Struts2/result-type.png)
  - #### 关于转发与重定向
    - #### 转发 
      - #### 一次请求
      - #### 地址栏不变
      - #### 请求域中数据不丢失
      - #### 服务器行为
      - #### 只能是在当前应用中转发
    - #### 重定向
      - #### 两次请求
      - #### 地址栏改变
      - #### 请求域中数据丢失
      - #### 浏览器行为
      - #### 可以定向到当前应用外部
    - #### 使用流输出
  - #### 请求参数的封装
  - #### EL表达式三个没有
    - #### 没有空指针异常
    - #### 没有字符串拼接
    - #### 没有数组越界
  - #### OGNL表达式
    - #### OGNL(Object Graph Navigation Language)对象图导航语言，可以存取Java对象的任意属性。
  - #### OGNL上下文-ContextMap
    - #### ContextMap是Struts2框架中封装数据最大的容器，封装了我们一次请求可能会用到的所有数据。
    - #### ContextMap是一个Map结构。Map的Key是String类型，Map的Value是Objece类型。
    - #### 里面内容包括但不限于如下内容：
  ```
                     |
                     |--application 它是一个Map，里面存的是应用域中的所有数据
                     |
                     |--session 它是一个Map,里面存的是会话域中的所有数据
        context map  |
                     |--value stack(root) 它是一个对象，List结构
                     |
                     |--action (the current action) 它是一个对象，表示的是当前正执行的Action对象
                     |
                     |--request 它是一个Map，里面存的是请求域中的所有数据
                     |
                     |--parameters 它是一个Map,里面存的是请求参数。request.getParameterMap()
                     |
                     |--attr (searches page, request, session, then application scopes) 它是一个Map,里面存的是四大域中的数据，并且查找是按照有小到大的顺序查找。
                     |
  ```
  - #### ActionContext以及它和ContextMap的关系
    -  #### 它是一个工具类，里面提供可以便捷操作ContextMap的方法。
    - #### ActionContext的创建时间点：每次请求都会创建新的。放在Struts2的核心过滤器中的doFilter方法，由于java ee应用是多线程的，它通过把ActionContext绑定到ThreadLocal上实现了线程同步。
  - #### ValueStack对象的调用
    - #### 也是一个工具类，它是一个List
  - #### Struts2中EL表达式的使用
  - #### Struts2中的拦截器---拦截器链(拦截器都是单例)
    - #### 过滤器和拦截器的区别？
      - #### 过滤器是servlet规范中的一部分，任何java web工程都可以使用。
      - #### 过滤器在url-pattern中配置了/*之后，可以对所有要访问的资源拦截。
      - #### 拦截器是Struts2框架自己的，只有使用了Struts2框架的工程才能用。
