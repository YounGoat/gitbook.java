#	序列化和反序列化

作为对象可序列化的前提，其所属类须满足以下要求：
```java
// 实现 java.io.Serializable 接口。
public class Employee implements java.io.Serializable {
	// 所有属性均可序列化。
	public String name;
	public String address;
	public transient int SSN; // 若属性不可序列化，则必须用 transient 修饰。
	public int number;

	public void mailCheck() {
		System.out.println("Mailing a check to " + name + " " + address);
	}
}

// 代码引自 https://www.tutorialspoint.com/java/java_serialization.htm
```
