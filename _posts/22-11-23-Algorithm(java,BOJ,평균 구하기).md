---
layout: single
title:  "Algorithm BOJ 평균 구하기 1546"
categories: algorithm
tag: [Java, algorithm, BOJ, 백준, 평균 구하기, 자료구조, 수학, 백준1546]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ (평균 구하기)

### 문제
  ![평균 구하기](/assets/img/BOJ1546.jpg)

### 풀이
<li>max점수와 sum누적점수를 저장해서 sum * 100 / max / 과목수(N) 를 코드로 구현</li>

### 슈도코드
<li>get value N</li>
<li>Array arr for N[i]</li>
<li>loop for(0 ~ N) score save</li>
<li>var for max</li>
<li>var for sum</li>
<li>loop for(0 ~ N) max, sum</li>
<li>print sum * 100 / max / N</li>

### 코드구현
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {

      Scanner sc = new Scanner(System.in);
      int N = sc.nextInt();
      int arr[] = new int[N];
      for (int i = 0; i < N; i++) {
          arr[i] = sc.nextInt();
      }
      sc.close();
      long sum = 0;
      long max = 0;
      for (int i = 0; i < N; i++) {
          sum += arr[i];
          if (arr[i] > max) max = arr[i];
      }
      System.out.println(sum * 100.0 / max / N);
    }
}
```
