---
layout: post
title: java 并发编程基础 I
subtitle: 线程基础知识
keywords:   THREAD,JAVA
category:   Java
author:     "BINISM"
tags:		[java， multithread]
---

## 目录
{: .no_toc}

* 目录
{:toc}

## 使用线程的优势
1. 发挥多处理器强大能力
2. 建模的简单性
3. 简化异步事件：单线程服务器为避免线程阻塞，必须使用异步非阻塞的IO，使用复杂性高，并且易出错。使用多线程服务在一个线程受到阻塞时，不会影响到其他请求的处理。
4. ···

## 线程带来的风险
1. 安全性问题
  没有足够同步情况下，多个线程的执行顺序是不可预测的，会产生与预期不同的结果。

2. 活跃性问题
  串行程序中活跃性问题形式之一：无意中造成无限循环，循环之后的代码无法得到执行。多线程带来的其他问题：死锁、活锁、饥饿等等

3. 性能问题
   性能问题与活跃性问题密切相关，包含多个方面，如：服务时间过长、响应不灵敏、吞吐率过低、资源消耗高、可伸缩性较低等等。良好的并发程序设计能提高程序性能，但线程总会带来某种程度的运行时开销，比如：

   * 线程上下文切换：当线程调度器临时挂起活跃线程并转而运行另一个线程时，会频发地出现上下文切换（Context Switch）操作。这种操作会带来极大地开销：保存和回复上下文，丢失局部性，额外消耗CPU
   * 同步机制引起的开销：为保证线程安全性，在使用共享数据时，必须使用同步机制。 这些操作大多会抑制编译器对代码的优化，使缓存中的数据失效，增加共享内存总线同步流量。

## java语言中无处不在的线程

在java语言中，即使没有显式得创建线程，但在框架中仍然可能会创建线程，这些线程中调用的代码必须时线程安全的。

每个java程序都会使用到线程。当JVM启动时，它将JVM的内部任务（如，垃圾回收、终结操作等）创建后台线程，并创建一个主线程来运行main方法。java中的一些组件，都会创建线程池并调用这些线程中的方法。如果要使用这些功能就必须熟悉并发性和线程安全性。

> 框架通过在框架线程中调用应用程序代码将并发行引入到程序中。在代码中将不可避免地访问应用程序状态，因此所有访问这些状态的代码路径必须是线程安全的。

下面的程序均会在应用程序之外的线程中调用应用程序的代码：

* Timer

  Timer类的作用是使任务在稍后的时刻一次或周期性的进行。这些TimerTask将在Timer管理的线程中执行。若某个TimerTask访问了应用程序中其他线程访问的数据，那么TimerTask和其他类都需要以线程安全的方式访问数据。最简单的方法是确保TimeTask访问的对象本身是线程安全的，从而把线程安全性封装到共享对象的内部。

* Servlet和JSP

  每个Servlet都表示一个程序逻辑组件，在高吞吐率的网站中，多个客户端可能会同时请求同一个Servlet服务。在Servlet规范中，Servlet同样需要满足被多个线程同时调用（servlet必须是线程安全的）。Servlet和JSP，以及ServletContext和httpsession等容器中保存的Servlet过滤器和对象等，都必须是线程安全的。

* 远程方法调用（RMI）

  在远程调用过程中，远程对象将在一个由RMI管理的线程中调用。一个远程对象可能会被多个RMI线程同时调用。远程对象需注意两个线程安全性问题：正确协同在多个对象中共享的状态，以及对远程对象本身状态的访问。

* Swing和AWT

  GUI应用程序的一个固有属性是异步性。用户在任意时刻点击一个按钮，应用程序就会及时响应，即使应用程序正在进行别的任务。Swing和AWT通过创建单独的线程（事件处理器）来处理用户触发的事件。若事件处理器需要访问其他线程同时访问的应用程序状态，那么这个事件处理器和访问这个状态的其他代码，都必须通过线程安全的方式来访问此状态。

## 线程安全性

编写线程安全代码，核心在于要对状态的访问操作进行管理，特别是对 **共享的（Share）** 和 **可变的（Mutable）** 状态的访问。

**共享的（Share）** 意味着变量可以被多个线程访问。

**可变的（Mutable）** 意味着变量值在其生命周期内可以发生变化。

对象的线程安全性的需求是由它是否被多个线程同时访问决定的。当多个线程访问某个状态变量，并且有任意一个线程执行写入操作时，必须采用同步机制协同这些线程对变量的访问。

