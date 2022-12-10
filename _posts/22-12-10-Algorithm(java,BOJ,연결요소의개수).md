---
layout: single
title:  "Algorithm BOJ 연결요소의개수 11724"
categories: algorithm
tag: [Java, algorithm, BOJ, 그래프, DFS/BFS, 백준11724]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ 연결요소의개수
[https://www.acmicpc.net/problem/11724](https://www.acmicpc.net/problem/11724)

### 문제
![연결요소의개수](/assets/img/BOJ11724.jpg)

### 풀이
<li>DFS가 탐색하는 회수를 카운팅, 몇개의 요소로 나뉘어있는지를 세는 문제</li>
<li>방향이 없기때문에 양쪽엣지에 다른엣지도 서로 추가</li>
<li>ArrayList와 boolean은 1번을 1번으로 표기하기위해 0번은 무시하고 n + 1 로 진행</li>
<li>모두탐색후 카운팅 출력</li>

### 코드구현
```java
import java.io.*;
import java.util.*;

public class 연결요소의개수_11724 {
    static ArrayList<Integer>[] A;
    static boolean visited[];

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        int n = Integer.parseInt(st.nextToken());   
        int m = Integer.parseInt(st.nextToken());   
        A = new ArrayList[n + 1];
        visited = new boolean[n + 1];
        for (int i = 1; i < n + 1 ; i++) {
            A[i] = new ArrayList<Integer>();
        }
        for (int i = 0; i < m; i++) {
            st = new StringTokenizer(br.readLine());    
            int s = Integer.parseInt(st.nextToken());
            int e = Integer.parseInt(st.nextToken());
            A[s].add(e);
            A[e].add(s);    // 양방향 엣지라서 양쪽에 엣지를 더하기
        }
        int count = 0;
        for (int i = 1; i < n + 1; i++) {
            if (!visited[i]) {
                count++;
                DFS(i);
            }
        }
        System.out.println(count);
    }
    static void DFS(int v) {
        if (visited[v]) {
            return;
        }
        visited[v] = true;
        for (int i : A[v]) {
            if (visited[i] == false) {
                DFS(i);
            }
        }
    }
}
```
