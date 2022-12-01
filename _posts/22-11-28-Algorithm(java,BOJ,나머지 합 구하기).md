---
layout: single
title:  "Algorithm BOJ 나머지 합 구하기 10986"
categories: algorithm
tag: [Java, algorithm, BOJ, 백준, 나머지 합 구하기, 수학, 누적의 합, 백준10986]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ (나머지 합 구하기)
[https://www.acmicpc.net/problem/10986](https://www.acmicpc.net/problem/10986)

### 문제
![나머지 합 구하기](/assets/img/BOJ10986.jpg)

### 풀이
<li>입력받은N값 으로 누적된 합배열 S 생성</li>
<li>S를 M값으로 나눈값으로 덮어씌우기</li>
<li>일단 S에서 0이나온answer 카운팅</li>
<li>덮어씌워진 합배열에서 같은 인덱스개수를 카운팅</li>
<li>answer에 0이 3개일때(3C2) 1이 2개일때(2C2)..합</li>

### 코드구현
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int N = sc.nextInt();
        int M = sc.nextInt();
        long[] S = new long[N];
        long[] C = new long[M];
        long answer = 0;

        S[0] = sc.nextInt();
        for (int i = 1; i < N; i++) {
            S[i] = S[i - 1] + sc.nextInt();
        }

        for (int i = 0; i < N; i++) {
            int remainder = (int) (S[i] % M);
            if (remainder == 0) answer++;
            C[remainder]++;
        }

        for (int i = 0; i < M; i++) {
            if (C[i] > 1) {
                answer = answer + (C[i] * (C[i] - 1) / 2);
            }
        }
        System.out.println(answer);
    }
}
```
