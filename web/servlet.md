#	Servlet

##	Hello World!

```java
import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

public class HelloWorld extends HttpServlet {

    public void doGet(HttpServletRequest request, HttpServletResponse response)
    throws IOException, ServletException
    {
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<html>");
        out.println("<head>");
        out.println("<title>Hello World!</title>");
        out.println("</head>");
        out.println("<body>");
        out.println("<h1>Hello World!</h1>");
        out.println("</body>");
        out.println("</html>");
    }
}

// @cite /examples/servlets/helloworld.html
```

##	编译

Servlet 属于 J2EE，不属于 Java Standard 的一部分，因此使用 JDK 编译时，须指定 -cp / -classpath 参数：

```bash
javac -cp ${CATALINA_BASE}/lib/servlet-api.jar HelloWorld.java
```

##	在 Tomcat 中使用 Servlet

了解如何在 Tomcat 中使用 servlet 的简便途径，是模仿 Tomcat 默认应用 /examples 的配置：

```bash
{$CATALINA_BASE}/webapps/examples/WEB-INF/web.xml
# CATALINA_BASE 代表 Tomcat 的安装路径。
```

分解步骤如下：

###	安置 .class/.jar 文件

类文件应当安置在环境变量 ``${CLASS_PATH}`` 指定的目录下。除此之外，还有两个位置可以选择：

*	__Tomcat 默认库目录__  
	位于 ``${CATALINA_BASE}/lib/``；或者  
*	__应用库目录__  
	位于 ``{WEB_APP_BASE}/WEB-INF/classes``。

###	配置

取决于你希望在全局（整个 Tomcat 实例）或局部（特定应用）使用，有不止一处可以添加有关 servlet 的配置。通常建议将其放在应用的 web.xml 文件中：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                      http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
  version="4.0"
  metadata-complete="true">

  <servlet>
    <servlet-name>hello</servlet-name>
    <servlet-class>HelloServlet</servlet-class>
  </servlet>

  <servlet-mapping>
    <servlet-name>hello</servlet-name>
    <url-pattern>/hello</url-pattern>
  </servlet-mapping>

</web-app>
```

如果配置文件不存在，那就创建一个。

###	访问

```bash
# 假定应用名为 demo
http://localhost:8080/demo/hello
```

注意：如果 class 变更，需要重新启动 Tomcat 才能生效。

##	SEE


*	*Java Servlet Technology*  
	http://www.oracle.com/technetwork/java/index-jsp-135475.html

*
	https://java.net/downloads/servlet-spec/Final/servlet-3_1-final.pdf

*	*Servlet 工作原理解析*  
	http://www.ibm.com/developerworks/cn/java/j-lo-servlet/index.html
