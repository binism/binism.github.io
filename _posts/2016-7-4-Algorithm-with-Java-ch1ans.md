---
layout:    post
title:     【Algorithm】 ch1.1 Answers
keywords:  Algorithm,Java
category:  Algorithm
tags:      [Algorithm,Answers]
mathjax:   true
date:      2016-07-04
author:     "BINISM"
---

---

## 目录
{: .no_toc}

* 目录
{:toc}

---



## Fundamentals - Basic Programming Model

### 1. Give the value of each of the following expressions

   a.  ( 0 + 15 ) / 2

   b.  2.0e-6 * 100000000.1

   c.   true && false \|\| true && true

   ans:
   a. 7   b. 200.0000002 c. true;

### 2. Give the type and value of each of the following expressions:

   a.  (1 + 2.236)/2

   b.  1 + 2 + 3 + 4.0

   c.  4.1 >= 4

   d.  1 + 2 + "3"

   ans:
   a. double 1.618
   b. double 10.0
   c. boolean true
   d. string "33"

### 3. Write a program that takes three integer command-line arguments and prints equalif all three are equal, and not equalotherwise.
   ans:

```java
   public static void main(String[] args) {
        int arg1 = Integer.parseInt(args[0]);
        int arg2 = Integer.parseInt(args[1]);
        int arg3 = Integer.parseInt(args[2]);
        if( arg1 == arg2 && arg2 == arg3)
            System.out.println("equel");
        else
            System.out.println("not equel");
        return;
    }
```

#### 4. What (if anything) is wrong with each of the following statements?

a.   if (a > b) then c = 0;

b.   if a > b { c = 0; }

c.   if (a > b) c = 0;

d.   if (a > b) c = 0 else b = 0;

ans:
    a. delete then;
    b:b. (a>b);
    c. right;
    d. right;

### 5. Write a code fragment that prints true if the double variables x and y are both strictly between 0 and 1and false otherwise.

ans:

```java
   if( x > 0 && x <　1 && y > 0 && y <　1)
     System.out.println("true");
   else
     System.out.print("false");
```

### 6. What does the following program print?

```java
  int f = 0;
  int g = 1;
  for (int i = 0; i <= 15; i++)
  {
    StdOut.println(f);
    f = f + g;
    g = f - g;
  }
```

  ans：0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610

### 7.  Give the value printed by each of the following code fragments:

a.

```java
  double t = 9.0;
  while (Math.abs(t - 9.0/t) > .001)
      t = (9.0/t + t) / 2.0;
  StdOut.printf("%.5f\n", t);
```

b.

```java
  int sum = 0;
  for (int i = 1; i < 1000; i++)
      for (int j = 0; j < i; j++)
          sum++;
  StdOut.println(sum);

```

c.

```java
  int sum = 0;
  for (int i = 1; i < 1000; i *= 2)
      for (int j = 0; j < 1000; j++)
          sum++;
  StdOut.println(sum);
```

  ans:
  a. 3.00009
  b. 499500
  c. 10000

### 8. What do each of the following print?

   a.  System.out.println('b');

   b.  System.out.println('b' + 'c');

   c.  System.out.println((char) ('a' + 4));

 Explain each outcome.

  ans:
  a. b
  b. 197
  c. e

### 9. Write a code fragment that puts the binary representation of a positive integer N into a String s.

  ans:Java has a built-in method Integer.toBinaryString(N)for this job, but the point of the exercise is to see how such a method might be implemented. Here is a particularly concise solution:

```java
  String s = "";
  for (int n = N; n > 0; n /= 2)
    s = (n % 2) + s;
```

### 10. What is wrong with the following code fragment?

```java
   int[] a;
   for (int i = 0; i < 10; i++)
      a[i] = i * i;
```

ans:  It  does  not  allocate  memory  for a[] with new.  This  code  results  in  a variable a might not have been initialized compile-time error.

### 11. Write a code fragment that prints the contents of a two-dimensional boolean array, using \* to represent trueand a space to represent false. Include row and column numbers.

   ans:~

### 12. **What does the following code fragment print?**

