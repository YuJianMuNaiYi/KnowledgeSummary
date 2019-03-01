# Vue 
## 1.概念

# Vuex
  ![](/images/Vue/Vuex.png)
- #### 核心概念
  - #### State
    - #### state就是Vuex中的公共的状态
  - #### Getters 
    - #### 将getters理解为store的计算属性，getters的返回值会根据它的依赖被缓存起来，且只有当它的依赖值发生了改变才会被重新计算。
  - #### Mutations
    - #### 理解为store中的methods。mutations保存着更改数据的回调函数，该函数官方规定叫type，第一个参数是state,第二个参数是payload,也就是自定义的参数。
- #### Actions
    - #### actions类似于mutations,不同在于：
      - #### actions提交的是mutations而不是直接变更状态。
      - #### actions中可以包含异步操作，mutations中绝对不允许出现异步。
      - #### actions中的回调函数的第一个参数是context,是一个与store实例具有相同属性和方法的对象。
- #### Modules
  - #### 由于使用单一状态树，应用的所有状态会集中到一个比较大的对象。当应用变得非常复杂时，store对象就有可能变得相当臃肿。为了解决以上问题，Vuex允许我们将Store分割成(module)。每个模块拥有自己的state、mutation、action、getter、甚至是嵌套子模块---从上至下进行同样方式的分割。