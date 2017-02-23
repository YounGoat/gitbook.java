#	Mac OS X 中的 Java

## 	Where is Java in Mac OS X?

>	The Java Runtime (JRE) that you download from java.com or oracle.com contains a plugin to run Java content from your browser. In order to use the command line tools, you will need to download the Java Development Kit (JDK). The JRE and JDK are separate and can coexist on your system. Only one JRE can be installed on Mac OS X. There can be multiple JDKs installed on a system, as many as you wish.  
>	@cite https://java.com/en/download/help/version_manual.xml#cmdline

```bash
# 显示当前有效的 Java Home
/usr/libexec/java_home

# 列出本次所安装所有版本的 Java Home
/usr/libexec/java_home -V

/System/Library/Frameworks/JavaVM.framework/
/Library/Internet\ Plug-Ins/JavaAppletPlugin.plugin/Contents/Home/bin/java
/Library/Java/JavaVirtualMachines/
```

##	SEE

*	*Information and system requirements for installing and using Oracle Java on Mac OS X*  
	https://java.com/en/download/faq/java_mac.xml
