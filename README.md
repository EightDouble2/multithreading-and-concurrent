# 多线程 multithreading

## 线程简介

### 程序、进程、线程

![img](https://github.com/EightDouble2/multithreading/blob/master/src/main/resources/img/001.png)

- 程序
  - 指令和数据的有序集合，其本身没有任何运行的含义，是一个静态的概念。
- 进程
  - 执行程序的一次执行过程，是一个动态的概念。是系统资源分配的单位。
- 线程
  - 通常在一个进程中可以有若干个线程，一个进程至少有一个线程，否则就没有存在的意义。线程是CPU调度和执行的单位。

> 很多多线程是模拟出来的，真正的多线程是指有多个CPU，即多核，如服务器。如果是模拟出来的多线程，即在一个CPU的情况下，在同一个时间点，CPU只能执行一个代码，因为CPU切换得很快，所以有同时执行的错觉。

### 概念

- 线程就是独立的执行路径。
- 在程序运行时，即使没有自己创建线程，后台也会有多个线程，如主线程，GC线程。
- `main()` 方法称之为主线程，为系统的入口，用于执行整个程序。
- 在一个进程中，如果开辟了多个线程，线程的运行由调度器安排调度，调度器是与操作系统紧密相关的，先后顺序是不能人为干预的。
- 对同一份资源操作时，会存在资源抢夺的的问题，需要加入并发控制。
- 线程会带来额外的开销，如CPU调度时间，并发控制开销。
- 每个线程在自己的工作内存交互，内存控制不当会造成数据不一致。 

## **线程实现**

### 继承Thread类

- 自定义线程类继承Thread类。
- 重写 `run()` 方法，编写线程执行体。
- 创建线程对象，调用 `start()` 方法启动线程。
- 不建议使用：OOP(封装、继承、多态)单继承局限性

### 实现Runnable接口

推荐使用实现Runnable接口，避免Java单继承局限性。

- 自定义线程类实现Runnable接口。
- 实现 `run()` 方法，编写线程执行体。
- 创建线程对象，传入实现类对象，调用 `start()` 方法启动线程。
- 建议使用：避免单继承局限性，方便同一个对象被多个线程使用。

### 实现Callable接口

- 实现Callable接口，需要返回值类型。
- 重写 `call()` 方法，需要抛出异常。
- 创建目标对象。
- 创建执行服务：`ExecutorService executorService = Executors.newFixedThreadPool(1);`
- 提交执行：`Future<Boolean> result1 = executorService.submit(t);`
- 获取结果：`boolean r1 = result1.get();`
- 关闭服务：`executorService.shutdownNow();`

### 静态代理

真实对象和代理对象都要实现同一个接口，代理对象要代理真实角色。

优点：
- 代理对象可以做很多真实对象做不了的事情。
- 真实对象专注做自己的事情

### Lambda表达式

为什么要使用Lambda表达式：
- 避免匿名内部类定义过多。
- 可以让代码看起来更简洁。
- 去掉没有意义的代码，只留下核心的逻辑。

函数式接口：
- 任何接口，如果只包含唯一一个抽象方法，那么它就是一个函数式接口。
- 对于函数式接口，我们可以通过Lambda表达式来创建该接口的对象。

## 线程状态

## **线程同步**

## 线程通信问题

## 高级主题