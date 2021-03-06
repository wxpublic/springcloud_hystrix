# springcloud_hystrix
springcloud熔断器Hystrix应用，本项目采用类声明方式（非注解）实现服务降级，与springcloud_combineMaven仓库项目数同一个项目，不同之处在于服务降级处理方式：一个采用类实现Feign接口方式，一个采用降级主方法添加注解方式。

主要内容有：

使用Hystrix类方式实现实现服务降级、熔断功能！

代码摘要：

演示熔断器Hystrix; 以类方式自动实现服务降级、线程隔离、服务熔断；解决服务的雪崩效应，Hystrix有两种保护服务的实现方式：注解和类形式;本项目演示类方式！（推荐使用），以类方式实现服务降级时，远端方法调用将在新的线程池开启新的线程，采用异步线程执行，即memberServiceFeign远程调用的会员方法和订单父方法使用不同线程池不同的线程;并异步执行，即服务线程隔离！

类熔断的实现步骤：

1、定义类(比如：MemberServiceFallBack)继承memberServiceFeign 接口;

2、在类对应方法内做服务降级处理，并返回结果;

3、在memberServiceFeign接口的注解@FeignClient属性fallback值中添加定义类.class引用(MemberServiceFallBack.class);

项目其他功能：Feign客户端使用（自带ribbon负载均衡器），一些必须的参数配置；

