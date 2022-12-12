---
layout: single
title:  "Algorithm BOJ DFS와BFS 1260"
categories: algorithm
tag: [Java, algorithm, BOJ, 수학, 그래프, 탐색, DFS/BFS, 백준1260]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ DFS와BFS
[https://www.acmicpc.net/problem/1260](https://www.acmicpc.net/problem/1260)

### 문제
![DFS와BFS](/assets/img/BOJ1260.jpg)

### 풀이
<li>그래프 데이터를 인접리스트에 저장</li>
<li>양방향노드 이기떄문에 인접리스트에 양방 삽입</li>
<li>문제에 같은노드면 작은숫자 조건충족을위해 오름차순 정렬</li>
<li>정렬시 0에는 null이 있으므로 1부터시작</li>
<li>DFS와 BFS돌며 순서를 기록하여 출력</li>

### 코드구현
```java
import java.util.*;

public class Main {
    static boolean visited[];
    static ArrayList<Integer> A[];

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int N = sc.nextInt();
        int M = sc.nextInt();
        int start = sc.nextInt();
        A = new ArrayList[N + 1];
        // 배열에 각 어레이 리스트 생성
        for (int i = 1; i <= N; i++) {
            A[i] = new ArrayList<Integer>();
        }
        // 생성된 어레이리스트에 양방향노드삽입
        for (int i = 0; i < M; i++) {
            int S = sc.nextInt();
            int E = sc.nextInt();
            A[S].add(E);
            A[E].add(S);
        }
        // 번호가 작은거먼저 방문을 위해 오름차순 정렬 **0에는 null이 있으므로 1부터**
        for (int i = 1; i <= N; i++) {
            Collections.sort(A[i]);
        }
        visited = new boolean[N + 1];
        DFS(start);
        System.out.println();   // 줄바꿈 의미의 개행
        visited = new boolean[N + 1];
        BFS(start);
        System.out.println();
    }
    public static void DFS(int Node) {
        System.out.print(Node + " ");
        visited[Node] = true;
        for (int i : A[Node]) {
            if (!visited[i]) {
                DFS(i);
            }
        }
    }
    public static void BFS(int Node) {
        Queue<Integer> queue = new LinkedList<Integer>();
        queue.add(Node);
        visited[Node] = true;

        while (!queue.isEmpty()) {
            int nowNode = queue.poll();
            System.out.print(nowNode + " ");
            for (int i : A[nowNode]) {
                if (!visited[i]) {
                    visited[i] = true;
                    queue.add(i);
                }
            }
        }
    }
}

```
