#	Tomcat 的配置

我们日常所说的 Tomcat 配置，大多数是针对其核心组件 Catalina 而言。

##	配置体系的构成

Tomcat/Catalina 的配置体系包含一系列配置文件，配置格式以 .xml 文件为主，也包括个别 .policy 和 .properties 文件。这些配置文件之间，既有功能的分工，也有作用域的层叠。有的配置文件的位置是固定的，由 Tomcat 程序根据特定规则直接检索；有的配置文件的位置则是在主配置文件中设置的。

*	__{$CATALINA_BASE}/conf/catalina.policy__
	>	Security Policy Permissions for Tomcat

	安全策略配置。  
	该文件遵循标准安全策略语法，这种语法是 JEE 规范的一部分。

*	__{$CATALINA_BASE}/conf/catalina.properties__  
	Catalina 性能优化的重要工具。  
	该文件遵循标准的 Java 属性文件格式。

*	__{$CATALINA_BASE}/conf/logging.properties__   
	指定服务所使用的日志工具及日志格式。  
 	该文件遵循标准的 Java 属性文件格式。

*	__{$CATALINA_BASE}/conf/context.xml__  
	>	The contents of this file will be loaded for each web application.

	应用缺省配置。  
	在 Tomcat 的语境中，context 指代 web 应用。

*	__{$CATALINA_BASE}/conf/server.xml__  
	Tomcat 核心配置文件。  
	该配置文件中的配置变更，需要重启 Tomcat 才能生效。

*	__{$CATALINA_BASE}/conf/tomcat-users.xml__  
	``server.xml::/Server/GlobalNamingResources/Resource/@pathname``

*	__{$CATALINA_BASE}/conf/web.xml__

*	__{$CATALINA_BASE}/conf/{ENGINE_NAME}/{HOST_NAME}/__

*	__{WEB_APP_HOME}/META-INF/context.xml__  

*	__{WEB_APP_HOME}/WEB-INF/web.xml__  
	``context.xml::/Context/WatchedResource[text()="${catalina.base}/conf/web.xml"]``

##	环境变量

{TOMCAT}/bin/catalina.sh 脚本文件中包含一节标题为 *Environment Variable Prerequisites* 的注释，可视为对 Tomcat 所依赖的环境变量的权威说明。

##	Connector 配置

Tomcat 在 server.xml 配置文件中定义了所启用的连接器：

```xml
<Server>
	<!-- ... -->
	<Service>
		<Connector port="8080" protocol="HTTP/1.1"
		           connectionTimeout="20000" redirectPort="8443" />
	</Service>
</Server>
```

注意，``server.xml::/Server/Service/*`` 中包括了连接器和容器配置。

##	Container 配置

容器的配置与连接器有两点显著的不同：
1.	容器的配置分散在不同的 XML 配置文件中，并且其配置元素也__不以 Container 命名__；
2.	容器允许有条件的嵌套。

###	Engine

>	An Engine represents the entry point (within Catalina) that processes every request.  
>	@cite server.xml

Engine 配置元素位于 ``server.xml::/Server/Service/Engine``，每个 ``<Service/>`` 元素中只能包含一个 ``<Engine/>`` 元素。

###	Host

###	Context

###	容器的通用配置

*	__Lisenter__

*	__Realm__

*	__Resource__

*	__Value__

##	SEE

*	*Apache Tomcat 9 Configuration Reference*  
	http://tomcat.apache.org/tomcat-9.0-doc/config/

*	*A Simple Guide To Tomcat Logging*  
	https://www.mulesoft.com/tcat/tomcat-logging
