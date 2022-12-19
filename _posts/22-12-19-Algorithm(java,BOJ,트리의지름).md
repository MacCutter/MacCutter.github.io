---
layout: single
title:  "Algorithm BOJ 트리의지름 1167"
categories: algorithm
tag: [Java, algorithm, BOJ, 수학, 그래프, 탐색, DFS/BFS, 백준1167]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## 트리의지름
[https://www.acmicpc.net/problem/1167](https://www.acmicpc.net/problem/1167)

### 문제
![트리의지름](/assets/img/BOJ1167.jpg)

### 풀이
<li>그래프를 인접리스트안의 인접리스트에 저장, 별도의 노드클래스 생성(노드,가중치)를 표현</li>
<li>임의의 노드에서 BFS를 실행후 거리배열에 저장, 가장긴거리가 저장된 지점에서 다시 BFS실행</li>
<li>이후 최종 거리배열에서 오름차순으로 가장높은거리 출력</li>

### 코드구현
```java
import java.util.*;

public class Main {
    static boolean visited[];
    static int distance[];
    static ArrayList<Edge>[] A;

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int N = sc.nextInt();
        A = new ArrayList[N + 1];
        for (int i = 1; i <= N; i++) {  // 1번노드부터 있어서 1시작
            A[i] = new ArrayList<Edge>();
        }
        for (int i = 0; i < N; i++) {
            int S = sc.nextInt();
            while (true) {
                int E = sc.nextInt();
                if (E == -1)
                    break;
                int V = sc.nextInt();
                A[S].add(new Edge(E, V));
            }
        }
        distance = new int[N + 1];
        visited = new boolean[N + 1];
        BFS(1);
        int Max = 1;    // 아직 한게없으니 1이 최대
        for (int i = 2; i <= N; i++) {   // 1은 시작했으니 제외하고 2부터 N까지 distance값 max로 갱신(그다음 시작점)
            if (distance[Max] < distance[i])
                Max = i;
        }
        distance = new int[N + 1];
        visited = new boolean[N + 1];
        BFS(Max);   // 갱신된 새로운 시작점
        Arrays.sort(distance); // 오름차순으로 Max값을 후미로
        System.out.println(distance[N]);    // sort된 해당배열의 제일끝(N)번째는 제일 큰숫자
    }
    private static void BFS(int index) {
        Queue<Integer> queue = new LinkedList<Integer>();
        queue.add(index);
        visited[index] = true;
        while (!queue.isEmpty()) {
            int now_node = queue.poll();
            for (Edge i : A[now_node]) {
                int e = i.e;
                int v = i.value;
                if (!visited[e]) {
                    visited[e] = true;
                    queue.add(e);
                    distance[e] = distance[now_node] + v;   // 거리배열 업데이트
                }
            }
        }
    }
    static class Edge {
        int e;
        int value;
        public Edge(int e, int value) {
            this.e = e;
            this.value = value;
        }
    }
}
```
