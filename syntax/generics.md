#	Generics，泛型

```java
List<Integer> li = new ArrayList<Integer>();
li.put(new Integer(1));
Integer i = li.get(0);
```

在 JDK 1.7 或更新版本中，在可以推断实际类型的前提下，支持简略语法：
```java
List<Integer> li = new ArrayList<>();
```
因为 ```<>``` 形如钻石，故称为 *diamond operator*。

##	References
*	http://www.cnblogs.com/lwbqqyumidi/p/3837629.html
*	http://www.cnblogs.com/panjun-Donet/archive/2008/09/27/1300609.html
