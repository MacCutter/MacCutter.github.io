---
layout: single
title:  "Algorithm BOJ 절댓값힙 11286"
categories: algorithm
tag: [Java, algorithm, BOJ, 백준, 자료구조, 우선순위큐, 백준11286]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ 절댓값힙
[https://www.acmicpc.net/problem/11286](https://www.acmicpc.net/problem/11286)

### 문제
![절댓값힙](/assets/img/BOJ11286.jpg)

### 풀이
<li>입력값이 0일때 큐가 비어있으면 0출력 아닐땐 절대값이 최소인수로 출력</li>
<li>절대값도 같다면 작은수(음수)로 출력</li>
<li>입력값이 0이 아닐때 우선순위 큐에가서 자동정렬</li>

### 코드구현
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.PriorityQueue;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());
        PriorityQueue<Integer> pq = new PriorityQueue<>((o1, o2) -> {
            int first_abs = Math.abs(o1);
            int second_abs = Math.abs(o2);
            if (first_abs == second_abs)
                return o1 > o2 ? 1 : -1;
            else
                return first_abs - second_abs;
        });
        for (int i = 0; i < N; i++) {
            int request = Integer.parseInt(br.readLine());
            if (request == 0) {
                if (pq.isEmpty())
                    System.out.println("0");
                else
                    System.out.println(pq.poll());
            } else
                pq.add(request);
        }
    }
}
```
