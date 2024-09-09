# Easy Retrofit


## 🙋‍♀️ 简要介绍


`easy-retrofit`是一个轻量级的网络请求框架,它使用 Retrofit2 作为网络请求框架,在多种支持依赖注入的Java Web框架下(Springboot, Quarkus), 通过Annotation声明Retrofit, 通过依赖注入的方式隐式的实例化Retrofit对象,可以使Retrofit很容易的集成到Web框架中,并提供更多扩展的功能.

同时, `easy-retrofit`提供了一个易于扩展且无侵入性的扩展架构设计(extension),你可以创建各种基于OKHTTP3的Interceptor来完成你想要的功能.

当前, `easy-retrofit`只支持Springboot, Quarkus, 并计划对其他具有依赖注入的Java Web框架进行支持.

### 支持Spring boot
你可以参考[springboot-easy-retrofit](https://github.com/easyretrofit/springboot-easy-retrofit)的文档开始使用.

### 支持Quarkus
项目地址 [quarkus-easy-retrofit](https://github.com/quarkiverse/quarkus-easy-retrofit)
, 其中[文档](https://docs.quarkiverse.io/quarkus-easy-retrofit/dev/index.html)处在初期阶段,这里只告诉你如何引入到你的项目.并进行初步使用.
, 更多的功能请参考[springboot-easy-retrofit](https://github.com/easyretrofit/springboot-easy-retrofit)的文档.

tips: 你只需要注意替换Springboot中的`@Autowired`和`@Resource`注解为 Quarkus的`@Inject`

## 🚀 特性
`easy-retrofit`包含了几大块周边的能力
1. 自定义实现call adapter 
2. 自定义实现converter
4. 基于`easy-retrofit`扩展架构,自定义实现扩展(extension)
5. 基于`easy-retrofit`扩展架构,自定义实现集成(integration),当然集成也属于一种扩展.

## 什么是扩展
扩展是easy-retrofit中非常重要的概念, 扩展核心是基于OKHttp3的Interceptor,并提供增强功能.
其中的增强, 核心是使用Annotation的方式, 在运行时获取更多的设置参数,并将所有的设置参数传递给OkHttp3的Interceptor. 

[创建一个扩展](extension.zh_CN.md)

## 什么是集成

集成实际上也是一种扩展, 但是它与扩展不同的是, 扩展不仅仅针对OkHttp3的Interceptor, 同时也对Retrofit的builder进行了集成.

在集成中, 我们可以进行高度的定制化, 比如有这样的一个企业级应用, 它需要引入Gson Converter 和 Rxjava2 Call Adapter, 同时需要一个拦截器来处理Http Header的请求.

那么,如果你没有这个集成的话, 那么你就需要在项目中写这些集成所必须的代码,并且复用的话只能是在每一个项目里重复写一遍.

而集成则可以解决这个问题, 你只需要创建一个集成项目, 然后在集成项目里完成这些集成工作, 在发布后, 只需要在业务项目里里引入集成库即可.

[创建一个集成](integration.zh_CN.md)

## 🌈 贡献指南
对于核心项目, 如果是BUG,那么你可以创建一个PR, 并提交; 如果是新功能, 那么你可以创建一个discussion, 我们一起讨论这个有趣的提议.

对于扩展项目, 你可以在`esay-retrofit`首页的Discussions Tab中创建一个discussion,在我们讨论过后,我会为你创建相应的项目.
