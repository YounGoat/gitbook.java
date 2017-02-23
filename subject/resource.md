#	Java Resource

“资源”实质上 Java 程序在运行时读写的数据文件。

##	常用的路径定位方法

```java
// Applet
Applet.getCodeBase();
Applet.getAudioClip(url);

// Application
System.getProperty("user.home");
System.getProperty("java.home");

// Location-Independent
this.getClass().getResource("");
this.getClass().getResource("/");
this.getClass().getClassLoader().getResource("");
ClassLoader.getSystemResource("");
Thread.currentThread().getContextClassLoader().getResource("");
ServletActionContext.getServletContext().getRealPath("/");
```

##	getResource()

```java
// file: foo/Bar.java
package foo;
class Bar {
	public static void main(String[] args) {
		// 请用 System.out.println() 方法输出所有的返回值。

		/*1*/ Bar.class.getResource("");
		/*2*/ Bar.class.getResource(".");
		/*3*/ Bar.class.getResource("/");
		/*4*/ Bar.class.getResource("/foo.json");

		/*5*/ ClassLoader.getSystemResource("");
		/*6*/ ClassLoader.getSystemResource(".");
		/*7*/ ClassLoader.getSystemResource("./foo.json");
		/*8*/ ClassLoader.getSystemResource("/");
	}
}
```

```bash
# 编译
javac -d out foo/Bar.java

# 打包
jar cf fooBar.jar -C out .

# 直接执行 .class 文件
java -cp out foo.Bar
# 相应的返回值：
# 1 file:/CWD/out/foo/
# 2 file:/CWD/out/foo/
# 3 file:/CWD/out/
# 4 null
#
# 5 file:/CWD/out/
# 6 file:/CWD/out/
# 7 null
# 8 null

# 在 .jar 中执行
java -cp fooBar.jar foo.Bar
# 相应的返回值：
# 1 jar:file:/CWD/fooBar.jar!/foo/
# 2 null
# 3 null
# 4 null
#
# 5 null
# 6 null
# 7 null
# 8 null

# 添加 foo.json 文件
mkdir CP2
touch CP2/foo.json

# 将 CP2 列入 classpath，再次直接执行 .class 文件
java -cp out:CP2 foo.Bar
# 相应的返回值：
# 1 file:/CWD/out/foo/
# 2 file:/CWD/out/foo/
# 3 file:/CWD/out/
# 4 file:/CWD/CP2/foo.json
#
# 5 file:/CWD/out/
# 6 file:/CWD/out/
# 7 file:/CWD/CP2/foo.json
# 8 null

# 调换 classpath 中目录的顺序，再次直接执行 .class 文件
java -cp out:CP2 foo.Bar
# 相应的返回值：
# 1 file:/CWD/out/foo/
# 2 file:/CWD/out/foo/
# 3 file:/CWD/CP2/
# 4 file:/CWD/CP2/foo.json
#
# 5 file:/CWD/CP2/
# 6 file:/CWD/CP2/
# 7 file:/CWD/CP2/foo.json
# 8 null


# 将 .jar 文件和 CP2 列入 classpath 并执行
java -cp fooBar.jar:CP2 foo.Bar
# 相应的返回值：
# 1 jar:file:/CWD/fooBar.jar!/foo/
# 2 null
# 3 file:/CWD/CP2/
# 4 file:/CWD/CP2/foo.json
#
# 5 file:/CWD/CP2/
# 6 file:/CWD/CP2/
# 7 file:/CWD/CP2/foo.json
# 8 null
```

##	SEE

*	*The Classpath*  
	http://www.antwerkz.com/blog/the-classpath

*	The Java™ Tutorials：*PATH and CLASSPATH*  
	https://docs.oracle.com/javase/tutorial/essential/environment/paths.html

*	The Java™ Tutorials：*Location-Independent Access to Resources*  
	http://docs.oracle.com/javase/7/docs/technotes/guides/lang/resources.html
