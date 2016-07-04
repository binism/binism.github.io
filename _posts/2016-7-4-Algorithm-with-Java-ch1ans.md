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

# Fundamentals

## Basic Programming Model

1. Give the value of each of the following expressions

   a.  ( 0 + 15 ) / 2

   b.  2.0e-6 * 100000000.1

   c.   true && false \|\| true && true

   ans:
   a. 7   b. 200.0000002 c. true;

2. Give the type and value of each of the following expressions:

   a.  (1 + 2.236)/2

   b.  1 + 2 + 3 + 4.0

   c.  4.1 >= 4

   d.  1 + 2 + "3"

   ans:
   a. double 1.618
   b. double 10.0
   c. boolean true
   d. string "33"

3. Write a program that takes three integer command-line arguments and prints equalif all three are equal, and not equalotherwise.
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

4. What (if anything) is wrong with each of the following statements?

    a.   if (a > b) then c = 0;

    b.   if a > b { c = 0; }

    c.   if (a > b) c = 0;

    d.   if (a > b) c = 0 else b = 0;

    ans:

    a. delete then;
    b. (a>b);
    c. right;
    d. right;

5. Write a code fragment that prints true if the double variables x and y are both strictly between 0 and 1and false otherwise.

   ans:
```java
   if( x > 0 && x <　1 && y > 0 && y <　1)
     System.out.println("true");
   else
     System.out.print("false");
```

6. What does the following program print?

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

7.  Give the value printed by each of the following code fragments:

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

8. What do each of the following print?

   a.  System.out.println('b');

   b.  System.out.println('b' + 'c');

   c.  System.out.println((char) ('a' + 4));

 Explain each outcome.

  ans:
  a. b
  b. 197
  c. e

9. Write a code fragment that puts the binary representation of a positive integer N into a String s.

  ans:Java has a built-in method Integer.toBinaryString(N)for this job, but the point of the exercise is to see how such a method might be implemented. Here is a particularly concise solution:
```java
  String s = "";
  for (int n = N; n > 0; n /= 2)
    s = (n % 2) + s;
```

10. What is wrong with the following code fragment?
```java
   int[] a;
   for (int i = 0; i < 10; i++)
      a[i] = i * i;
```

    ans:  It  does  not  allocate  memory  for a[] with new.  This  code  results  in  a variable a might not have been initialized compile-time error.

11. Write a code fragment that prints the contents of a two-dimensional boolean array, using \* to represent trueand a space to represent false. Include row and column numbers.

   ans:~

12. **What does the following code fragment print?**
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

13. Write a code fragment to print the     transposition(rows and columns changed) of a two-dimensional array with M rows and N columns.

   ans:
```java
   for(int i = 0; i < N; i++) {
      for(int j = 0; j < M; j++)
        System.out.print(A[j][i]);
      System.out.print("\n");
    }
```

14. Write a static method lg()that takes an int value N as argument and returns the largest int not larger than the base-2 logarithm of N. Do notuse Math.

   ans:
```java
   if(N == 0)
      exit(-1);
   int i = 1,ans = 0;
   while(i < N){
     i >> 1;
     ans++;
   }
   return ans-1;
```

15. Write a static methodhistogram()that takes an array a[] of intvalues and an integer M as arguments and returns an array of length M whose ith entry is the number of times the integer iappeared in the argument array. If the values in a[] are all between 0 and M–1,  the  sum  of  the  values  in  the  returned  array  should  be  equal  to a.length.
