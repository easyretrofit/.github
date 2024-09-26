# Easy Retrofit


## 🙋‍♀️ 简要介绍


`easy-retrofit`是一个使用`Retrofit2`作为基础网络请求框架,在多种支持依赖注入的Java Web框架下(Springboot, Quarkus, ...), 通过Annotation声明Retrofit, 通过依赖注入的方式隐式的实例化Retrofit对象,可以使Retrofit2很容易的集成到具有依赖注入的Web框架中,并提供更多扩展的功能.

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
1. 自定义实现retrofit的`call-adapter`
2. 自定义实现retrofit的`converter` 
3. 基于`easy-retrofit`扩展架构,自定义实现扩展(extension)
4. 基于`easy-retrofit`扩展架构,自定义实现集成(integration),当然集成也属于一种扩展.

## 自定义Adapter
当前的`easy-retrofit`提供了如下自定义Adapter的方式:

1. [adapter-simple-body](https://github.com/easyretrofit/adapter-simple-body)

这是一个同步请求的Adapter,可以返回一个JOPO对象,与请求的返回类型一致.

2. [adapter-reactor](https://github.com/easyretrofit/adapter-reactor)

这是一个可以同步或异步的Adapter,可以返回一个Mono/Flux对象. 这样允许你在业务代码里使用Flux/Mono来处理异步请求.

## 自定义Converter
当前的`easy-retrofit`提供了如下自定义Converter的方式:

1. [converter-simple-body-base-type](https://github.com/easyretrofit/converter-simple-body-base-type)
这是当你使用了[adapter-simple-body](https://github.com/easyretrofit/adapter-simple-body), 那么你需要这个Converter来完成Java 基础类型的反序列化, 否则无法处理Java基本类型的返回值.


## 📦 什么是扩展
扩展是easy-retrofit中非常重要的概念, 扩展核心是基于OKHttp3的Interceptor,并提供增强功能.

增强的方式是通过Annotation的方式, 在运行时获取更多的设置参数,并将这些设置参数传递给Interceptor来完成相应的扩展. 

扩展的实现方式可以是基于Springboot的starter, 也可以是基于Quarkus的extension.

当前的`easy-retrofit`提供了如下的扩展:

1. [retry](https://github.com/easyretrofit/extension-retry)

这是一个轻量级的重试解决方案.

计划中的扩展:

**轻量级的TimeLimiter** 对于一些场景, 我们需要更细粒度的控制超时时间, 比如在某些场景下, 我们需要设置一个更长的超时时间, 而在某些场景下, 我们需要设置一个更短的超时时间. 我们通过这个扩展, 我们可以很方便的在运行时动态修改超时时间.

**轻量级的Bulkhead** 这个扩展的目标是解决在某些场景下, 我们需要限制并发请求的数量. 通过将请求分配到不同的舱壁中，可以限制每个舱壁内的并发请求数量，从而避免资源过载。

**客户端负载均衡** 目前只想支持SpringCloud, 在云原生的环境下, 更多的服务直接使用K8S的Service来完成服务器端负载均衡. 所以暂时没有考虑针对Quarkus进行客户端负载均衡的扩展.

**限流降级sentinel** 目前已经有一个sentinel的实现, 但是并不在`easy-retrofit`社区中, 已经不再维护. 你仍旧可以在[demo](https://github.com/liuziyuan/easy-retrofit-demo)中找到他的使用方式, 但是由于easy-retrofit `core`库的重构, 已经不再支持.

**限流降级resilience4j** 计划添加.


### 创建一个扩展

阅读[创建扩展](extension.zh_CN.md)文档, 来完成你自己的第一个扩展.

## 📦 什么是集成

集成实际上也是一种扩展, 但是它与扩展不同的是, 扩展不仅仅针对OkHttp3的Interceptor, 扩展同时也对Retrofit的builder进行了集成.

在集成中, 我们可以进行高度的定制化, 比如有这样的一个企业级应用, 它需要引入Gson Converter 和 Rxjava2 Call Adapter, 同时需要一个拦截器来处理Http Header的请求.

那么,如果你没有这个集成的话, 那么你就需要在项目中写这些集成所必须的代码,并且复用的话只能是在每一个项目里重复写一遍.

而集成则可以解决这个问题, 你只需要创建一个集成项目, 然后在集成项目里完成这些集成工作, 在发布后, 只需要在业务项目里里引入集成库即可.

### 创建一个集成
阅读[创建集成](integration.zh_CN.md)文档, 来完成你自己的第一个集成.


## 关于扩展与集成
我个人期望社区能贡献更多的扩展, 扩展的实现方式可以是基于Springboot的starter, 也可以是基于Quarkus的extension.

当有一个扩展功能,我希望可以分为如下几个工程, 分别是`core`, `spring-boot-starter`, `quarkus-extension`. 这样就能保证核心功能是通用的, 而扩展功能是针对特定的框架.


## 🌈 贡献指南
对于核心项目, 如果是BUG,那么你可以创建一个PR, 并提交; 如果是新功能, 那么你可以创建一个discussion, 我们一起讨论这个有趣的提议.

对于扩展项目, 你可以在`esay-retrofit`首页的Discussions Tab中创建一个discussion,在我们讨论过后,我会为你创建相应的项目.
