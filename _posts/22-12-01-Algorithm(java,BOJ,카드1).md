---
layout: single
title:  "Algorithm BOJ 카드1 2161"
categories: algorithm
tag: [Java, algorithm, BOJ, 백준, 자료구조, 구현, 큐, 백준2161]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ 카드1
[https://www.acmicpc.net/problem/2161](https://www.acmicpc.net/problem/2161)

### 문제
![카드1](/assets/img/BOJ2161.jpg)

### 풀이
<li>N장의 카드를 받아 1번카드가 제일위에 N번카드가 제일 밑으로 간상태</li>
<li>1번카드를 버리고(출력) 2번카드가 N번카드의 밑으로 가고 반복</li>
<li>N개의카드만큼 버리게되서 N개의 카드를 출력하면 되는 문제</li>
<li>반복문으로 queue를 이용하여 front로 카드를 버리고 rear로 카드를 넣는방법</li>
<li>배열 result를 만들어 버리는카드를 하나씩 받아서 최종 출력</li>

### 코드구현
```java
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        Queue<Integer> queue = new LinkedList<>();
        int N = sc.nextInt();
        int[] result = new int[N];

        for (int i = 1; i <= N; i++) {
            queue.add(i);
        }

        for (int i = 0; i < N; i++) {
            result[i] = queue.poll();
            queue.add(queue.poll());
        }

        for (int i : result) {
            System.out.println(i);
        }
    }
}
```
