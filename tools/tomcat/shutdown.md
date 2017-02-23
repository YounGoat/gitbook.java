#	停止运行 Tomcat

在 server.xml 顶级元素使用两个属性来描述 Tomcat 接收终止运行信号的方式：

```xml
 <Server port="8005" shutdown="SHUTDOWN">
	 <!-- ... -->
</Server>
```

>	The port attribute is used to specify which port Tomcat should listen to for shutdown commands. The shutdown attribute defines the command string to be listened for on the specified port to trigger a shutdown.  
>	@cite https://www.mulesoft.com/tcat/tomcat-configuration
