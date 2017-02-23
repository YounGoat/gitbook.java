#	Maven 快速入门

命令基础形式：
```bash
mvn [options] [<goal(s)>] [<phase(s)>]
```
Maven 命令可以同时指定多个目标（goal）和生命周期阶段（phase），其执行顺序即取决于调用顺序。e.g.

```bash
mvn archetye
```

常用选项：
*	-D, --define  
	定义系统参数。

*	-X, --debug  
	打开调试模式。当你执行 mvn 命令未及预期，却茫然无措时，调试模式是非常有用的发现问题的手段。


##	mvn archetype:generate

```bash
# 确认 maven 及 JDK 已安装成功。
mvn -v

# 创建一个新项目。
mvn archetype:generate -DgroupId=com.mycompany.helloworld -DartifactId=helloworld -Dpackage=com.mycompany.helloworld -Dversion=1.0-SNAPSHOT
```

###	Blocked On "Generating project in Interactive mode"?

由于需要访问网络资源，这一命令在执行中可能会长时间地卡在这一环节：
```
[INFO] Generating project in Interactive mode
```

可以通过预先下载 archetype-catalog 来解决这一问题：
```bash
# 切换到 maven 用户目录。
cd ~/.m2/

# 下载目录文件。
wget http://repo.maven.apache.org/maven2/archetype-catalog.xml
```

再次执行 maven 命令，并指定参数 ``-DarchetypeCatalog=local``：
```bash
mvn archetype:generate -DgroupId=com.mycompany.helloworld -DartifactId=helloworld -Dpackage=com.mycompany.helloworld -Dversion=1.0-SNAPSHOT -DarchetypeCatalog=local
```

archetype 插件专门提供了一个功能（goal）来生成目录文件：
```bash
# 从本地库中提取目录。
mvn archetype:crawl
# OUTPUT: ~/.m2/repository/archetype-catalog.xml
```

##	mvn package

```bash
# 切换到项目根目录，并执行 maven 命令。
cd helloworld

# 编译并打包。
mvn package

# 执行。
java -cp target/helloworld-1.0-SNAPSHOT.jar com.mycompany.helloworld.App
```

###	[ERROR] javac: source release 1.6 requires target release 1.6

请修改 pom.xml 文件，变更编译行为的 JVM 适配版本：

```xml
<build>
	<plugins>
		<plugin>
			<groupId>org.apache.maven.plugins</groupId>
			<artifactId>maven-compiler-plugin</artifactId>
			<version>2.3.2</version>
			<configuration>
				<source>1.6</source>
				<target>1.6</target>
			</configuration>
		</plugin>
	</plugins>
</build>
```

##	SEE

*	*Apache Maven 入门篇*  
	http://www.oracle.com/technetwork/cn/community/java/apache-maven-getting-started-1-406235-zhs.html
