# Easy-Retrofit Extension 

一个`easy-retrofit`扩展应该具备一下几个要素:

1. 在resources目录下添加一个`retrofit-extension.properties`文件, 声明扩展
2. 创建一个OKHttp3 Interceptor, 继承`BaseInterceptor`
3. 创建一个Annotation, 它的属性作为Interceptor的需要的参数
4. 创建一个配置类, 这依赖于你使用的Web框架

## 在Springboot中创建一个扩展
这里有一个示例: https://github.com/liuziyuan/easy-retrofit-extension-print-spring-boot-starter

这个例子描述了如何在Springboot中创建一个Interceptor, 实现打印前缀的扩展

这个示例会告诉你如何在你的Springboot项目中使用这个扩展 https://github.com/liuziyuan/easy-retrofit-demo/tree/main/retrofit-spring-boot-extension-sample

## 在Quartus中创建一个扩展

这里有一个示例: https://github.com/liuziyuan/quarkus-easy-retrofit-extension-print

这个例子描述了如何在Quarkus中创建一个在Interceptor, 实现打印前缀的扩展

这个示例会告诉你如何在你的Quarkus项目中使用这个扩展 https://github.com/liuziyuan/quarkus-easy-retrofit-extension-sample




