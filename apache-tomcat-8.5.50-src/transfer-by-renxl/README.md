### **翻译**

摘要
tomcat总体架构设计
参见[tomcat总体架构图.png]


一个server就是一个监听请求与处理请求的容器
为了区分具体的connector与container的映射关系
将一个server建立多个service 
同时每个service有多个connector与一个container 
并且将container抽象成引擎
通过这样的设计将网络协议解耦，一个引擎可以包含多个web应用程序Context

同时tomcat设计人员希望一台应用服务器可以支持多个域名访问而不是多个服务器
所以在engine与context之间增加了Host组件来处理域名，也就是一个engine可以包含多个host而一个host可以包含多个部署程序
而一个web应用又可以包含多个servlet【tomcat取名Wrapper】


最终初始的tomcat架构图如下:参见[tomcat总体架构图.png]

tomcat同时赋予了所有组件LifeCycle 包含启动组件start() 初始化组件init() 停止组件stop() 销毁组件destory()

tomcat通过service的executor实现service下所有组件的线程资源共享
同时适配器实现connector与container[engine]的解耦
同时pipeline与valve实现请求职责链式处理

tomcat的类加载器特性
隔离性： 不同应用不会冲突
灵活性： 不同应用互相之间热部署不影响
性能：   不加载其他web应用的jar提高性能



本翻译并非全部代码翻译
该翻译的具体任务是完成 tomcat server的核心架构源码翻译
包含 server启动 以及请求接收两部分
涉及的具体包




org.apache
  .catalina
    .connector
    .core
    .startup
  .coyote