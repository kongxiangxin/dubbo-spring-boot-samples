> 本示例基于dubbo-spring-boot-project 2.7.3版本，可能会根据新版的发布而过时，阅读时请注意。


关于dubbo在spring-boot中该如何使用，网上有很多例子，但因为时间跨度太久，很多例子已经过时了，一切还是要以官方的例子为准。

在github上搜索dubbo和spring-boot整合的项目的话，可能会找到下面两个，分别是
1. [alibaba / dubbo-spring-boot-starter](https://github.com/alibaba/dubbo-spring-boot-starter)
2. [apache / dubbo-spring-boot-project](https://github.com/dubbo/dubbo-spring-boot-project)

第一个项目，已经归档了（archived），不再更新，所以我们要以第二个项目为准，千万别搞错了。

打开第二个项目的主页，就开始浏览README中的Getting Started章节。 这个章节给我们展示了一个无注册中心（dubbo.registry.address=N/A）的例子。

但是它却跑不起来，消费者启动后无法找到service provider，报Not found exported service的错误。

需要在消费者Reference服务提供者时，url里指明version。其实version已经指明了，但不知为何还要在url里再次指定。
```
//  @Reference(version = "1.0.0", url = "dubbo://127.0.0.1:12345")
    @Reference(version = "1.0.0", url = "dubbo://127.0.0.1:12345?version=1.0.0")
    private DemoService demoService;
```