Java中的主要同步机制是关键字 `synchronized`，它提供一种独占的加锁方式。其他“同步”术语还包括`volatile`类型变量，显示锁（Explicit Lock）和原子变量。

> 修复 由于没有以合适的同步方式访问可变状态变量造成的错误 有以下三种方式：
* 不在线程间共享该状态的变量。
* 将状态变量修改为不可变的变量。
* 在访问状态变量时使用同步。

### 线程安全性定义

当多个线程访问某个类时，不管运行时采用何种调度方式或者这些线程将如何交替执行，并且在主调代码中不需要任何额外的同步和协同，这个类都能表现出正确的行为，那么就称这个类是线程安全的。

> 线程安全类中封装了必要的同步机制，因此客户端无须进一采取同步措施。

> 无状态的对象一定是线程安全的。
例：无状态的Servlet。不包含任何域、也不包含任何对其他类中域的引用，计算过程中的临时状态仅存在线程栈上的局部变量中，并且只能由正在执行的线程访问。

```java
@ThreadSafe
public class StatelessFactorizer implements Servlet {
  public void service(ServletRequest req, ServletResponse resp) {
    BigInteger i = extractFromRequest(req);
     BigInteger[] factors = factor(i);
      encodeIntoResponse(resp, factors);
  }
}
```

## 原子性

### 竟态条件
当某个计算的正确性取决于多个线程交替执行的顺序时，就会发生竟态条件。最常见的竟态条件的类型就是“先检查后执行（Check-Then-Ack）”，即可能通过一个失效的观测结果来决定下一步动作。

### 复合和原子操作

> 假定有两个操作A和B,若从执行A的线程来看，当另一个线程执行B时，要么将B执行完，要么完全不执行B，那么A和B对彼此来说是原子的。

为了保证线程安全性，“先检查后执行”和“读取-修改-写入”等操作必须是原子的。我们将“先检查后执行”和“读取-修改-写入”等操作统称为复合操作：包含了一组必须以原子方式执行的操作才能保证线程的安全性。

## 加锁机制

程序中的可变状态有时是互相关联的，要保持状态的一致性，就必须在单个原子操作中更新所有相关的状态变量。

```java
@NotThreadSafe
public class UnsafeCachingFactorizer implements Servlet {
   private final AtomicReference<BigInteger> lastNumber = new AtomicReference<BigInteger>();
    private final AtomicReference<BigInteger[]> lastFactors = new AtomicReference<BigInteger[]>();
    public void service(ServletRequest req, ServletResponse resp) {
       BigInteger i = extractFromRequest(req);
        if (i.equals(lastNumber.get()))
           encodeIntoResponse(resp, lastFactors.get());
        else {
          BigInteger[] factors = factor(i);
          lastNumber.set(i); lastFactors.set(factors);
          encodeIntoResponse(resp, factors);
         }
    }
}
```


### 内置锁

java提供一种内置锁机制来支持原子性：同步代码块。

```java
synchronized (lock) { // Access or modify shared state guarded by lock }
```

java内置锁相当于一种互斥体，最多有一个线程能持有这种锁。

### 重入

当一个线程请求其他线程持有的锁时，发出的请求会被阻塞。锁的重入性指 某个线程试图获得一个已经由它自己持有的锁时，这个请求就会成功。“重入”意味着获取锁的粒度是“线程”而不是调用。

如果内置锁不是重入的，那么下面的代码将会发生死锁：
```java
public class Widget {
  public synchronized void doSomething() { ... }}
  public class LoggingWidget extends Widget {
  public synchronized void doSomething() {
      System.out.println(toString() + ": calling doSomething");
       super.doSomething();
  }
}
```

### 用锁来保护状态

> 对于可以由多个线程访问的每个可变状态变量，必须在保持相同锁的情况下执行对该变量的所有访问。在这种情况下，我们说变量由该锁保护。

> 每个共享的可变变量都应该由一个锁来保护。从而向维护人员说明锁是哪一个。

> 对于每个涉及多个变量的不变性条件，该不变性条件中涉及的所有变量都必须由同一个锁保护。

### 锁的活跃性与性能

> 简单性和性能之间经常存在相互制约的关系。在实施同步策略时，要抵制为了性能而盲目地牺牲简单性（可能破坏安全性）。

> 避免在长时间的计算或操作中持有锁，否则可能无法快速完成，如网络或控制台I/O。
