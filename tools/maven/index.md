#	Maven

>	to apply patterns to a project's build infrastructure in order to promote comprehension and productivity by providing a clear path in the use of best practices

作为构建工具，Maven 的受众不止于 Java 开发者；但是对于 Java 开发者而言，Maven 不止于构建工具，更是 Java 开发最佳实践的代名词。Maven 所总结的程序设计工程化模式，对于其他开发者也具有借鉴意义。

##	术语

*	*BOM*, Bill Of Materials
*	*Build Lifecycle*
*	*Build Phase*
*	*POM*, Project Object Model
*	*Profile*

##	编译生命周期

>	Maven is based around the central concept of a build lifecycle.  
>	@cite https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html

工件（Artifact）与编译生命周期（Build Lifecycle），一静一动，构成了 Maven 的两大核心概念。*default*, *clean*, *site* 是内建的三个生命周期。

>	Each of these build lifecycles is defined by a different list of build phases, wherein a build phase represents a stage in the lifecycle.  
>	@cite https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html

每个生命周期由若干阶段（phase）__有序__ 组成。例如，*default* 生命周期由以下阶段组成：

*	validate
*	compile
*	test
*	package
*	verify
*	install
*	deploy

##	目标与任务

>	A plugin goal represents a specific task (finer than a build phase) which contributes to the building and managing of a project. It may be bound to zero or more build phases. A goal not bound to any build phase could be executed outside of the build lifecycle by direct invocation. The order of execution depends on the order in which the goal(s) and the build phase(s) are invoked.   
>	@cite https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html

Maven 的实质是一个任务框架，生命周期和阶段定义了任务流模型，具体任务是由插件（plugin）完成。一个插件可以拥有一个或多个功能模块，相应地可以完成一个或多个目标（goal）。“目标”既可以被绑定到特定生命周期的特定阶段，当执行到该阶段时，被隐式地调用；也可以直接在命令中被显式地调用。

##	SEE

*	官方网站  
	http://maven.apache.org/

*	*Maven Getting Started Guide*  
	http://maven.apache.org/guides/getting-started/index.html

*	*Introduction to the Build Lifecycle*  
	https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html

*	*Lifecycle Reference*  
	https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html#Lifecycle_Reference
