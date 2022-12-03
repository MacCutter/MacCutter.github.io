---
layout: single
title:  "Algorithm BOJ 주몽의명령 1940"
categories: algorithm
tag: [Java, algorithm, BOJ, 백준, 정렬, 투포인터, 백준1940]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---
## BOJ (주몽의명령)
[https://www.acmicpc.net/problem/1940](https://www.acmicpc.net/problem/1940)

### 문제
![주몽의명령](/assets/img/BOJ1940.jpg)

### 풀이
<li>입력받은 N을 오름차순 정렬</li>
<li>투포인터 start = 0 , end = N - 1 로 시작</li>
<li>start와 end 를 합친것이 A라고 했을때 반복문으로</li>
<li>A < M 일경우 start++ (작은숫자를 늘려주기)</li>
<li>A > M 일경우 end -- (큰숫자를 줄여주기)</li>
<li>A = M 일경우 카운트++</li>
<li>출력 카운트</li>

### 코드구현
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());
        int M = Integer.parseInt(br.readLine());
        long[] A = new long[N];

        StringTokenizer st = new StringTokenizer(br.readLine());
        for (int i = 0; i < N; i++) {
            A[i] = Integer.parseInt(st.nextToken());
        }

        Arrays.sort(A);

        int startIdx = 0;
        int endIdx = N - 1;
        int cnt = 0;
        while (startIdx < endIdx) {
            if (A[startIdx] + A[endIdx] < M ) {
                startIdx++;
            } else if (A[startIdx] + A[endIdx] > M) {
                endIdx--;
            } else {
                cnt++;
                startIdx++;
                endIdx--;
            }
        }
        System.out.println(cnt);
    }
```
