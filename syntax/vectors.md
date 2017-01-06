#	矢量数据

*java.util* 提供了数以百计的复杂数据对象，其中包含了常用的矢量对象。

```java
import java.util.Vector;
import java.util.Enumeration;

public class EnumerationTester {

   public static void main(String args[]) {
      Enumeration days;
      Vector dayNames = new Vector();

      dayNames.add("Sunday");
      dayNames.add("Monday");
      dayNames.add("Tuesday");
      dayNames.add("Wednesday");
      dayNames.add("Thursday");
      dayNames.add("Friday");
      dayNames.add("Saturday");
      days = dayNames.elements();

      while (days.hasMoreElements()) {
         System.out.println(days.nextElement());
      }
   }
}

// 代码引自 https://www.tutorialspoint.com/java/java_enumeration_interface.htm
```

##	See

*	*Java - Collections Framework*  
	https://www.tutorialspoint.com/java/java_collections.htm
