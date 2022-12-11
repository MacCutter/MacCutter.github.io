---
layout: single
title:  "Algorithm BOJ 신기한소수찾기 2023"
categories: algorithm
tag: [Java, algorithm, BOJ, 수학, 소수판정, DFS/BFS, 백준2023]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ 신기한소수찾기
[https://www.acmicpc.net/problem/2023](https://www.acmicpc.net/problem/2023)

### 문제
![신기한소수찾기](/assets/img/BOJ2023.jpg)

### 풀이
<li>DFS로 4자리의 숫자가 되었을때 그숫자가 뒤에서부터 1개식 줄여서 각3자리, 2자리 ,1자리가 되었을때도 모두 소수인지 묻는 문제</li>
<li>DFS함수는 숫자를 한자리부터 넣고 자릿수(digit) 을 (depth)의 개념으로 봐서 한자리 늘릴때마다 소수인지 판단하여(1~4자리숫자중 한자리라도 소수가 아니면 탈락되기 때문에) 4자리까지 만들어가고 최종4자리숫자도 소수이면 출력</li>
<li>isPrime에서는 소수를 number의 루트가되는 숫자까지만 판별</li>

### 코드구현
```java
import java.util.Scanner;

public class Main {
    static int N;
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        N = sc.nextInt();   // N = 4
        DFS(2, 1);
        DFS(3, 1);
        DFS(5, 1);
        DFS(7, 1);
    }
    static void DFS(int number, int digits) {
        if (digits == N) {
            if (isPrime(number)) {
                System.out.println(number);
            }
            return;
        }
        for (int i = 1; i < 10; i++) {
            if (i % 2 == 0) {
                continue;
            }
            if (isPrime(number * 10 + i)) {
                DFS(number * 10 + i, digits + 1);
            }
        }
    }
    static boolean isPrime(int num) {
        for(int i=2; i*i<=num; i++)
            if(num % i == 0) return false;
        return true;
    }
}
```
