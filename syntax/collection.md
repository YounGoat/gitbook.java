#	The Java Collections Framework

集合（Collection）处理是常规编程中一个看似简单，实则颇有深意的问题，对于强类型语言来说尤其如此。因此才有了“集合框架（Collections Framework）”，试图用一个统一的模型或者模式来处理与集合有关的问题。一个集合框架包含至少三个方面：
*	接口（interface）
*	实现（implementation）
*	算法（algorithm）

##	核心接口

*	*Collection*  
*	*Set* extends Collection  
	不支持重复元素。
*	*SortedSet* extends Set
*	*List* extends Collection  
	有序集合，也称为序列（Sequence）。
*	*Queue* extends Collection  
	单向队列。
*	*Deque* extends Collection  
	双向队列。
*	*Map*  
	映射。
*	*SortedMap* extends Map

所有的核心集合接口都支持泛型（generic）。

##	重要实现

*	*ArrayList* implements List
*	*HashMap* extends AbstractMap implements Map
* 	*HashTable* extends Dictionary implements Map

##	集合的遍历

本节中将介绍几种不同的集合遍历（Traverse）方法。为此，我们准备了一个简单的集合对象：
```java
ArrayList<String> al = new ArrayList<>();
al.add("One");
al.add("Two");
al.add("Three");
al.add("Four");
al.add("Five");
```

###	 Aggregrate Operations

自 Java 1.8 版本起，支持聚合操作：

```java
al.stream()
		.filter(e -> e.length() <= 3)
		.forEach(e -> System.out.println(e));
```

聚合操作还支持多线程并行：

```java
al.parallelStream()
		.forEach(e -> System.out.println(e));
```

其他典型聚合方法：

```java
al.stream().collect(Collectors.joining(", "));
```

###	for-each, for Construct

```java
for (String e : al) {
	System.out.println(e);
}
```

或者，
```java
for (int i = 0; i < al.size(); i++) {
	System.out.println(al.get(i));
}
```

###	Iterators

```java
for (Iterator<String> it = al.iterator(); it.hasNext(); ) {
	String s = it.next();
	System.out.println(s);
}
```

##	集合的批量操作

除了遍历，集合还支持批量操作（Bulk Operation），比如：
```java
al.removeAll(Collections.singleton(null));
```

##	集合与数组

```java
Object[] ao = al.toArray();

// 转换为数组时，如果提供了预制容器，则会按照容器的规格（类型）生成新的数组。
// 同时，toArray() 将会依次填充（覆盖）预制容器，填满为止。
String[] as0 = new String[0];
String[] as1 = al.toArray(as0);
```

##	SEE

*	*The Java™ Tutorials，Trail: Collections*  
	http://docs.oracle.com/javase/tutorial/collections/index.html

##	REL

*	STL, C++ Standard Template Library
*	Smalltalk's collection hierarchy