```java
   int[] a = new int[10];
   for (int i = 0; i < 10; i++)
      a[i] = 9 - i;
   for (int i = 0; i < 10; i++)
      a[i] = a[a[i]];
   for (int i = 0; i < 10; i++)
      System.out.println(a[i]);
```

   ans: 0 1 2 3 4 4 3 2 1 0 (not 0 1 2 3 4 5 6 7 8 9)

### 13. Write a code fragment to print the     transposition(rows and columns changed) of a two-dimensional array with M rows and N columns.

   ans:

```java
   for(int i = 0; i < N; i++) {
      for(int j = 0; j < M; j++)
        System.out.print(A[j][i]);
      System.out.print("\n");
    }
```

### 14. Write a static method lg()that takes an int value N as argument and returns the largest int not larger than the base-2 logarithm of N. Do notuse Math.

ans:

```java
   if(N == 0)
      exit(-1);
   int i = 1,ans = 0;
   while(i < N){
    i =  i * 2;
     ans++;
   }
   return ans-1;
```

### 15. Write a static method histogram() that takes an array a[] of int values and an integer M as arguments and returns an array of length M whose ith entry is the number of times the integer i appeared in the argument array. If the values in a[] are all between 0 and M–1,  the  sum  of  the  values  in  the  returned  array  should  be  equal  to a.length.

ans:

```java
public static int [] histogram(int [] A, int N) {
        int []ans = new int[N];
        for(int i = 0; i < A.length; i++){
            int  index= A[i];
            if(index < N && index >= 0)
                ans[index] ++;
        }
        return ans;
    };
```

### 16. Give the value of exR1(6):

```java
public static String exR1(int n)
{
  if (n <= 0) return "";
  return exR1(n-3) + n + exR1(n-2) + n;
}
```
ans: 311361142246

### 17. Criticize the following recursive function:

```java
public static String exR2(int n)
{
  String s = exR2(n-3) + n + exR2(n-2) + n;
  if (n <= 0) return "";
  return s;
}
```

ans:The base case will never be reached. A call to exR2(3) will result in calls to exR2(0), exR2(-3), exR3(-6), and so forth until a Stack Overflow Error occurs.

### 18. Consider the following recursive function:

```java
public static int mystery(int a, int b)
{
  if (b == 0) return 0;
  if (b % 2 == 0) return mystery(a+a, b/2);
  return mystery(a+a, b/2) + a;
}
```

What are the values of mystery(2, 25)and mystery(3, 11)? Given positive integers
aand b, describe what value mystery(a, b)computes. Answer the same question, but replace the three + operators with * and replace return 0 with return 1.

ans: mystery(2, 25) = 50,  mystery(3, 11)= 33;  33554432, 177147;

### 19. Run the following program on your computer:

```java
public class Fibonacci {
    public static long F(int N) {
        if (N == 0) return 0;
        if (N == 1) return 1;
        return F(N-1) + F(N-2);
}
public static void main(String[] args)
{
    for (int N = 0; N < 100; N++)
        StdOut.println(N + " " + F(N));
}
```

What is the largest value of N for which this program takes less than 1 hour to compute the value of F(N)? Develop a better implementation of F(N)that saves computed values in an array.


ans:

```java
public class Fibonacci{

    public static long F(int N){
        if (N == 0) return 0;
        if (N == 1) return 1;

        long[] f = new long[N+1];
        f[0] = 0;
        f[1] = 1;

        for (int i = 2; i <= N; i++{
            f[i] = f[i-1] + f[i-2];

        }
        return f[N];
    }

    public static void main(String[] args)
    {
        for (int N = 0; N < 100; N++)
            StdOut.println(N + " " + F(N));
    }
}
```

### 20.Write a recursive static method that computes the value of ln (N !).

ans:

```Java
public class Calln {

    private static double lnPro(int N){
        if (N == 1) return 0;
        if (N == 2) return 1;

        return Math.log(N) + lnPro(N-1);
    }
    public static void main(String[] args){
        int N = Integer.parseInt(args[0]);
        double value = lnPro(N);
        StdOut.print(value);
    }
}
```
