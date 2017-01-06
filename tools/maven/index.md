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

>	Maven is based around the central concept of a build lifecycle
>	https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html

工件（Artifact）与编译生命周期（Build Lifecycle），一静一动，构成了 Maven 的两大核心概念。*default*, *clean*, *site* 是内建的三个生命周期。

>	Each of these build lifecycles is defined by a different list of build phases, wherein a build phase represents a stage in the lifecycle.
>	https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html

每个生命周期由若干阶段（Stage）__有序__组成。

##	在线资源

*	官方网站  
	http://maven.apache.org/

*	*Maven Getting Started Guide*  
	http://maven.apache.org/guides/getting-started/index.html

*	*Introduction to the Build Lifecycle*  
	https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html

*	*Lifecycle Reference*  
	https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html#Lifecycle_Reference
