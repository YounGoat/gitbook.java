#	Maven Plugins

>	Maven is - at its heart - a plugin execution framework; all work is done by plugins.
>	https://maven.apache.org/plugins/index.html

在 POM 中，插件以依赖（dependency）的形式存在，除了必须的 GNV 之外，它还必须指定 ``<scope>...</scope>`` 即生效阶段。

##	直接执行插件

```bash
mvn <plugin-prefix>:<goal>
mvn <plugin-group-id>:<plugin-artifact-id>[:<plugin-version>]:<goal>
```

##	SEE

*	*Available Plugins*  
	http://maven.apache.org/plugins/


*	*Guide to Configuring Plug-ins*  
	http://maven.apache.org/guides/mini/guide-configuring-plugins.html
