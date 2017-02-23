#	JSP, Java Server Page


##	Tomcat 与 JSP

Tomcat 默认通过 Jasper 支持 JSP 运行，配置见：
```
${CATALINA_BASE}/conf/web.xml::/web-app/servlet
```

Tomcat 在运行时监视 .jsp 文件的变化，自动执行编译并将生成的类文件保存在下述目录中：
```
${CATALINA_BASE}/work/{ENGINE_NAME}/{HOST_NAME}/
```
这些类文件才是供 JVM 执行的中间代码。

##	JSP 生命周期

*	Compilation
*	Initialization
*	Execution
*	Cleanup

##	SEE

*	WIKIPEDIA: *JavaServer Pages*  
	https://en.wikipedia.org/wiki/JavaServer_Pages

*	*JSP Tutorial*  
	http://www.tutorialspoint.com/jsp/
