---
layout: single
title:  "Algorithm BOJ ABCDE(친구관계) 13023"
categories: algorithm
tag: [Java, algorithm, BOJ, 수학, 그래프, 탐색, DFS/BFS, 백준13023]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ ABCDE(친구관계)
[https://www.acmicpc.net/problem/13023](https://www.acmicpc.net/problem/13023)

### 문제
![ABCDE(친구관계)](/assets/img/BOJ13023.jpg)

### 풀이
<li>그래프 데이터를 인접리스트에 저장</li>
<li>모든노드 DFS를 수행하여 깊이가 5이상(ABCDE=5명) 이상이면 1, 아니면 0 출력</li>

### 코드구현
```java
import java.util.*;

public class Main {
    static ArrayList<Integer> A[];
    static boolean visited[];
    static boolean arrive;

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int N = sc.nextInt();
        int M = sc.nextInt();
        A = new ArrayList[N];
        visited = new boolean[N];
        arrive = false;

        for (int i = 0; i < N; i++) {
            A[i] = new ArrayList<Integer>();
        }
        for (int i = 0; i < M; i++) {
            int S = sc.nextInt();
            int E = sc.nextInt();
            A[S].add(E);
            A[E].add(S);
        }
        for (int i = 0; i < N; i++) {
            DFS(i,1);   // (i, 1) = 0부터 돌면서 깊이는 1로 시작
            if (arrive)
                break;
        }
        if (arrive)
            System.out.println(1);
        else
            System.out.println(0);

    }
    public static void DFS(int now, int depth) {
        if (depth == 5 || arrive) {
            arrive = true;
            return;
        }
        visited[now] = true;
        for (int i : A[now]) {
            if (!visited[i]) {
                DFS(i, depth + 1);
            }
        }
        visited[now] = false;
    }
}
```
