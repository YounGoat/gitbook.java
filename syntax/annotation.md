#	Annotation，注解或元注释

*Annotation* 的本意即注释，更精确一点，是指与正文关联紧密的边注或旁注。在 Java 的语境中，用来指代一种特殊的、用于修饰上下文代码的注释，我们称其为__注解__或__元注释__。与普通的注释不同，Annotation 虽然不是代码，但事实上影响程序的运行逻辑，其用途包含但不限于：

>	*	*Information for the compiler* — Annotations can be used by the compiler to detect errors or suppress warnings.
>	*	*Compile-time and deployment-time processing* — Software tools can process annotation information to generate code, XML files, and so forth.
>	*	*Runtime processing* — Some annotations are available to be examined at runtime.

@cite "http://docs.oracle.com/javase/tutorial/java/annotations/"

自 [Java 5](http://java.sun.com/j2se/1.5.0/docs/guide/language/annotations.html) 开始，允许开发人员定义自己的 annotation。

##	Annotation vs. Doc Tag

__元注释与注释中的标签（tag）是两回事__，虽然它们之前可能存在某种联系，比如：
```java
// Javadoc comment follows
/**
 * @deprecated
 * explanation of why it was deprecated
 */
@Deprecated
static void deprecatedMethod() { }
```
@cite http://docs.oracle.com/javase/tutorial/java/annotations/predefined.html

##	DEMO

```java
import java.lang.annotation.Documented;

@Documented
@interface ClassPreamble {
    String author();
    String date();
    int currentRevision() default 1;
    String lastModified() default "N/A";
    String lastModifiedBy() default "N/A";
    // Note use of array
    String[] reviewers();
}

@ClassPreamble (
        author = "John Doe",
        date = "3/17/2002",
        currentRevision = 6,
        lastModified = "4/12/2004",
        lastModifiedBy = "Jane Doe",
        // Note array notation
        reviewers = {"Alice", "Bob", "Cindy"}
)
public class AnnotationTest {
}
```
@cite http://docs.oracle.com/javase/tutorial/java/annotations/declaring.html

##	Java SE 预定义元注释
@cite http://docs.oracle.com/javase/tutorial/java/annotations/predefined.html

*	*@Deprecated*
	>	@Deprecated annotation indicates that the marked element is deprecated and should no longer be used. The compiler generates a warning whenever a program uses a method, class, or field with the @Deprecated annotation.

*	*@Override*
	>	While it is not required to use this annotation when overriding a method, it helps to prevent errors. If a method marked with @Override fails to correctly override a method in one of its superclasses, the compiler generates an error.

*	*@SuppressWarnings*
	>	@SuppressWarnings annotation tells the compiler to suppress specific warnings that it would otherwise generate.

##	SEE

*	*The Java™ Tutorials, Lesson: Annotations*  
	http://docs.oracle.com/javase/tutorial/java/annotations/index.html

*	*Java 8 Annotation 新特性在软件质量和开发效率方面的提升*  
	http://www.ibm.com/developerworks/cn/java/j-lo-java8annotation/index.html
