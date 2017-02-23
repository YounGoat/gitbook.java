#	枚举

*enum* 是 Java 5 开始支持的关键字，它带来了一个新的数据类型：枚举型。Java 中的枚举型数据——与我最初设想的不同——并非具名的整型数值，而是货真价实的对象。除了开头的数值枚举部分，枚举型的声明过程与类定义无异，而事实上，所有的枚举型也确实是 *java.lang.Enum* 的子类。

##	DEMO

简单的枚举型示例：
```java
public enum Day {
    SUNDAY, MONDAY, TUESDAY, WEDNESDAY,
    THURSDAY, FRIDAY, SATURDAY
}
// @cite http://docs.oracle.com/javase/tutorial/java/javaOO/enum.html
```

较复杂的枚举型示例：
```java
public enum Planet {
    MERCURY (3.303e+23, 2.4397e6),
    VENUS   (4.869e+24, 6.0518e6),
    EARTH   (5.976e+24, 6.37814e6),
    MARS    (6.421e+23, 3.3972e6),
    JUPITER (1.9e+27,   7.1492e7),
    SATURN  (5.688e+26, 6.0268e7),
    URANUS  (8.686e+25, 2.5559e7),
    NEPTUNE (1.024e+26, 2.4746e7);

    private final double mass;   // in kilograms
    private final double radius; // in meters
    Planet(double mass, double radius) {
        this.mass = mass;
        this.radius = radius;
    }
    private double mass() { return mass; }
    private double radius() { return radius; }

    // universal gravitational constant  (m3 kg-1 s-2)
    public static final double G = 6.67300E-11;

    double surfaceGravity() {
        return G * mass / (radius * radius);
    }
    double surfaceWeight(double otherMass) {
        return otherMass * surfaceGravity();
    }
}
// @cite http://docs.oracle.com/javase/tutorial/java/javaOO/enum.html
```

##	enum vs. Enumeration

*enum* 是一个数据类型，本质上是一个类；而 *[Enumeration](http://docs.oracle.com/javase/7/docs/api/java/util/Enumeration.html)* 是一个接口。

##	REF

*	*The Java™ Tutorials: Enum Types*  
	http://docs.oracle.com/javase/tutorial/java/javaOO/enum.html
