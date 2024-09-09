# Easy Retrofit


## 🙋‍♀️ 简要介绍
`easy-retrofit`是一个基于retrofit库,在多种支持依赖注入的Java Web框架下(Springboot, Quarkus), 通过Annotation声明Retrofit, 通过依赖注入的方式隐式的实例化Retrofit,可以使Retrofit很容易的集成到Web框架中,并提供更多扩展的功能.

同时, `easy-retrofit`提供了一个易于扩展且无侵入性的扩展架构设计(extension),你可以创建各种基于OKHTTP3的Interceptor来完成你想要的功能.

`easy-retrofit`包含了几大块周边的能力
1. 自定义实现call adapter 
2. 自定义实现converter
4. 基于`easy-retrofit`扩展架构,自定义实现扩展(extension)
5. 基于`easy-retrofit`扩展架构,自定义实现集成(integration),当然集成也属于一种扩展.


## 🌈 贡献指南
对于核心项目, 如果是BUG,那么你可以创建一个PR, 并提交; 如果是新功能, 那么你可以创建一个discussion, 我们一起讨论这个有趣的提议.

对于扩展项目, 你可以在`esay-retrofit`首页的Discussions Tab中创建一个discussion,在我们讨论过后,我会为你创建相应的项目.
