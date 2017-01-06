#	快速入门

##	准备工作

###	软件安装

在本章中，我们将会使用 JDK 自带的三个命令：

*	*javac* - Java compiler  
	用于编译源代码并生成类文件（.class）。

*	*java* - Java appliction launcher  
	用于执行已编译的类文件。

*	*jar* - Java archive tool  
	用于创建特定的包文件（.jar）。

在使用 JDK/JRE 命令族时，需要注意以下几点：

*	命令中的长格式参数名以__一个横线__（dash）而不是习惯上的两个横线起首：
	```bash
	java -version  # 正确
	java --version # 错误
	```
	也因此，

*	命令参数必须书写完整：
	```bash
	java -version  # 正确
	java -ver      # 错误
	```

*	命令参数是大小写敏感的：
	```bash
	java -version  # 正确
	java -Version  # 错误
	```

这些习惯也被 Java 系的软件所继承（比如 Maven），也算是一种文化的传承。此外，JDK / JRE 命令族也有一些通用或准通用的参数选项:

*	*-classpath*  
	指定类检索路径。

*	*-X<name>*  
	使用非标准的选项。单独使用 -X 选项可以列举可用的非标准选项。

*	*-D<name>=<value>*  
	这是非常特殊的选项，用于提交预定义选项之外的数据。

##	编译

```bash
mkdir out
# javac 虽然可以指定输出目录，但该目录必须已经存在。

javac -d out Hello.java
```

##	运行
