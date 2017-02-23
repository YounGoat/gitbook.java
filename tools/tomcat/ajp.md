#	Tomcat vs. Apache

Tomcat 可以作为独立的 web 服务器使用，也可以作为单纯的 Servlet 容器，与 Apache 或 Nginx 等高性能 web 服务器配合使用。在后一种场景中，Tomcat 可以使用 AJP connector 直接与 Apache 通信，这种通信方式使用专用的二进制协议以提高性能。

使用默认配置启动 Tomcat 服务时，将占用三个端口：
*	8005, SHUTDOWN
*	8080, HTTP
*	8009, AJP

其中，AJP 容器通过 8009 端口接收来自 Apache 的请求，我们可以修改 server.xml 相关配置调整端口号，或者停用 AJP connector：
```xml
<Server>
	<!-- ... -->
	<Service>
		<!-- Define an AJP 1.3 Connector on port 8009 -->
		<Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />
	</Service>
</Server>
```

##	SEE

*	*The Apache Tomcat Connectors: mod_jk, ISAPI redirector, NSAPI redirector*
	http://tomcat.apache.org/connectors-doc/
