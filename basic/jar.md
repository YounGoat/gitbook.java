#	Java Archive (JAR) 和 jar 命令

>	Often a number of Java files will be packed together in a manner similar to the UNIX .tar files. The Java analog is .jar files, which are created and unpacked using the jar command and the xf option, similar to the UNIX tar.  
>	The program java also has a -jar option, allowing you to execute a program without unpacking the .jar file.  
>	In referencing a .jar file via a classpath, the .jar file name must be included in the path, not just the directory
containing it.
>	@cite [A Quick, Painless Introduction to the Java Programming Language](http://heather.cs.ucdavis.edu/~matloff/Java/JavaIntro.html)

>	A JAR file is essentially a zip file that contains an optional META-INF directory.
>	@cite [JAR File Specification](http://www.tutorialspoint.com/java/java_quick_guide.htm)

##	素材准备

我们假定有以下类文件：

```bash
+ out/Hello.class
+ out2/foo/Man.class
# 主类 Hello 依赖 foo.Man。
```

##	创建

```bash
# 创建 jar 文件
jar cf Hello.jar out/*.class

# 运行 jar 文件中的类
java -classpath out2:Hello.jar Hello
# 对于解释器来说，jar 文件和普通的类目录并无区别。

# 分解 jar 文件
jar xf Hello.jar
# 或者，也可以用以下命令之一来分解 jar 文件，这直观地表明 jar 实质也是一个 zip 格式文件。
tar xf Hello.jar
unzip Hello.jar
```

##	MANIFEST.MF

分解 jar 文件后，我们将会得到一个额外的目录：
```bash
META-INF/
META-INF/MANIFEST.MF
# ...
```
MANIFEST.MF 是一个基于 RFC822 构建的数据文件，它可以进一步描述 jar 文件的内部构造。

###	Main-Class：指定 JAR 的主类（启动类）

首先，创建作为 MANIFEST 载体的文本文件，添加一行描述信息：
```bash
# manifest.txt
# 注意：真实的 MANIFEST 文件中不能添加注释。
Main-Class: Hello
```

然后，创建 jar 文件并执行：
```bash
jar cfm Hello.jar manifest.txt -C out . -C out2 .
# -C out 指示临时切换工作目录到 out 目录，然后将该目录下的所有文件添加到 jar 文件中。
# 目的是避免 jar 文件中将包括 out 这个目录结构。

# 执行带默认主类的 jar 文件。
java -jar Hello.jar
```
请特别留心，选项 fm 的顺序必须和相应的参数值（即 Hello.jar 和 manifest.txt）的顺序保持一致。为什么非要将选项和参数分别集中书写，而不是将相应的选项和参数成对书写呢？这真是一种奇怪的实践！

###	Class-Path：指定 JAR 运行时类路径

```bash
#  创建 jar 文件时，不包含依赖项。
jar cfm Hello.jar manifest.txt -C out .

# 注意：如果使用了 -jar 参数，则解释器将忽略 -classpath 参数。
# 因此，以下命令无法得到预期效果。
java -classpath out2 -jar Hello.jar

# 只能将 jar 文件作为类目录之一，并指定主类执行。
java -classpath out2:Hello.jar Hello
```

我们也可以添加 MANIFEST 属性 Class-Path 来解决：
```bash
# manifest.txt
Main-Class: Hello
# 增加 Class-Path 属性。必须后缀路径分隔符，以指示这是一个目录。
Class-Path: out2/
```

##	创建可执行的 JAR


##	SEE

*	*JAR File Overview*  
	http://docs.oracle.com/javase/6/docs/technotes/guides/jar/jarGuide.html

*	*JAR File Specification*  
	http://docs.oracle.com/javase/6/docs/technotes/guides/jar/jar.html

*	*Working with Manifest Files: The Basics*  
	https://docs.oracle.com/javase/tutorial/deployment/jar/manifestindex.html

	*	*Setting an Application's Entry Point*  
		https://docs.oracle.com/javase/tutorial/deployment/jar/appman.html

*	*JAR files revealed*   
	English https://www.ibm.com/developerworks/library/j-jar/  
	中文版 http://www.ibm.com/developerworks/cn/java/j-jar/

##	REL

*	*RFC822: Standard for ARPA Internet Text Messages*  
	https://www.w3.org/Protocols/rfc822/  
