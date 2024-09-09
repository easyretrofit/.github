# Easy-Retrofit Integration

一个`easy-retrofit`集成应该具备一下几个要素:

1. 在resources目录下添加一个`retrofit-extension.properties`文件, 声明扩展
2. 提供了两种扩展, 分别支持Interceptor 和 RetrofitBuilder

你可以在集成中写混合写`easy-retrofit` 两种扩展, 也可以引入一个扩展, 总之, 你最终在 `retrofit-extension.properties`文件中声明扩展就好.
需要注意, 在`retrofit-extension.properties`中,可以配置多个扩展, 以逗号分割.


## 在Springboot中创建一个扩展
这里有一个示例: https://github.com/liuziyuan/easy-retrofit-integration-spring-boot-web-starter

这个示例会告诉你如何在你的Springboot项目中使用这个扩展 https://github.com/liuziyuan/easy-retrofit-demo/tree/main/retrofit-spring-boot-integration-sample

## 在Quartus中创建一个扩展

这里有一个示例: https://github.com/liuziyuan/quarkus-easy-retrofit-extension-print

这个例子描述了如何在Quarkus中创建一个在Interceptor, 实现打印前缀的扩展

这个示例会告诉你如何在你的Quarkus项目中使用这个扩展 https://github.com/liuziyuan/quarkus-easy-retrofit-extension-sample


