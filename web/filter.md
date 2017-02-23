#	Filter，过滤器

有了 servlet 的经验，学习如何编写和使用 filter 就简单多了。

##	HelloFilter

```java
import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

public class HelloFilter implements Filter {

	@Override
	public void init(FilterConfig arg) throws ServletException {
		System.out.println("HelloFilter initialized");
	}

	@Override
	public void doFilter(ServletRequest req, ServletResponse res,
	                     FilterChain chain) throws IOException, ServletException {
		HttpServletRequest request = (HttpServletRequest)req;
		System.out.println("HelloFilter touched by " + request.getRequestURI());
		chain.doFilter(req, res);
	}

	@Override
	public void destroy() {
		System.out.println("HelloFilter destroyed");
	}
}
```

##	编译

Filter 的编译同样依赖 servlet-api：

```bash
javac -cp ${CATALINA_BASE}/lib/servlet-api.jar HelloFilter.java
```

##	在 Tomcat 中使用 Filter

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                             http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0"
         metadata-complete="true">

	<filter>
		<filter-name>hello</filter-name>
		<filter-class>HelloFilter</filter-class>
	</filter>

	<filter-mapping>
		<filter-name>hello</filter-name>
		<url-pattern>/*</url-pattern>
	</filter-mapping>

	<servlet>
		<servlet-name>hello</servlet-name>
		<servlet-class>HelloWorld</servlet-class>
	</servlet>

	<servlet-mapping>
		<servlet-name>hello</servlet-name>
		<url-pattern>/hello</url-pattern>
	</servlet-mapping>

</web-app>
```
