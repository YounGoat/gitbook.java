#	线程与多线程

##	通过实现 Runnable 接口创建线程

```java
// （1）实现 Runnable 接口。
class RunnableDemo implements Runnable {
    private Thread t;
    private String threadName;

    RunnableDemo(String name) {
        threadName = name;
        System.out.println("Creating " + threadName);
    }

	// （2）实现 Runnable 接口所要求的 run() 方法。
	// 线程的业务逻辑将在此方法中执行。
    public void run() {
        System.out.println("Running " + threadName);
        try {
            for (int i = 4; i > 0; i--) {
                System.out.println("Thread: " + threadName + ", " + i);
                // Let the thread sleep for a while.
                Thread.sleep(50);
            }
        } catch (InterruptedException e) {
            System.out.println("Thread " + threadName + " interrupted.");
        }
        System.out.println("Thread " + threadName + " exiting.");
    }

    public void start() {
        System.out.println("Starting " + threadName);
        if (t == null) {
			// （3）将 Runnable 实例装入线程，创建线程实例，
            t = new Thread(this, threadName);
			// （4）启动线程。
            t.start();
        }
    }
}

public class TestThread {
    public static void main(String args[]) {
		RunnableDemo R1 = new RunnableDemo("Thread-1");
        R1.start();

        RunnableDemo R2 = new RunnableDemo("Thread-2");
        R2.start();
    }
}

// 代码引自 https://www.tutorialspoint.com/java/java_multithreading.htm
```

##	通过继承 Thread 类创建线程

```java
// （1）继承 Thread 类。
class ThreadDemo extends Thread {
    private String threadName;

    ThreadDemo(String name) {
        threadName = name;
        System.out.println("Creating " + threadName);
    }

    // （2）覆盖父类的 run() 方法。
    // 线程的业务逻辑将在此方法中执行。
    public void run() {
        System.out.println("Running " + threadName);
        try {
            for (int i = 4; i > 0; i--) {
                System.out.println("Thread: " + threadName + ", " + i);
                // Let the thread sleep for a while.
                Thread.sleep(50);
            }
        } catch (InterruptedException e) {
            System.out.println("Thread " + threadName + " interrupted.");
        }
        System.out.println("Thread " + threadName + " exiting.");
    }
}

public class MT {
    public static void main(String args[]) {
        ThreadDemo T1 = new ThreadDemo("Thread-1");
		// （3）启动线程，run() 将在线程中被执行。
        T1.start();

        ThreadDemo T2 = new ThreadDemo("Thread-2");
        T2.start();
    }
}
```
