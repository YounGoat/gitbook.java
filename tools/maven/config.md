#	Maven 的配置

##	环境变量

*	*MAVEN_OPTS*

##	配置文件

*	__全局配置__

	```bash
	# Mac OS X
	{MAVEN_HOME}/libexec/conf/settings.xml
	{MAVEN_HOME}/libexec/conf/toolchains.xml
	```

*	__用户配置__

	```bash
	{USER_HOME}/.m2/settings.xml
	```

*	__项目配置__

	```bash
	{PROJECT_HOME}/.mvn/maven.config
	extensions.xml
	```

##	SEE

*	*Configuring Maven*  
	http://maven.apache.org/guides/mini/guide-configuring-maven.html

*	*Settings Reference*  
	http://maven.apache.org/settings.html
