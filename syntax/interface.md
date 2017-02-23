#	接口

##	接口可以实例化吗？

接口可以视为特殊的抽象类，当然不可以实例化。但是我们可以简化接口的实现和实例化。

```java
// 类的定义
interface Ball {
    public abstract float Diameter();
}
```

传统上，我们是这样实现接口的：

```java
class Football implements Ball {
	public float Diameter() {
		return 69;
	}
}

Ball football = new Football();
System.out.println(football.Diameter());
```

我们也可以这样来简化其实现过程：

```java
Ball football = new Ball() {
	public float Diameter() {
		return 69;
	}
};
```

对于函数式接口（本例中接口 Ball 只声明了一个抽象函数，所以它就是一个函数式接口），还可以进一步简化：

```java
Ball football = () -> 69;
```

##	函数式接口

##	SEE

*	*Difference between final and effectively final*  
	http://stackoverflow.com/questions/20938095/difference-between-final-and-effectively-final
