---
layout: single
title:  "Algorithm BOJ 미로탐색 2178"
categories: algorithm
tag: [Java, algorithm, BOJ, 수학, 그래프, 탐색, DFS/BFS, 백준2178]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## 미로탐색
[https://www.acmicpc.net/problem/2178](https://www.acmicpc.net/problem/2178)

### 문제
![미로탐색](/assets/img/BOJ2178.jpg)

### 풀이
<li>결국 최단거리를 묻는문제 BFS풀이가 필요</li>
<li>상하좌우를 탐색하며 배열밖으로 벗어나지않게 N,M에 도착할때의 깊이 풀어내기</li>
<li></li>
<li></li>
<li></li>
<li></li>
<li></li>
<li></li>
<li></li>
<li></li>
<li></li>


### 코드구현
```java
import java.io.*;
import java.util.*;

public class 미로탐색_2178 {
    static int[] dx = {0, 1, 0, -1};
    static int[] dy = {1, 0, -1, 0};
    static boolean[][] visited;
    static int[][] A;
    static int N, M;

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        N = Integer.parseInt(st.nextToken());
        M = Integer.parseInt(st.nextToken());
        A = new int[N][M];
        visited = new boolean[N][M];
        for (int i = 0; i < N; i++) {
            st = new StringTokenizer(br.readLine());
            String line = st.nextToken();
            for (int j = 0; j < M; j++) {
                A[i][j] = Integer.parseInt(line.substring(j, j + 1));
            }
        }
        BFS(0,0);
        System.out.println(A[N - 1][M - 1]);
    }

    public static void BFS(int i, int j) {
        Queue<int[]> queue = new LinkedList<>();
        queue.offer(new int[] {i, j});  // 시작노드 삽입
        while (!queue.isEmpty()) {
            int now[] = queue.poll();
            visited[i][j] = true;
            for (int k = 0; k < 4; k++) {
                int x = now[0] + dx[k]; // dx = {0, 1, 0, -1} 기존x자리에 dx 돌아가면서 대입
                int y = now[1] + dy[k]; // dy = {1, 0, -1, 0} 기존y자리에 dy 돌아가면서 대입
                if (x >= 0 && y >= 0 && x < N && y < M) {   // 좌표 유효성 검사 양수이면서&좌표밖으로 안나가는
                    if (A[x][y] != 0 && !visited[x][y]) {   // 0이 아니면서 방문한적 없는
                        visited[x][y] = true;
                        A[x][y] = A[now[0]][now[1]] + 1;    // 깊이 업데이트
                        System.out.println(A[x][y]);
                        queue.add(new int[] {x, y});
                    }
                }
            }
        }
    }
}
```
