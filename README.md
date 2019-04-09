# Kafka
This is example for Kafka learning
首先在GitHUb上创建一个仓库，然后添加Readme.md
打开本地的Github客户端，采用用户名登录之后，Clone kafka的项目到本地D盘
然后打开该文件，进行编辑。
然后打开GitHub客户端，点击Change之后，然后进行Commit就上传到GitHUb了

消息中间件
准备Zookeeper，
Zookeeper下载的地方
http://zookeeper.apache.org/releases.html#download；

Kafka下载的地方
https://www.apache.org/dyn/closer.cgi?path=/kafka/2.2.0/kafka_2.12-2.2.0.tgz

下载并安装在D:\zookeeper-3.4.14

准备Kafaka，下载并安装在D:\kafka_2.12-2.2.0

准备Redis，https://github.com/MicrosoftArchive/redis/releases

D:\Redis-x64-3.2.100
https://blog.csdn.net/qq_40784783/article/details/80610426

Window下配置Kafka以及Zookeeper环境
https://www.cnblogs.com/shike8080/p/6483123.html

设置ZookKeeper,kafaka，Redis的Home目录，增加path的路径

从BroadView上下载源码，kafka的部分

JDK1.8环境下依然报错 Unsupported major.minor version 52.0
https://blog.csdn.net/weixin_34014277/article/details/85968903
卡了半天，重新配置JAVA_HOME和PATH，项目正常运行......

要保证上面三个都是依赖jdk1.8，不然启动的时候会产生错误

原始的版本中无Tomcat插件。为方便进行调试。在Pom文件中增加了Tomcat的插件
   <plugin>
                    <groupId>org.apache.tomcat.maven</groupId>
                    <artifactId>tomcat7-maven-plugin</artifactId>
                    <version>2.2</version>
                    <configuration>
                        <path>/</path>
                        <port>8080</port>
                    </configuration>
                </plugin>
                
启动后访问
http://localhost:8080/page/second-kill-detail.html
点击秒杀，成功运行

//Listener是获取到业务数据进行相应的业务处理，比如秒杀后续的生成订单、短信通知等

在页面上秒杀动作，采用Ajax的请求。后端采用ResponseBody的方式进行回应。
这里注意@RestController注解相当于@ResponseBody ＋ @Controller合在一起的作用
https://blog.csdn.net/qq_34608620/article/details/80723843
如果采用@Controller，默认是返回页面的，如果不返回页面
 @RequestMapping(value = "buy")
    @ResponseBody
    public Map<String, Object> buy() {
        Map<String, Object> result = new HashMap<>();

        if (service.buy()) {
            result.put("buyResult", true);
            result.put("msg", "秒杀成功");
        } else {
            result.put("buyResult", false);
            result.put("msg", "没有秒到该商品");
        }

        return result;
    }



report如何调试？
一开始，report的页面出现后，click之后的，通过浏览器的F12，分析，服务端没有url。
但是服务器实际上有相应的url。只是在web.xml的配置文件中，
  <servlet>
        <servlet-name>SpringMVC</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <init-param>
            <param-name>contextConfigLocation</param-name>
            <param-value>classpath:report-spring.xml</param-value>
        </init-param>
        <load-on-startup>1</load-on-startup>
        <async-supported>true</async-supported>
    </servlet>
    
    
     <param-value>classpath:report-spring.xml</param-value>
     这个para的参数，还是原来的second-kill-spring.xml
     所以，就无法进行访问后端的资源
     
注解的使用
@Bean的定义方法？
从Spring3.0，@Configuration用于定义配置类，可替换xml配置文件，被注解的类内部包含有一个或多个被@Bean注解的方法，这些方法将会被AnnotationConfigApplicationContext或AnnotationConfigWebApplicationContext类进行扫描，并用于构建bean定义，初始化Spring容器。

与Spring结合之后，Send采用模板方式
接受的时候，采用Listener的方式。


