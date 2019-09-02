springboot 是一个个微服务

spirngcloud 就是把这些微服务进行有机的结合和连接

两大架构，阿里的dubbo的zookeeper 和   springcloud推荐的netflix的Eureka

zookeeper 是采用RPC 远程过程调用  保证C(一致性)A(可用性)P(分区容错性)中的CP，注册中心是主从结构，主坏了必须停下来选主，此时的可用性就没了

Eureka是REST  保证 AP，全是平等的，只要有可用的就可用，但不能保证数据的强一致性。

Eureka是一个注册服务中心，就像第三方的托管机构，

最简单的Eureka至少有3个springboot，Eureka-server   、 provider   、consumer

使用起来不难，就是引入对应的jar包，然后搭配相应的注释@xxx的

Eureka-server 需要引入eureka-server的jar包，

provider  和   consumer 都需要引入  eureka-client  的jar包，都是Eureka的客户端，consumer 用一个叫RestTemplate的类来调用 provider

consumer引入eureka-client  的jar包是用来发现服务的，调用服务用Ribbon，Ribbon的使用不用引jar包，只需要在RestTemplate的方法上面加上@LoadBalanced即可

```java
@Configuration
public class BeanConfig{
    
    @LoadBalanced  //这个就是用Ribbon来调用provider的
    @Bean
    public RestTemplate restTemplate(){
        return new RestTemplate();
    }
    
}
```

Eureka-server的服务器，也是一个springboot，他要坏了怎么办？

所以需要Eureka-server服务器的集群，多台服务器，相互注册（不能自己注册自己），这样一台坏了可以找另一台