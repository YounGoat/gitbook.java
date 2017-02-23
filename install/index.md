#	安装与配置

##	环境变量

*	*CLASSPATH*  
	该环境变量将为 JRE 指示类库路径，与 JDK 无关。```javac``` 命令以自身所在的 JDK 的 lib 目录作为默认类库，其他类库路径需要通过 ```-classpath``` 参数指定，例如：

	```bash
	javac -cp d:\apache-tomcat-7.0.47\lib\servlet-api.jar myServlet.java
	```
