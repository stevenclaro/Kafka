# Kafka
This is example for Kafka learning
������GitHUb�ϴ���һ���ֿ⣬Ȼ�����Readme.md
�򿪱��ص�Github�ͻ��ˣ������û�����¼֮��Clone kafka����Ŀ������D��
Ȼ��򿪸��ļ������б༭��
Ȼ���GitHub�ͻ��ˣ����Change֮��Ȼ�����Commit���ϴ���GitHUb��

��Ϣ�м��
׼��Zookeeper��
Zookeeper���صĵط�
http://zookeeper.apache.org/releases.html#download��

Kafka���صĵط�
https://www.apache.org/dyn/closer.cgi?path=/kafka/2.2.0/kafka_2.12-2.2.0.tgz

���ز���װ��D:\zookeeper-3.4.14

׼��Kafaka�����ز���װ��D:\kafka_2.12-2.2.0

׼��Redis��https://github.com/MicrosoftArchive/redis/releases

D:\Redis-x64-3.2.100
https://blog.csdn.net/qq_40784783/article/details/80610426

Window������Kafka�Լ�Zookeeper����
https://www.cnblogs.com/shike8080/p/6483123.html
��jdk֮��һ��Ҫ������Java_HOME��Ȼ����Path�����Ӹ�·�������û���������Java_HOME����ʹ����Java-version����ȷ�з�������Ȼ�޷�����zookkeeper


����ZookKeeper,kafaka��Redis��HomeĿ¼������path��·��

��BroadView������Դ�룬kafka�Ĳ���

����kafka����ȷ�ķ�ʽӦ�� kafka-server-start   ..\..\config\server.properties

JDK1.8��������Ȼ���� Unsupported major.minor version 52.0
https://blog.csdn.net/weixin_34014277/article/details/85968903
���˰��죬��������JAVA_HOME��PATH����Ŀ��������......

Ҫ��֤����������������jdk1.8����Ȼ������ʱ����������

ԭʼ�İ汾����Tomcat�����Ϊ������е��ԡ���Pom�ļ���������Tomcat�Ĳ��
   <plugin>
                    <groupId>org.apache.tomcat.maven</groupId>
                    <artifactId>tomcat7-maven-plugin</artifactId>
                    <version>2.2</version>
                    <configuration>
                        <path>/</path>
                        <port>8080</port>
                    </configuration>
                </plugin>
                
��������ʣ����Ҳ��Maven���������Tomcat7��run
http://localhost:8080/page/second-kill-detail.html
�����ɱ���ɹ�����
�������󣺷����������ɹ�������ҳ����ʵ�ʱ�򣬾�̬��Դû�����⣬����@control�ķ�������Ӧ����������2�������ļ��д���1����Web.xml�ļ��У�����1����
ע�⣺��SpringMVC���õ�ʱ��������Ҫע����2���ط�
<!-- ����Spring MVC��ǰ�˿����� -->
    <servlet>
        <servlet-name>SpringMVC</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <init-param>
            <param-name>contextConfigLocation</param-name>
            <!--<param-value>classpath:report-spring.xml</param-value>-->
            <param-value>classpath:second-kill-spring.xml</param-value>

        </init-param>
        <load-on-startup>1</load-on-startup>
        <async-supported>true</async-supported>
    </servlet>

   ����ط���Web.xmlɨ��second-kill-spring.xml�ļ���
   Ȼ����second-kill-spring.xml�ļ��У���SpringMVC��Dispatch������
    ����<context:component-scan base-package="org.study.mq.kafka.secondKill"/> ��ɨ��

   ����Second��Ŀ�Ϳ��Ա����ʡ�
   ���ʵ�ʱ��Ϊ����ʾЧ�������һ�ξͰѶ�������ɡ��ڷ�����ǰ��ո����ۣ������ڷ���ǰ�˵�ʱ��ֻ��һ���ɹ��ı�ǡ�

����report��ʱ��ҲҪ��2���ط����и�����һ����web��ɨ���xml���ƣ�����һ����Web������
���ʵ�ַ http://localhost:8080/hello



//Listener�ǻ�ȡ��ҵ�����ݽ�����Ӧ��ҵ����������ɱ���������ɶ���������֪ͨ��

��ҳ������ɱ����������Ajax�����󡣺�˲���ResponseBody�ķ�ʽ���л�Ӧ��
����ע��@RestControllerע���൱��@ResponseBody �� @Controller����һ�������
https://blog.csdn.net/qq_34608620/article/details/80723843
�������@Controller��Ĭ���Ƿ���ҳ��ģ����������ҳ��
 @RequestMapping(value = "buy")
    @ResponseBody
    public Map<String, Object> buy() {
        Map<String, Object> result = new HashMap<>();

        if (service.buy()) {
            result.put("buyResult", true);
            result.put("msg", "��ɱ�ɹ�");
        } else {
            result.put("buyResult", false);
            result.put("msg", "û���뵽����Ʒ");
        }

        return result;
    }



report��ε��ԣ�
һ��ʼ��report��ҳ����ֺ�click֮��ģ�ͨ���������F12�������������û��url��
���Ƿ�����ʵ��������Ӧ��url��ֻ����web.xml�������ļ��У�
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
     ���para�Ĳ���������ԭ����second-kill-spring.xml
     ���ԣ����޷����з��ʺ�˵���Դ

ע���ʹ��
@Bean�Ķ��巽����
��Spring3.0��@Configuration���ڶ��������࣬���滻xml�����ļ�����ע������ڲ�������һ��������@Beanע��ķ�������Щ�������ᱻAnnotationConfigApplicationContext��AnnotationConfigWebApplicationContext�����ɨ�裬�����ڹ���bean���壬��ʼ��Spring������

��Spring���֮��Send����ģ�巽ʽ
���ܵ�ʱ�򣬲���Listener�ķ�ʽ��

ҳ�汨�����ݽṹΪReportData�������ReportMetaData����һ�� �����ReportMetaData��

Constants.TOPIC_CLICK


kafka�Զ�����Ϣ���л��ͷ����л���ʽ
https://blog.csdn.net/shirukai/article/details/82152172

��������String���͵����л���Ҳ����֧��String���͵ķ����л���
���Key,Value������String���͵����л�����ô�������ݵ�ʱ�򣬿��Բ���Json��Ȼ��jsonObject.toJSONString()
Ҳ����Key����String���л���Value���ö���� Faston��json����Ȼ���ڽ��ն�Ҳ����fastson�����ܵ���JsonתΪ����Json���ڶ�̬��������Ƿǳ��ķ��㣬�Ҹо��ҵ�����Ķ�̬���Եķ���
����ǳ�����Ҫ��

ע�⣬�Ƚ�һ��Netty�����л�������ط������л�����ʲô��ͬ��

��ǰ���µİ汾����ȥ���ǣ�Report���֡�
���Է��ʵķ�ʽ��http://localhost:8080/hello
�������ɱ����Ŀ����ô����web.xml�н��и���һ������xml�������ļ��и���һ�¡��Ϳ����ˡ�

