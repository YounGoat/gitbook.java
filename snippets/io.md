#	IO 片断

##	read file content to String object

```java
String path = "/path/to/file";
String content = new Scanner(new File(path)).useDelimiter("\\Z").next();
```

##	classLoader.getResource() vs. class.getResource()
