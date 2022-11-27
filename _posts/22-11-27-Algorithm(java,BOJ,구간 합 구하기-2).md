---
layout: single
title:  "Algorithm BOJ 구간합 구하기(2)"
categories: algorithm
tag: [Java, algorithm, BOJ, 백준, 구간합 구하기, 자료구조, 수학, 백준11660]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ (구간합 구하기-2)

### 문제
  ![구간합 구하기](/assets/img/BOJ11660.jpg)

### 풀이
<li>NxN의 배열을 반복으로 나열</li>
<li>연산이 중복되지 않도록 구간합 배열 따로생성</li>
<li>D[x2][y2] - D[x1 - 1][y2] - D[x2][y1 - 1] + D[x1 - 1][y1 - 1]로 결과 출력</li>

### 슈도코드
<li>var for N</li>
<li>var for M</li>
<li>save original array in double loop</li>
<li>save sum array in double loop</li>
<li>D[i][j] = D[i][j - 1] + D[i - 1][j] - D[i - 1][j - 1] + A[i][j]</li>
<li>print result in double loop</li>
<li>D[x2][y2] - D[x1 - 1][y2] - D[x2][y1 - 1] + D[x1 - 1][y1 - 1]</li>

### 코드구현
```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        int N = Integer.parseInt(st.nextToken());
        int M = Integer.parseInt(st.nextToken());

        int A[][] = new int[N + 1][N + 1];
        for (int i = 1; i <= N; i++) {
            st = new StringTokenizer(br.readLine());
            for (int j = 1; j <= N; j++) {
                A[i][j] = Integer.parseInt(st.nextToken());
            }
        }

        int D[][] = new int[N + 1][N + 1];
        for (int i = 1; i <= N; i++) {
            for (int j = 1; j <= N; j++) {
                D[i][j] = D[i][j - 1] + D[i - 1][j] - D[i - 1][j - 1] + A[i][j];
            }
        }

        for (int i = 0; i < M; i++) {
            st = new StringTokenizer(br.readLine());
            int x1 = Integer.parseInt(st.nextToken());
            int y1 = Integer.parseInt(st.nextToken());
            int x2 = Integer.parseInt(st.nextToken());
            int y2 = Integer.parseInt(st.nextToken());

            int result = D[x2][y2] - D[x1 - 1][y2] - D[x2][y1 - 1] + D[x1 - 1][y1 - 1];
            System.out.println(result);
        }
    }
}
```
