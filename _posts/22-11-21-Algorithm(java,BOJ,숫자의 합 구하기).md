---
layout: single
title:  "Algorithm BOJ 숫자의 합 구하기 11720"
categories: algorithm
tag: [Java, algorithm, BOJ, 백준, 숫자의 합, 자료구조, 수학, 문자열, 백준11720]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ (숫자의 합 구하기)
(https://www.acmicpc.net/problem/11720)

### 문제
  ![숫자의 합 구하기](/assets/img/BOJ11720.jpg)

### 슈도코드
<li>get value N</li>
<li>길이N의 숫자 String sNum에 입력받기</li>
<li>make var for sum</li>
<li>loop for (0 ~ N)</li>
<li>sNum의 각자리를 정수형으로 변환하며 sum에 누적</li>
<li>print sum</li>

### 코드구현
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        int N = sc.nextInt();
        String sNum = sc.next();
        sc.close();
        int sum = 0;
        for (int i = 0; i < N; i++) {
            sum += sNum.charAt(i) - '0';
        }
        System.out.println(sum);
    }
}
```
