catalina.policy tomcat运行在安全模式下的安全策略配置
catalina.properties 环境变量配置
context.xml 用于定义所有web应用需要加载的context配置，如果web应用指定自己的context.xml则会被覆盖

jaspic-providers.xml
jaspic-providers.xsd

logging.properties 日志配置 包含日志级别 日志路径等等

server.xml tomcat核心配置文件 用于配置tomcat 的connector 监听端口  Host等，该配置为catalina创建Server的参考

tomcat-users.xml 定义tomcat的用户 角色等 tomcat的manager模块采用该配置进行用户安全认证
tomcat-users.xsd


web.xml 部署描述文件 定义servlet与MIME的映射 如果应用中包含web.xml则tomcat会结合该配置与部署程序的配置并已部署程序配置为优先配置



自8.0开始 tomcat开始支持Servlet3.1
自8.0开始使用NIO 取代7.0的BIO ,自8.5开始不再支持BIO
自8.0开始采用异步日志 同时支持HTTP2 与NIO2

